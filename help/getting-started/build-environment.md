---
title: Die Build-Umgebung
description: Erfahren Sie mehr über die spezielle Build-Umgebung, die Cloud Manager-Benutzer zum Erstellen und Testen Ihres Codes verwenden.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 53%

---


# Die Build-Umgebung {#build-environment}

Erfahren Sie mehr über die spezielle Build-Umgebung, die Cloud Manager-Benutzer zum Erstellen und Testen Ihres Codes verwenden.

## Umgebungsdetails {#details}

Cloud Manager-Build-Umgebungen weisen die folgenden Attribute auf.

* Die Build-Umgebung ist Linux-basiert und von Ubuntu 22.04 abgeleitet.
* Apache Maven 3.9.4 ist installiert.
   * Adobe empfiehlt Benutzern [die Aktualisierung ihrer Maven-Repositorys, um HTTPS anstelle von HTTP](#https-maven) zu verwenden.
* Die installierten Java-Versionen sind Oracle JDK 8u401 und Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* Standardmäßig ist die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk1.8.0_401` gesetzt, die Oracle JDK 8u401 enthält. Weitere Einzelheiten finden Sie im Abschnitt [Alternative JDK-Version für die Maven-Ausführung](#alternate-maven).
* Es sind einige zusätzliche erforderliche Systempakete installiert.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere Pakete können zur Build-Zeit installiert werden, wie im Abschnitt [Installieren zusätzlicher Systempakete](#installing-additional-system-packages) beschrieben.
* Jeder Build erfolgt in einer unberührten Umgebung. Der Build-Container behält keinen Status zwischen Ausführungen bei.
* Maven wird immer mit den folgenden drei Befehlen ausgeführt:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wird auf Systemebene mit einer `settings.xml`-Datei konfiguriert, die automatisch das öffentliche Adobe-Artefakt-Repository enthält und ein Profil namens `adobe-public` verwendet. Weitere Informationen finden Sie im [öffentlichen Maven-Repository für Adobe](https://repo1.maven.org/) .
* Node.js 18 ist für [Frontend-Pipelines](/help/overview/ci-cd-pipelines.md) verfügbar.

>[!NOTE]
>
>Obwohl Cloud Manager keine bestimmte Version des Programms des `jacoco-maven-plugin` definiert, muss mindestens die Version `0.7.5.201505241946` verwendet werden.

>[!TIP]
>
>In den folgenden zusätzlichen Ressourcen erfahren Sie, wie Sie Cloud Manager-APIs verwenden:
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Erstellen einer API-Integration](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API-Berechtigungen](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)

## HTTPS-Maven-Repositorys {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) hat eine rollierende Aktualisierung der Build-Umgebung gestartet (abgeschlossen mit Version 2023.12.0), die eine Aktualisierung auf Maven 3.8.8 enthielt. Eine wesentliche Änderung, die in Maven 3.8.1 eingeführt wurde, war eine Sicherheitsverbesserung, die darauf abzielte, potenzielle Schwachstellen zu minimieren. Insbesondere deaktiviert Maven jetzt standardmäßig alle unsicheren `http://*` Spiegel, wie in den [Maven-Versionshinweisen](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291) beschrieben.

Aufgrund dieser Sicherheitsverbesserung können bei einzelnen Benutzenden während des Build-Schritts Probleme auftreten, insbesondere beim Herunterladen von Artefakten aus Maven-Repositorys, die unsichere HTTP-Verbindungen verwenden.

Um ein reibungsloses Erlebnis mit der aktualisierten Version zu gewährleisten, empfiehlt Adobe, dass Benutzende ihre Maven-Repositorys so aktualisieren, dass sie HTTPS anstelle von HTTP verwenden. Diese Anpassung steht im Einklang mit dem wachsenden Trend der Branche hin zu sicheren Kommunikationsprotokollen und trägt zur Aufrechterhaltung eines sicheren und zuverlässigen Build-Prozesses bei.

## Verwenden einer bestimmten Java-Version {#using-java-version}

Standardmäßig verwenden vom Cloud Manager-Build-Prozess erstellte Projekte das Oracle 8 JDK. Kunden, die ein alternatives JDK verwenden möchten, haben zwei Optionen.

* [Maven Toolchains](#maven-toolchains)
* [Auswahl einer alternativen JDK-Version für den gesamten Maven-Ausführungsprozess](#alternate-maven)

### Maven Toolchains {#maven-toolchains}

Mit dem [Maven Toolchain-Plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) können Projekte ein bestimmtes JDK (oder eine Toolchain) auswählen, das im Kontext von toolchain-basierten Maven-Plug-ins verwendet werden soll. Dieser Vorgang erfolgt in der Datei &quot;`pom.xml`&quot; des Projekts, indem ein Anbieter und ein Versionswert angegeben werden. Ein Beispielabschnitt in der Datei `pom.xml` ist:

```xml
        <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
            </jdk>
        </toolchains>
    </configuration>
</plugin>
```

Dieser Vorgang führt dazu, dass alle Toolchain-fähigen Maven-Plug-ins das Oracle JDK, Version 11 verwenden.

Bei Verwendung dieser Methode wird Maven selbst weiterhin mit dem standardmäßigen JDK (Oracle 8) ausgeführt und die `JAVA_HOME`-Umgebungsvariable wird nicht geändert. Daher funktioniert das Überprüfen oder Erzwingen der Java-Version über Plug-ins wie das [Apache Maven Enforcer-Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) nicht und solche Plug-ins dürfen nicht verwendet werden.

Die derzeit verfügbaren Anbieter-/Versionskombinationen sind:

| Anbieter | Version |
|---|---|
| Oracle | 1.8 |
| Oracle | 1.11 |
| Oracle | 11 |
| So | 1.8 |
| So | 1.11 |
| So | 11 |

>[!NOTE]
>
>Ab April 2022 wird Oracle JDK als Standard-JDK für die Entwicklung und den Betrieb von AEM-Anwendungen verwendet. Der Build-Prozess von Cloud Manager wechselt automatisch zur Verwendung von Oracle JDK, auch wenn in der Maven-Toolchain explizit eine alternative Option ausgewählt ist. Weitere Informationen finden Sie in den [Versionshinweisen vom April](/help/release-notes/2022/2022-4-0.md) .

### JDK-Version der alternativen Maven-Ausführung {#alternate-maven}

Es ist auch möglich, Oracle 8 oder Oracle 11 als JDK für die gesamte Maven-Ausführung auszuwählen. Im Gegensatz zu den Optionen der Toolketten ändert dies das JDK, das für alle Plug-ins verwendet wird, es sei denn, die Konfiguration der Toolketten ist ebenfalls festgelegt. In diesem Fall wird die Konfiguration der Toolketten weiterhin für die Maven-Plug-ins angewendet, die für Toolketten verwendet werden. Daher funktioniert das Überprüfen und Erzwingen der Java-Version mit dem [Apache Maven Enforcer-Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/).

Erstellen Sie dazu eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Diese Datei kann entweder den Inhalt `11` oder `8` enthalten. Alle anderen Werte werden ignoriert. Wenn `11` angegeben ist, wird Oracle 11 verwendet und die Umgebungsvariable `JAVA_HOME` wird auf `/usr/lib/jvm/jdk-11.0.22` festgelegt. Wenn `8` angegeben ist, wird Oracle 8 verwendet und die Umgebungsvariable `JAVA_HOME` wird auf `/usr/lib/jvm/jdk1.8.0_401` festgelegt.

## Umgebungsvariablen {#environment-variables}

### Standard-Umgebungsvariablen {#standard-environ-variables}

In einigen Fällen muss der Build-Prozess je nach Informationen zum Programm oder zur Pipeline variiert werden.

Wenn Sie beispielsweise ein Tool wie gulp für die JavaScript-Minimierung verwenden, bevorzugen Sie möglicherweise unterschiedliche Minimierungsstufen für Entwicklungs-, Staging- und Produktionsumgebungen.

Um dies zu unterstützen, fügt Cloud Manager diese Standard-Umgebungsvariablen bei jeder Ausführung dem Build-Container hinzu.

| Variablenname | Beschreibung |
|---|---|
| `CM_BUILD` | Immer auf `true` (wahr) festgelegt |
| `BRANCH` | Die konfigurierte Verzweigung für die Ausführung |
| `CM_PIPELINE_ID` | Numerische Pipeline-Kennung |
| `CM_PIPELINE_NAME` | Name der Pipeline |
| `CM_PROGRAM_ID` | Numerische Programmkennung |
| `CM_PROGRAM_NAME` | Name des Programms |
| `ARTIFACTS_VERSION` | Die von Cloud Manager generierte synthetische Version bei einer Staging- oder Produktions-Pipeline |

### Verfügbarkeit der Standard-Umgebungsvariablen {#availability}

Standard-Umgebungsvariablen können an verschiedenen Stellen verwendet werden.

#### Autoren-, Vorschau- und Veröffentlichungsumgebungen {#author-preview-publish}

In der Authoring-, Vorschau- und Veröffentlichungsumgebung können sowohl reguläre Umgebungsvariablen als auch Geheimnisse verwendet werden.

#### Dispatcher {#dispatcher}

Nur normale Umgebungsvariablen können mit [der Dispatcher](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher) verwendet werden. Geheimnisse können nicht verwendet werden.

Umgebungsvariablen können jedoch nicht in `IfDefine` -Direktiven verwendet werden.

>[!TIP]
>
>Validieren Sie die Verwendung von Umgebungsvariablen vor der Bereitstellung mit [Dispatcher lokal](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools).

#### OSGi-Konfigurationen {#osgi}

In den [OSGi-Konfigurationen](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi) können sowohl reguläre Umgebungsvariablen als auch Geheimnisse verwendet werden.

### Pipeline-Variablen {#pipeline-variables}

In einigen Fällen kann Ihr Build-Prozess von bestimmten Konfigurationsvariablen abhängen, die nicht im Git-Repository platziert werden können oder zwischen Pipeline-Ausführungen mit derselben Verzweigung variieren müssen.

Cloud Manager ermöglicht die Konfiguration dieser Variablen über die Cloud Manager-API oder die Cloud Manager-CLI individuell für die Pipelines. Variablen können entweder als reiner Test oder mit Data-at-Rest-Verschlüsselung gespeichert werden. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die dann aus der Datei `pom.xml` oder anderen Build-Skripten referenziert werden kann.

Um eine Variable mithilfe der CLI festzulegen, führen Sie einen Befehl ähnlich dem folgenden aus.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Aktuelle Variablen können mit einem Befehl ähnlich dem folgenden aufgelistet werden.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Variablen müssen bestimmte Einschränkungen einhalten.

* Variablen dürfen nur alphanumerische Zeichen und den Unterstrich (`_`) enthalten.
   * Der Konvention nach sollten die Namen in Großbuchstaben geschrieben werden.
* Pro Pipeline sind maximal 200 Variablen zulässig.
* Jeder Name darf maximal 100 Zeichen lang sein.
* Jeder Zeichenfolgenwert darf maximal 2048 Zeichen lang sein.
* Jeder `secretString` -Wert darf maximal 500 Zeichen enthalten.

Bei Verwendung in einer Maven-`pom.xml`-Datei ist es in der Regel hilfreich, diese Variablen Maven-Eigenschaften mithilfe einer ähnlichen Syntax wie der folgenden zuzuordnen.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Installieren zusätzlicher Systempakete {#installing-additional-system-packages}

Damit einige Builds vollständig funktionieren, müssen zusätzliche Systempakete installiert werden. So ist es z. B. möglich, dass ein Build ein Python- oder Ruby-Skript aufruft, wofür der entsprechende Sprach-Interpreter installiert sein muss. Dieses Szenario kann durch Aufruf von [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) zum Aufrufen von APT durchgeführt werden. Diese Ausführung sollte im Allgemeinen in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen sein. Um beispielsweise Python zu installieren, können Sie Folgendes tun:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Diese Technik kann auch verwendet werden, um sprachspezifische Pakete zu installieren. Verwenden Sie also `gem` für RubyGems oder `pip` für Python-Pakete.

>[!NOTE]
>
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es nicht in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein Systempaket in der AEM-Umgebung installieren möchten, wenden Sie sich an Ihre Adobe-Support-Mitarbeiter.
