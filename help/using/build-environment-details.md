---
title: Grundlagen zur Build-Umgebung
description: Auf dieser Seite erfahren Sie mehr über Umgebungen
feature: Environments
exl-id: b3543320-66d4-4358-8aba-e9bdde00d976
source-git-commit: 9959f649e553d0ff6d41a70a468bec3e2e854d75
workflow-type: ht
source-wordcount: '997'
ht-degree: 100%

---

# Grundlagen zur Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Erstellungsumgebung. Diese Umgebung weist die folgenden Attribute auf:

* Die Erstellungsumgebung ist Linux-basiert und von Ubuntu 18.04 abgeleitet.
* Apache Maven 3.6.0 ist installiert.
* Die installierten Java-Versionen sind Oracle JDK 8u202, Azul Zulu 8u292, Oracle JDK 11.0.2 und Azul Zulu 11.0.11.
* Standardmäßig ist die Umgebungsvariable JAVA_HOME auf `/usr/lib/jvm/jdk1.8.0_202` gestzt, das Oracle JDK 8u202 enthält. Weitere Informationen dazu finden Sie unter [Alternative JDK-Version der Maven-Ausführung](#alternate-maven).
* Es sind einige zusätzliche erforderliche Systempakete installiert:

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick

* Andere Pakete können zur Erstellungszeit wie [unten](#installing-additional-system-packages) beschrieben installiert werden.
* Jeder Build wird in einer unberührten Umgebung erstellt, der Build-Container speichert zwischen den Ausführungen keinen Status.
* Maven wird immer mit den folgenden drei Befehlen ausgeführt:

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`

* Maven wird auf Systemebene mit einer settings.xml-Datei konfiguriert, die automatisch das öffentliche Adobe-**Artefakt**-Repository mit einem Profil namens `adobe-public` enthält.
Weitere Informationen dazu finden Sie im [Adobe Public Maven Repository](https://repo1.maven.org/).

>[!NOTE]
>Obwohl Cloud Manager keine bestimmte Version des Programms des `jacoco-maven-plugin` definiert, muss mindestens die Version `0.7.5.201505241946` verwendet werden.


>[!NOTE]
>In den folgenden zusätzlichen Ressourcen erfahren Sie, wie Sie Cloud Manager-APIs verwenden:
> * [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager)
>* [Erstellen einer API-Integration](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/create-api-integration.md)
>* [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md)


## Verwenden einer bestimmten Java-Version {#using-java-version}

Standardmäßig werden Projekte vom Cloud Manager-Build-Prozess mit dem Oracle 8 JDK erstellt. Kunden, die ein anderes JDK verwenden möchten, haben zwei Optionen: Maven Toolchains und Auswahl einer alternativen JDK-Version für den gesamten Maven-Ausführungsprozess.

### Maven Toolchains {#maven-toolchains}

Das [Maven Toolchain-Plug-in](https://maven.apache.org/plugins/maven-toolchains-plugin/) ermöglicht es Projekten, ein bestimmtes JDK (oder *Toolchain*) auszuwählen, das im Kontext von Toolchain-fähigen Maven-Plug-ins verwendet werden soll. Dies geschieht in der `pom.xml`-Datei des Projekts, indem ein Anbieter und ein Versionswert angegeben werden. Ein Beispielabschnitt in der Datei `pom.xml` ist:

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

* Oracle 1.8
* Oracle 1.11
* Oracle 11
* Sun 1.8
* Sun 1.11
* Sun 11
* Azul 1.8
* Azul 1.11
* Azul 8

### Version des alternativen Maven-Ausführungs-JDK {#alternate-maven}

Es ist auch möglich, Azul 8 oder Azul 11 als JDK für die gesamte Maven-Ausführung auszuwählen. Im Gegensatz zu den Toolchain-Optionen ändert dies das für alle Plug-ins verwendete JDK, es sei denn, die Toolchain-Konfiguration ist ebenfalls festgelegt. In diesem Fall wird die Toolchain-Konfiguration weiterhin für Toolchain-fähige Maven-Plug-ins angewendet. Daher funktioniert in diesem Fall das Überprüfen und Erzwingen der Java-Version mit dem [Apache Maven Enforcer-Plug-in](https://maven.apache.org/enforcer/maven-enforcer-plugin/).

Erstellen Sie dazu eine Datei mit dem Namen `.cloudmanager/java-version` in der von der Pipeline verwendeten Git-Repository-Verzweigung. Diese Datei kann entweder den Inhalt 11 oder 8 enthalten. Alle anderen Werte werden ignoriert. Wenn „11“ angegeben ist, wird Azul 11 verwendet und die Umgebungsvariable JAVA_HOME wird auf `/usr/lib/jvm/jdk-11.0.11` festgelegt. Wenn „8“ angegeben ist, wird Azul 8 verwendet und die Umgebungsvariable JAVA_HOME wird auf `/usr/lib/jvm/jdk-8.0.292` festgelegt.

## Umgebungsvariablen {#environment-variables}

### Standard-Umgebungsvariablen {#standard-environ-variables}

In einigen Fällen müssen Kunden den Build-Prozess je nach Informationen zum Programm oder zur Pipeline variieren.

Wenn beispielsweise eine JavaScript-Minimierung während der Build-Erstellung mithilfe eines Tools wie gulp durchgeführt wird, soll beim Erstellen für eine Entwicklungsumgebung möglicherweise eine andere Minimierungsstufe verwendet werden als beim Erstellen für eine Staging- oder Produktionsumgebung.

Um dies zu unterstützen, fügt Cloud Manager diese Standard-Umgebungsvariablen bei jeder Ausführung dem Build-Container hinzu.

| **Variablenname** | **Definition** |
|---|---|
| CM_BUILD | Immer auf „true“ (wahr) festgelegt |
| BRANCH | Die konfigurierte Verzweigung für die Ausführung |
| CM_PIPELINE_ID | Numerische Pipeline-Kennung |
| CM_PIPELINE_NAME | Name der Pipeline |
| CM_PROGRAM_ID | Numerische Programmkennung |
| CM_PROGRAM_NAME | Name des Programms |
| ARTIFACTS_VERSION | Die von Cloud Manager generierte synthetische Version bei einer Staging- oder Produktions-Pipeline |

### Pipeline-Variablen {#pipeline-variables}

In einigen Fällen kann der Build-Prozess eines Kunden von bestimmten Konfigurationsvariablen abhängen, die nicht im Git-Repository platziert werden können oder zwischen Pipeline-Ausführungen mit derselben Verzweigung variieren müssen.

Cloud Manager ermöglicht die Konfiguration dieser Variablen über die Cloud Manager-API oder die Cloud Manager-CLI individuell für die Pipelines. Variablen können entweder als reiner Test oder mit Data-at-Rest-Verschlüsselung gespeichert werden. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die in der `pom.xml`-Datei oder anderen Build-Skripten referenziert werden kann.

Um eine Variable mithilfe der CLI festzulegen, führen Sie einen Befehl wie den folgenden aus:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

Aktuelle Variablen können aufgelistet werden:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Variablennamen dürfen nur alphanumerische Zeichen und Unterstriche (_) enthalten. Dabei sollten Großbuchstaben verwendet werden. Pro Pipeline sind maximal 200 Variablen zulässig. Jeder Name darf maximal 100 Zeichen und jeder Wert darf bei Variablen des Typs „String“ maximal 2048 Zeichen und bei Variablen des Typs „secretString“ maximal 500 Zeichen lang sein.

Bei Verwendung in einer `Maven pom.xml`-Datei ist es in der Regel hilfreich, diese Variablen Maven-Eigenschaften mit einer ähnlichen Syntax zuzuordnen:

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

Einige Builds erfordern die Installation zusätzlicher Systempakete, damit sie vollumfänglich funktionieren. So ist es z. B. möglich, dass ein Build ein Python- oder Ruby-Skript aufruft, wofür der entsprechende Sprach-Interpreter installiert sein muss. Dies kann durch Abfrage von [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) erfolgen, wodurch APT aufgerufen wird. Diese Ausführung sollte im Allgemeinen in einem Cloud Manager-spezifischen Maven-Profil eingeschlossen sein. So installieren Sie beispielsweise Python:

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
>Wenn Sie ein Systempaket auf diese Weise installieren, wird es **nicht** in der Laufzeitumgebung installiert, die für die Ausführung von Adobe Experience Manager verwendet wird. Wenn Sie ein Systempaket in der AEM-Umgebung installieren möchten, wenden Sie sich an Ihre Adobe-Support-Mitarbeiter.
