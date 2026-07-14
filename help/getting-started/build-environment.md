---
title: Die Build-Umgebung
description: Erfahren Sie mehr über die spezielle Build-Umgebung, die Cloud Manager-Benutzende zum Erstellen und Testen Ihres Codes verwenden.
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
TQID: https://experienceleague.adobe.com/AdGVWjyF0DXEX7jH5S39JQ506oVnNYGtYqAWNHcQeP8
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552eid: cd2426f1-5719-4006-b8c2-738e5969754b
subfeature_v2: id: d9eb3b3e-9447-4ed4-bf4a-96c7b245cb27
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 1205
ht-degree: 50%

---

# Die Build-Umgebung {#build-environment}

Erfahren Sie mehr über die spezielle Build-Umgebung, die Cloud Manager zum Erstellen und Testen Ihres Codes verwendet.

## Umgebungsdetails {#details}

Die Build-Umgebungen von Cloud Manager weisen folgende Eigenschaften auf.

* Die Build-Umgebung ist Linux-basiert und von Ubuntu 22.04 abgeleitet.
* Apache Maven 3.9.4 ist installiert.
   * Adobe empfiehlt Benutzenden, [ihre Maven-Repositorys zu aktualisieren, um HTTPS anstelle von HTTP zu verwenden](#https-maven).
* Die installierten Java-Versionen sind Oracle JDK 8u401 und Oracle JDK 11.0.22.
   * `/usr/lib/jvm/jdk1.8.0_401`
   * `/usr/lib/jvm/jdk-11.0.22`
* Standardmäßig wird die Umgebungsvariable `JAVA_HOME` auf `/usr/lib/jvm/jdk1.8.0_401` festgelegt, was Oracle JDK 8u401 enthält. Weitere Einzelheiten finden Sie [ Abschnitt Alternative JDK-Version ](#alternate-maven) Maven-Ausführung .
* Zusätzliche erforderliche Systempakete werden installiert.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere Pakete werden zur Build-Zeit installiert, wie im Abschnitt [Installieren zusätzlicher Systempakete“ ](#installing-additional-system-packages).
* Jeder Build wird in einer neuen Umgebung erstellt. Der Build-Container speichert keine Daten zwischen Ausführungen.
* Maven wird mit diesen drei Befehlen ausgeführt:
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wird auf Systemebene mit einer Datei `settings.xml` konfiguriert, die automatisch das öffentliche Adobe-Artefakt-Repository einschließt und ein Profil namens `adobe-public` verwendet. Weitere Informationen dazu finden Sie im [öffentlichen Maven-Repository von Adobe](https://repo1.maven.org/).
* Node.js 18 ist für [Frontend-Pipelines](/help/overview/ci-cd-pipelines.md) verfügbar.

>[!IMPORTANT]
>Die Unterstützung für Maven-Toolchains wurde mit Wirkung von Cloud Manager 2025.06.0 entfernt. Die JDK-Auswahl wird jetzt nur noch über `.cloudmanager/java-version` unterstützt. Weitere Informationen finden Sie unter [Verwenden einer bestimmten Java-Version](#using-java-version).

>[!NOTE]
>
>Obwohl Cloud Manager keine bestimmte Version des `jacoco-maven-plugin` definiert, muss mindestens eine Version `0.7.5.201505241946` sein.

>[!TIP]
>
>Informationen zur Verwendung von Cloud Manager-APIs finden Sie in den folgenden zusätzlichen Ressourcen:
>
>* [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Erstellen einer API-Integration](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration)
>* [API-Berechtigungen](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions)

## HTTPS-Maven-Repositorys {#https-maven}

Cloud Manager [2023.10.0](/help/release-notes/2023/2023-10-0.md) begann mit einem rollierenden Update der Build-Umgebung (abgeschlossen mit Version 2023.12.0), das ein Update auf Maven 3.8.8 enthielt. Eine in Maven 3.8.1 eingeführte Änderung war eine Sicherheitsverbesserung, um potenzielle Schwachstellen zu beheben. Insbesondere deaktiviert Maven nun alle unsicheren `http://*`-Spiegelungen standardmäßig, wie in den [Maven-Versionshinweisen](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291) beschrieben.

Einige Benutzende stoßen während des Build-Schritts auf Probleme beim Herunterladen von Artefakten aus Maven-Repositorys, die unsichere HTTP-Verbindungen verwenden.

Um ein reibungsloses Erlebnis mit der aktualisierten Version zu gewährleisten, empfiehlt Adobe, dass Benutzende ihre Maven-Repositorys so aktualisieren, dass sie HTTPS anstelle von HTTP verwenden. Diese Anpassung unterstützt die Umstellung der Branche auf sichere Kommunikationsprotokolle und sorgt für einen sicheren und zuverlässigen Build-Prozess.

## Verwenden einer bestimmten Java-Version {#using-java-version}

Standardmäßig werden Projekte vom Cloud Manager-Build-Prozess mit dem Oracle 8 JDK erstellt. Kunden, die ein alternatives JDK verwenden möchten, können eine alternative JDK-Version für den gesamten Maven-Ausführungsprozess auswählen.

>[!IMPORTANT]
>
>Maven-Toolchains werden in Cloud Manager 2025.06.0 nicht mehr unterstützt. Beachten Sie, dass Pipelines, die eine maven-toolchains-Plug-in-Konfiguration enthalten, mit `Cannot find matching toolchain definitions.` fehlschlagen. Verwenden Sie stattdessen die `.cloudmanager/java-version`-Datei, um JDK 11, 17 oder 21 auszuwählen.
>
>**Migrationsleitfaden:**
>
>1. Entfernen Sie Toolchains, indem Sie alle `org.apache.maven.plugins:maven-toolchains-plugin` und alle `toolchains.xml` löschen, die für Ihre Quellcodeverwaltung festgelegt wurden.
>1. Wählen Sie ein JDK mit `.cloudmanager/java-version` (21, 17 oder 11) aus, wie in [Alternative Maven-Ausführung JDK-Version](#alternate-maven) beschrieben.
>1. Adobe empfiehlt, den Cloud Manager-Build-Cache zu löschen oder eine neue Pipeline-Ausführung auszulösen.
>

<!--
DEPRECATED 
### Maven Toolchains {#maven-toolchains}

The [Maven Toolchains plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) lets projects select a specific JDK (or toolchain) to use in the context of toolchains-aware Maven plug-ins. This process is done in the project's `pom.xml` file by specifying a vendor and version value. A sample section in the `pom.xml` file is the following:

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

This process causes all toolchains-aware Maven plug-ins to use the Oracle JDK, version 11.

When using this method, Maven itself still runs using the default JDK (Oracle 8) and the `JAVA_HOME` environment variable is not changed. Therefore, checking or enforcing the Java version through plug-ins like the [Apache Maven Enforcer Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/) does not work and such plug-ins must not be used.

The currently available vendor/version combinations are:

|Vendor|Version|
|---|---|
| Oracle |1.8|
| Oracle |1.11|
| Oracle |11|
| Sun |1.8|
| Sun |1.11|
| Sun |11|

>[!NOTE]
>
>Starting April 2022, Oracle JDK is going to be the default JDK for the development and operation of AEM applications. Cloud Manager's build process automatically switches to using Oracle JDK, even if an alternative option is explicitly selected in the Maven toolchain. See the [April release notes](/help/release-notes/2022/2022-4-0.md) for more details.
-->

### Alternative JDK-Version für die Maven-Ausführung {#alternate-maven}

Sie können Oracle 8 oder Oracle 11 als JDK für die gesamte Maven-Ausführung auswählen. Dieser Ansatz ändert das für alle Plug-ins verwendete JDK. Daher wird das Überprüfen und Erzwingen der Java-Version mit dem [Apache Maven Enforcer-Plug-](https://maven.apache.org/enforcer/maven-enforcer-plugin/)) unterstützt.

Erstellen Sie dazu eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Diese Datei kann entweder den Inhalt `11` oder `8` enthalten. Alle anderen Werte werden ignoriert. Wenn `11` angegeben ist, verwendet das System Oracle 11 und setzt die `JAVA_HOME` Umgebungsvariable auf `/usr/lib/jvm/jdk-11.0.22`. Wenn `8` angegeben ist, verwendet das System Oracle 8 und setzt die `JAVA_HOME` Umgebungsvariable auf `/usr/lib/jvm/jdk1.8.0_401`.

## Umgebungsvariablen {#environment-variables}

### Standard-Umgebungsvariablen {#standard-environ-variables}

In einigen Fällen ist es erforderlich, den Build-Prozess basierend auf Informationen über das Programm oder die Pipeline zu variieren.

Wenn Sie beispielsweise ein Tool wie gulp für die JavaScript-Minimierung verwenden, sollten Sie im Vergleich zu Staging- und Produktionsumgebungen unterschiedliche Minimierungsstufen für die Entwicklung verwenden.

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

### Verfügbarkeit von Standard-Umgebungsvariablen {#availability}

Standard-Umgebungsvariablen können an verschiedenen Stellen verwendet werden.

#### Authoring-, Vorschau- und Veröffentlichungsumgebungen {#author-preview-publish}

In der Authoring-, Vorschau- und Veröffentlichungsumgebung können sowohl reguläre Umgebungsvariablen als auch Geheimnisse verwendet werden.

#### Dispatcher {#dispatcher}

Im [Dispatcher](https://experienceleague.adobe.com/de/docs/experience-manager-dispatcher/using/dispatcher) können nur reguläre Umgebungsvariablen verwendet werden. Geheimnisse können nicht verwendet werden.

Allerdings können Umgebungsvariablen nicht in `IfDefine`-Richtlinien verwendet werden.

>[!TIP]
>
>Validieren Sie die Verwendung von Umgebungsvariablen [lokal im Dispatcher](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools), bevor Sie sie bereitstellen.

#### OSGi-Konfigurationen {#osgi}

In den [OSGi-Konfigurationen](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi) können sowohl reguläre Umgebungsvariablen als auch Geheimnisse verwendet werden.

### Pipeline-Variablen {#pipeline-variables}

In einigen Fällen hängt der Build-Prozess von bestimmten Konfigurationsvariablen ab. Diese Variablen können nicht im Git-Repository platziert werden oder müssen zwischen Pipeline-Ausführungen mit derselben Verzweigung variieren.

Cloud Manager ermöglicht die Konfiguration dieser Variablen über die Cloud Manager-API oder die Cloud Manager-CLI individuell für die Pipelines. Variablen werden entweder als reiner Text oder im Ruhezustand verschlüsselt gespeichert. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die dann in der Datei `pom.xml` oder anderen Build-Skripten referenziert werden kann.

Um eine Variable mithilfe der CLI festzulegen, führen Sie einen Befehl ähnlich dem folgenden aus.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Aktuelle Variablen können mit einem Befehl ähnlich dem folgenden aufgelistet werden.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Variablen müssen bestimmte Einschränkungen einhalten.

* Variablennamen dürfen nur alphanumerische Zeichen und den Unterstrich (`_`) enthalten.
   * Standardmäßig werden die Namen alle großgeschrieben.
* Pro Pipeline sind maximal 200 Variablen zulässig.
* Jeder Name darf höchstens 99 Zeichen enthalten.
* Jeder Zeichenfolgenwert darf höchstens 2047 Zeichen enthalten.
* Jeder `secretString`-Wert darf höchstens 499 Zeichen enthalten.

Bei Verwendung in einer Maven-Datei `pom.xml` ist es in der Regel hilfreich, diese Variablen Maven-Eigenschaften mithilfe einer ähnlichen Syntax wie der folgenden zuzuordnen.

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

Um ordnungsgemäß zu funktionieren, müssen einige Builds zusätzliche Systempakete installieren. Ein Build ruft beispielsweise ein Python- oder Ruby-Skript auf und benötigt einen entsprechenden Sprach-Interpreter. Dieses Szenario kann durch Aufrufen des -[`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) zum Aufrufen von APT gehandhabt werden. Diese Ausführung ist in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen. Um beispielsweise Python zu installieren, können Sie wie folgt vorgehen:

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

Mit dieser Methode können Sie auch sprachspezifische Pakete installieren. Das heißt, Sie verwenden `gem` für RubyGems oder `pip` für Python-Pakete.

>[!NOTE]
>
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es nicht in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein Systempaket in der AEM-Umgebung installieren möchten, wenden Sie sich an den Adobe-Support.
