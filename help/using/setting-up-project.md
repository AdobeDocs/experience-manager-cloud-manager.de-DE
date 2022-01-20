---
title: Einrichten des Projekts
description: Auf dieser Seite erfahren Sie, wie Sie ein Projekt einrichten
feature: Getting Started, Production Programs
exl-id: ed994daf-0195-485a-a8b1-87796bc013fa
source-git-commit: 8861b5e48b8e1d081b4c8653000a8f2cf16dd11f
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 68%

---

# Einrichten des Projekts {#setting-up-your-project}

## Ändern der Projekteinstellungen {#modifying-project-setup-details}

Damit vorhandene AEM-Projekte erfolgreich in Cloud Manager erstellt und bereitgestellt werden können, müssen einige grundlegende Regeln berücksichtigt werden:

* Projekte müssen mit Apache Maven erstellt werden.
* Im Stammverzeichnis des Git-Repositorys muss eine *pom.xml*-Datei vorhanden sein. Diese *pom.xml*-Datei kann ggf. auf beliebig viele Untermodule verweisen (die wiederum weitere Untermodule umfassen usw.) wie nötig.

* Sie können Verweise auf weitere Maven-Artefakt-Repositorys in Ihren *pom.xml*-Dateien hinzufügen. Der Zugriff auf [kennwortgeschützte Artefakt-Repositorys](#password-protected-maven-repositories) wird bei entsprechender Konfiguration unterstützt. Allerdings wird der Zugriff auf netzwerkgeschützte Artefakte nicht unterstützt.
* Bereitstellbare Inhaltspakete werden erkannt, wenn Sie nach Inhaltspaketen im *ZIP*-Format suchen, die in einem Verzeichnis mit dem Namen *target* enthalten sind. Eine beliebige Anzahl von Untermodulen kann Inhaltspakete produzieren.

* Bereitstellbare Dispatcher-Artefakte werden erkannt, wenn Sie nach *ZIP*-Dateien (ebenfalls in einem Verzeichnis namens *target*) suchen, die Verzeichnisse mit den Namen *conf* und *conf.d* enthalten.

* Wenn mehrere Inhaltspakete vorhanden sind, ist die Reihenfolge der Paketimplementierungen nicht garantiert. Wenn eine bestimmte Reihenfolge benötigt wird, können die Abhängigkeiten des Inhaltspakets zum Definieren der Reihenfolge verwendet werden. Pakete können bei der Implementierung [übersprungen](#skipping-content-packages) werden.


## Aktivieren von Maven-Profilen in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In einigen wenigen Fällen müssen Sie den Build-Prozess möglicherweise etwas anders gestalten, wenn er in Cloud Manager und auf Entwickler-Workstations ausgeführt wird. In diesen Fällen können Sie mit [Maven-Profilen](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) definieren, wie der Build in verschiedenen Umgebungen (einschließlich Cloud Manager) abweichen soll.

Die Aktivierung eines Maven-Profils in der Cloud Manager-Build-Umgebung sollte über die oben beschriebene Umgebungsvariable CM_BUILD erfolgen. Beim Erstellen eines Profils, das nur außerhalb der Cloud Manager-Build-Umgebung verwendet werden soll, sollte hingegen das Nichtvorhandensein dieser Variable verifiziert werden.

Wenn zum Beispiel eine einfache Nachricht nur dann ausgegeben werden soll, wenn der Build innerhalb von Cloud Manager ausgeführt wird, verwenden Sie Folgendes:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Um dieses Profil auf einer Entwickler-Workstation zu testen, können Sie es entweder in der Befehlszeile (mit `-PcmBuild`) oder in der integrierten Entwicklungsumgebung (IDE) aktivieren.

Wenn zum Beispiel eine einfache Nachricht nur dann ausgegeben werden soll, wenn der Build außerhalb von Cloud Manager ausgeführt wird, verwenden Sie Folgendes:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

## Unterstützung für kennwortgeschütztes Maven-Repository {#password-protected-maven-repositories}

>[!NOTE]
>Artefakte aus einem passwortgeschützten Maven-Repository sollten nur sehr vorsichtig verwendet werden, da Code, der über diesen Mechanismus bereitgestellt wird, derzeit nicht die in den Quality Gates von Cloud Manager implementierenten Qualitätsregeln durchläuft. Daher sollten sie nur in seltenen Fällen und nur für Code verwendet werden, der nicht an AEM gebunden ist. Es wird empfohlen, neben der Binärdatei auch die Java-Quellen sowie den gesamten Projektquell-Code bereitzustellen.

Um ein kennwortgeschütztes Maven-Repository aus Cloud Manager zu verwenden, geben Sie das Kennwort (und optional den Benutzernamen) als geheime [Pipeline-Variable](/help/using/build-environment-details.md#pipeline-variables) an und verweisen Sie dann in einer Datei im git-Repository mit dem Namen `.cloudmanager/maven/settings.xml` auf dieses Geheimnis. Diese Datei folgt dem Schema der [Maven-Einstellungsdatei](https://maven.apache.org/settings.html). Wenn der Build-Vorgang von Cloud Manager gestartet wird, wird das `<servers>`-Element in dieser Datei mit der von Cloud Manager bereitgestellten `settings.xml`-Standarddatei zusammengeführt. Server-IDs, die mit `adobe` und `cloud-manager` beginnen, gelten als reserviert und sollten nicht von kundenspezifischen Servern verwendet werden. Server-IDs, die **nicht** mit einem dieser Präfixe oder der Standard-ID `central` übereinstimmen, werden von Cloud Manager niemals gespiegelt. Wenn diese Datei vorhanden ist, wird die Server-ID von innerhalb eines `<repository>`- und/oder `<pluginRepository>`-Elements in der `pom.xml`-Datei referenziert. Im Allgemeinen wären diese `<repository>`- und/oder `<pluginRepository>`-Elemente in einem [Cloud Manager-spezifischen Profil](#activating-maven-profiles-in-cloud-manager) enthalten, auch wenn dies nicht unbedingt erforderlich ist.

Beispiel: Das Repository befindet sich unter https://repository.myco.com/maven2, der von Cloud Manager zu verwendende Benutzername lautet `cloudmanager` und das Kennwort lautet `secretword`.

Legen Sie zunächst in der Pipeline das Kennwort als Geheimnis fest:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

Verweisen Sie anschließend aus der `.cloudmanager/maven/settings.xml`-Datei darauf:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

Verweisen Sie schließlich auf die Server-ID in der `pom.xml`-Datei:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
```

### Bereitstellen von Quellen {#deploying-sources}

Es empfiehlt sich, die Java-Quellen zusammen mit der Binärdatei in einem Maven-Repository bereitzustellen.

Konfigurieren Sie das maven-source-plugin in Ihrem Projekt:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-source-plugin</artifactId>
            <executions>
                <execution>
                    <id>attach-sources</id>
                    <goals>
                        <goal>jar-no-fork</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
```

### Bereitstellen von Projektquellen {#deploying-project-sources}

Es empfiehlt sich, die gesamte Projektquelle zusammen mit den Binärdaten in einem Maven-Respository bereitzustellen. Dies erlaubt die Neuerstellung des exakten Artefakts.

Konfigurieren Sie das maven-assembly-plugin in Ihrem Projekt:

```xml
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-assembly-plugin</artifactId>
            <executions>
                <execution>
                    <id>project-assembly</id>
                    <phase>package</phase>
                    <goals>
                        <goal>single</goal>
                    </goals>
                    <configuration>
                        <descriptorRefs>
                            <descriptorRef>project</descriptorRef>
                        </descriptorRefs>
                    </configuration>
                </execution>
            </executions>
        </plugin>
```

## Überspringen von Inhaltspaketen {#skipping-content-packages}

In Cloud Manager können Builds eine beliebige Anzahl von Inhaltspaketen generieren.
Aus vielerlei Gründen kann es sinnvoll sein, ein Inhaltspaket zu erstellen, es jedoch nicht bereitzustellen. Dies kann nützlich sein, etwa für Inhaltspakete, die nur zum Testen erstellt wurden, oder für Pakete, die in einem anderen Schritt im Build-Prozess (also als Unterpaket eines anderen Pakets) neu verpackt werden.

Um diese Szenarien zu berücksichtigen, sucht Cloud Manager in den Eigenschaften erstellter Inhaltspakete nach einer Eigenschaft namens ***cloudManagerTarget***. Wenn diese Eigenschaft auf „Ohne“ festgelegt ist, wird das Paket übersprungen und nicht bereitgestellt. Der Mechanismus zum Festlegen dieser Eigenschaft hängt davon ab, wie der Build das Inhaltspaket erzeugt. Mit dem filevault-maven-plugin würden Sie beispielsweise das Plug-in wie folgt konfigurieren:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Mit dem content-package-maven-plugin ist es ähnlich:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

## Artefakt-Wiederverwendung erstellen {#build-artifact-reuse}

In vielen Fällen wird derselbe Code in mehreren AEM-Umgebungen bereitgestellt. Wenn festgestellt wird, dass dieselbe Git-Übertragung in mehreren Pipelineausführungen mit vollem Stapel verwendet wird, verhindert Cloud Manager, dass die Codebasis neu erstellt wird.

Wenn eine Ausführung gestartet wird, wird der aktuelle HEAD-Commit für die Zweig-Pipeline extrahiert. Der Commit-Hash ist in der Benutzeroberfläche und über die API sichtbar. Wenn der Build-Schritt erfolgreich abgeschlossen wurde, werden die resultierenden Artefakte basierend auf diesem Commit-Hash gespeichert und können in nachfolgenden Pipeline-Ausführungen wiederverwendet werden. Wenn eine Wiederverwendung erfolgt, werden die Build- und Codequalitätsschritte effektiv durch die Ergebnisse der ursprünglichen Ausführung ersetzt. In der Protokolldatei für den Build-Schritt werden die Artefakte und die Ausführungsinformationen aufgelistet, die ursprünglich zum Erstellen verwendet wurden.

Im Folgenden finden Sie ein Beispiel für eine solche Protokollausgabe.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Das Protokoll des Codequalitätsschritts enthält ähnliche Informationen.

### Opt-out {#opting-out}

Falls gewünscht, kann das Wiederverwendungsverhalten für bestimmte Pipelines deaktiviert werden, indem die Pipeline-Variable festgelegt wird. `CM_DISABLE_BUILD_REUSE` nach `true`. Wenn diese Variable festgelegt ist, wird der Commit-Hash weiterhin extrahiert und die resultierenden Artefakte werden zur späteren Verwendung gespeichert, aber alle zuvor gespeicherten Artefakte werden nicht wiederverwendet. Um dieses Verhalten zu verstehen, sehen Sie sich das folgende Szenario an.

1. Eine neue Pipeline wird erstellt.
1. Die Pipeline wird ausgeführt (Ausführung #1) und der aktuelle HEAD-Commit lautet `becdddb`. Die Ausführung ist erfolgreich und die resultierenden Artefakte werden gespeichert.
1. Die `CM_DISABLE_BUILD_REUSE` festgelegt ist.
1. Die Pipeline wird erneut ausgeführt, ohne den Code zu ändern. Es sind zwar gespeicherte Artefakte vorhanden, die mit `becdddb`, werden sie aufgrund der `CM_DISABLE_BUILD_REUSE` -Variable.
1. Der Code wird geändert und die Pipeline wird ausgeführt. Der HEAD-Commit ist jetzt `f6ac5e6`. Die Ausführung ist erfolgreich und die resultierenden Artefakte werden gespeichert.
1. Die `CM_DISABLE_BUILD_REUSE` wird gelöscht.
1. Die Pipeline wird erneut ausgeführt, ohne den Code zu ändern. Da gespeicherte Artefakte mit `f6ac5e6`, werden diese Artefakte wiederverwendet.

### Einschränkungen {#caveats}

* [Umgang mit Maven-Versionen](/help/using/activating-maven-project.md) die Projektversion nur in Produktions-Pipelines ersetzen. Wenn daher derselbe Commit sowohl für die Ausführung einer Entwicklungs-Bereitstellung als auch für die Ausführung einer Produktions-Pipeline verwendet wird und die Entwicklungs-Bereitstellungs-Pipeline zuerst ausgeführt wird, werden die Versionen in der Staging- und Produktionsumgebung bereitgestellt, ohne dass Änderungen vorgenommen werden. In diesem Fall wird jedoch weiterhin ein Tag erstellt.
* Wenn das Abrufen der gespeicherten Artefakte nicht erfolgreich ist, wird der Build-Schritt so ausgeführt, als ob keine Artefakte gespeichert worden wären.
* Andere Pipeline-Variablen als `CM_DISABLE_BUILD_REUSE` werden nicht berücksichtigt, wenn Cloud Manager beschließt, zuvor erstellte Build-Artefakte wiederzuverwenden.

## Entwickeln von Code basierend auf Best Practices {#develop-your-code-based-on-best-practices}

Die Entwicklungs- und Beratungsteams von Adobe haben einen [umfassenden Satz an Best Practices für AEM-Entwickler zusammengestellt.](https://helpx.adobe.com/de/experience-manager/6-4/sites/developing/using/best-practices.html)
