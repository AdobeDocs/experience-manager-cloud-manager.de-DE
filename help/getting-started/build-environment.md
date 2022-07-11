---
title: Die Build-Umgebung
description: Erfahren Sie mehr über die spezielle Build-Umgebung, die Cloud Manager-Benutzer zum Erstellen und Testen Ihres Codes verwenden.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 52%

---


# Die Build-Umgebung {#build-environment}

Erfahren Sie mehr über die spezielle Build-Umgebung, die Cloud Manager-Benutzer zum Erstellen und Testen Ihres Codes verwenden.

## Umgebungsdetails {#details}

Die Build-Umgebungen von Cloud Manager weisen die folgenden Attribute auf.

* Die Erstellungsumgebung ist Linux-basiert und von Ubuntu 18.04 abgeleitet.
* Apache Maven 3.6.0 ist installiert.
* Die installierten Java-Versionen sind Oracle JDK 8u202 und Oracle JDK 11.0.2.
* Standardmäßig wird die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk1.8.0_202` festgelegt, was Oracle JDK 8u202 enthält. Siehe Abschnitt . [JDK-Version der alternativen Maven-Ausführung](#alternate-maven) für weitere Details.
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
* Maven wird auf Systemebene mit einer `settings.xml` Datei, die automatisch das Artefakt-Repository der öffentlichen Adobe mit einem Profil namens `adobe-public`.
   * Siehe Abschnitt [Öffentliches Maven-Repository der Adobe](https://repo1.maven.org/) für weitere Details.

>[!NOTE]
>
>Obwohl Cloud Manager keine bestimmte Version des Programms des `jacoco-maven-plugin` definiert, muss mindestens die Version `0.7.5.201505241946` verwendet werden.

>[!TIP]
>
>In den folgenden zusätzlichen Ressourcen erfahren Sie, wie Sie Cloud Manager-APIs verwenden:
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Erstellen einer API-Integration](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/)
>* [API-Berechtigungen](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)


## Verwenden einer bestimmten Java-Version {#using-java-version}

Standardmäßig werden Projekte vom Cloud Manager-Build-Prozess mit dem Oracle 8 JDK erstellt. Kunden, die ein alternatives JDK verwenden möchten, haben zwei Optionen.

* [Maven Toolchains](#maven-toolchains)
* [Auswählen einer alternativen JDK-Version für den gesamten Maven-Ausführungsprozess](#alternate-maven)

### Maven Toolchains {#maven-toolchains}

Die [Maven Toolchain-Plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) ermöglicht es Projekten, ein bestimmtes JDK (oder Toolchain) auszuwählen, das im Kontext von toolchain-fähigen Maven-Plug-ins verwendet werden soll. Dies geschieht in der `pom.xml`-Datei des Projekts, indem ein Anbieter und ein Versionswert angegeben werden. Ein Beispielabschnitt in der Datei `pom.xml` ist:

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

Dies führt dazu, dass alle Toolchain-fähigen Maven-Plug-ins das Oracle JDK, Version 11 verwenden.

Bei Verwendung dieser Methode wird Maven selbst weiterhin mit dem standardmäßigen JDK (Oracle 8) ausgeführt und die `JAVA_HOME`-Umgebungsvariable wird nicht geändert. Daher funktioniert das Überprüfen oder Erzwingen der Java-Version über Plug-ins wie das [Apache Maven Enforcer-Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) nicht und solche Plug-ins dürfen nicht verwendet werden.

Die derzeit verfügbaren Anbieter-/Versionskombinationen sind:

| Anbieter | Version |
|---|---|
| Oracle | 1.8 |
| Oracle | 1,11 |
| Oracle | 11 |
| Sun | 1,8 |
| Sun | 1,11 |
| Sun | 11 |

>[!NOTE]
>
>Ab April 2022 wird Oracle JDK das Standard-JDK für die Entwicklung und den Betrieb von AEM-Programmen sein. Der Build-Prozess von Cloud Manager wechselt automatisch zur Verwendung von Oracle JDK, auch wenn in der Maven-Toolchain explizit eine alternative Option ausgewählt ist. Siehe [Die Versionshinweise vom April](/help/release-notes/2022/2022-4-0.md) für weitere Informationen.

### Version des alternativen Maven-Ausführungs-JDK {#alternate-maven}

Es ist auch möglich, Oracle 8 oder Oracle 11 als JDK für die gesamte Maven-Ausführung auszuwählen. Im Gegensatz zu den Toolchain-Optionen ändert dies das für alle Plug-ins verwendete JDK, es sei denn, die Toolchain-Konfiguration ist ebenfalls festgelegt. In diesem Fall wird die Toolchain-Konfiguration weiterhin für Toolchain-fähige Maven-Plug-ins angewendet. Daher funktioniert in diesem Fall das Überprüfen und Erzwingen der Java-Version mit dem [Apache Maven Enforcer-Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/).

Erstellen Sie dazu eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Diese Datei kann entweder den Inhalt `11` oder `8`. Alle anderen Werte werden ignoriert. Wenn `11` angegeben ist, wird Oracle 11 verwendet und die `JAVA_HOME` Umgebungsvariable auf `/usr/lib/jvm/jdk-11.0.2`. Wenn `8` festgelegt ist, wird Oracle 8 verwendet und die `JAVA_HOME` Umgebungsvariable auf `/usr/lib/jvm/jdk1.8.0_202`.

## Umgebungsvariablen {#environment-variables}

### Standard-Umgebungsvariablen {#standard-environ-variables}

In einigen Fällen kann es erforderlich sein, den Build-Prozess basierend auf Informationen zum Programm oder zur Pipeline zu variieren.

Wenn beispielsweise die JavaScript-Minimierung während der Build-Erstellung über ein Tool wie gulp erfolgt, kann es sinnvoll sein, beim Erstellen für eine Entwicklungsumgebung eine andere Minimierungsstufe zu verwenden als beim Erstellen für Staging und Produktion.

Um dies zu unterstützen, fügt Cloud Manager bei jeder Ausführung dem Build-Container standardmäßige Umgebungsvariablen hinzu.

| Variablenname | Beschreibung |
|---|---|
| `CM_BUILD` | Immer auf `true` (wahr) festgelegt |
| `BRANCH` | Die konfigurierte Verzweigung für die Ausführung |
| `CM_PIPELINE_ID` | Numerische Pipeline-Kennung |
| `CM_PIPELINE_NAME` | Name der Pipeline |
| `CM_PROGRAM_ID` | Numerische Programmkennung |
| `CM_PROGRAM_NAME` | Name des Programms |
| `ARTIFACTS_VERSION` | Bei einer Staging- oder Produktions-Pipeline ist die von Cloud Manager generierte synthetische Version |

### Pipeline-Variablen {#pipeline-variables}

In einigen Fällen kann Ihr Build-Prozess von bestimmten Konfigurationsvariablen abhängen, die nicht im Git-Repository platziert werden können oder zwischen Pipeline-Ausführungen mit derselben Verzweigung variieren müssen.

Cloud Manager ermöglicht die Konfiguration dieser Variablen über die Cloud Manager-API oder die Cloud Manager-CLI individuell für die Pipelines. Variablen können entweder als reiner Test oder mit Data-at-Rest-Verschlüsselung gespeichert werden. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die in der `pom.xml`-Datei oder anderen Build-Skripten referenziert werden kann.

Um eine Variable mithilfe der CLI festzulegen, führen Sie einen Befehl ähnlich dem folgenden aus.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Aktuelle Variablen können mit einem Befehl ähnlich dem folgenden aufgeführt werden.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Variablen müssen bestimmten Einschränkungen entsprechen.

* Variablennamen dürfen nur alphanumerische Zeichen und den Unterstrich (`_`).
   * Standardmäßig sollten alle Namen in Großbuchstaben eingegeben werden.
* Pro Pipeline sind maximal 200 Variablen zulässig.
* Jeder Name darf höchstens 99 Zeichen enthalten.
* Jeder Zeichenfolgenwert muss weniger als 2048 Zeichen enthalten.
* Jeder secretString -Wert muss kleiner als und 500 Zeichen sein.

Bei Verwendung in einem Maven `pom.xml` -Datei, ist es in der Regel hilfreich, diese Variablen Maven-Eigenschaften mithilfe einer ähnlichen Syntax wie der folgenden zuzuordnen.

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

Um vollständig zu funktionieren, benötigen einige Builds zusätzliche Systempakete, die installiert werden müssen. Beispielsweise kann ein Build ein Python- oder Ruby-Skript aufrufen und muss daher einen entsprechenden Sprachinterpreter installiert haben. Dies kann durch Abfrage von [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) erfolgen, wodurch APT aufgerufen wird. Diese Ausführung sollte im Allgemeinen in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen sein. So installieren Sie beispielsweise Python:

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

Mit derselben Methode können Sie auch sprachspezifische Pakete installieren, d. h. mit `gem` für RubyGems oder mit `pip` für Python-Pakete.

>[!NOTE]
>
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es nicht in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein Systempaket in der AEM-Umgebung installieren möchten, wenden Sie sich an Ihre Adobe-Support-Mitarbeiter.
