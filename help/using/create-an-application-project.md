---
title: Erstellen eines AEM-Anwendungsprojekts
seo-title: Erstellen eines AEM-Anwendungsprojekts
description: 'null'
seo-description: Auf dieser Seite erfahren Sie, wie Sie bei den ersten Schritten mit Cloud Manager ein AEM-Projekt einrichten.
uuid: 7b976ebf-5358-49d8-a58d-0bae026303fa
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: Erste Schritte
discoiquuid: 76c1a8e4-d66f-4a3b-8c0c-b80c9e17700e
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Erstellen eines AEM-Anwendungsprojekts {#create-an-aem-application-project}

## Arbeiten mit dem Assistenten zum Erstellen eines AEM-Anwendungsprojekts {#using-wizard-to-create-an-aem-application-project}

Wenn Kunden Cloud Manager erstmals verwenden, erhalten sie ein leeres Git-Repository. Kunden, die bereits Adobe Managed Services (AMS) verwenden (oder ihre lokale AEM-Lösung zu AMS migrieren), verfügen im Allgemeinen bereits über Projektcode in Git (oder einem anderen Versionskontrollsystem) und importieren ihr Projekt in das Cloud Manager-Repository. Neue Kunden verfügen jedoch nicht über vorhandene Projekte.

Um neuen Kunden die ersten Schritte zu erleichtern, kann Cloud Manager jetzt als Ausgangspunkt ein minimales AEM-Projekt erstellen. Dieser Vorgang basiert auf dem [**AEM Project Archetype**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T12:52:50.071-0400

2018.8.0: Added this new section

 -->

Gehen Sie wie folgt vor, um ein AEM-Anwendungsprojekt in Cloud Manager zu erstellen:

1. Wenn Sie sich bei Cloud Manager anmelden und die grundlegende Programmeinrichtung abgeschlossen haben und das Repository zu diesem Zeitpunkt leer ist, wird im Bildschirm **Überblick** eine spezielle Aktionskarte angezeigt.

   ![](assets/image2018-10-3_14-29-44.png)

1. Klicken Sie auf **Erstellen**, um zum Bildschirm **Pipeline-Einrichtung** zu gelangen.

   ![](assets/image2018-10-3_14-30-22.png)

1. Klicken Sie auf **Erstellen**, um ein Dialogfeld zu öffnen, in dem Sie die für den AEM-Projektarchetyp erforderlichen Parameter angeben. Das Dialogfeld fragt standardmäßig zwei Werte ab:

   * **Titel**: Hier ist standardmäßig der *Programmname* angegeben.

   * **Neuer Verzweigungsname**: Hier ist standardmäßig *Master* angegeben.
   ![](assets/screen_shot_2018-10-08at55825am.png)

   Sie können das Dialogfeld über einen Ziehpunkt am unteren Rand des Dialogfelds erweitern. Das erweiterte Dialogfeld zeigt alle Konfigurationsparameter für den Archetyp an. Viele dieser Parameter verfügen über Standardwerte, die basierend auf dem **Titel** erstellt werden.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Wenn der **Titel** beispielsweise ***We.Finance*** lautet, wird der Parameter „Base Maven Artifact ID“ als ***com.wefinance*** generiert. Diese Werte können bei Bedarf geändert werden.
   >
   >
   >Den generierten Wert ***com.wefinance*** können Sie zum Beispiel in ***net.wefinance*** ändern.

1. Klicken Sie im vorherigen Schritt auf **Erstellen**, um das Starterprojekt mit dem Archetyp zu erstellen und in die benannte Git-Verzweigung zu übertragen. Anschließend können Sie die Pipeline einrichten.

## Einrichten des Projekts {#setting-up-your-project}

### Ändern der Projekteinstellungen {#modifying-project-setup-details}

Damit vorhandene AEM-Projekte erfolgreich in Cloud Manager erstellt und bereitgestellt werden können, müssen einige grundlegende Regeln berücksichtigt werden:

* Projekte müssen mit Apache Maven erstellt werden.
* Im Stammverzeichnis des Git-Repositorys muss eine Datei *pom.xml* vorhanden sein. Diese *pom.xml*-Datei kann ggf. auf beliebig viele Untermodule verweisen (die wiederum weitere Untermodule umfassen usw.) wie nötig.

* Sie können Verweise auf weitere Maven-Artefakt-Repositorys in Ihren *pom.xml*-Dateien hinzufügen. Allerdings wird der Zugriff auf kennwortgeschützte oder netzwerkgeschützte Artefakte nicht unterstützt.
* Bereitstellbare Inhaltspakete werden erkannt, wenn Sie nach Inhaltspaketen im *ZIP*-Format suchen, die in einem Verzeichnis mit dem Namen *target* enthalten sind. Eine beliebige Anzahl von Untermodulen kann Inhaltspakete produzieren.

* Bereitstellbare Dispatcher-Artefakte werden erkannt, wenn Sie nach *ZIP*-Dateien (ebenfalls in einem Verzeichnis namens *target*) suchen, die Verzeichnisse mit den Namen *conf* und *conf.d* enthalten.

* Wenn mehrere Inhaltspakete vorhanden sind, ist die Reihenfolge der Paketbereitstellungen nicht garantiert. Wenn eine bestimmte Reihenfolge benötigt wird, können die Abhängigkeiten des Inhaltspakets zum Definieren der Reihenfolge verwendet werden.

<!-- 

Comment Type: annotation
Last Modified By: jsyal
Last Modified Date: 2018-10-08T09:20:10.106-0400

2018.8.0: added existing in the opening sentence

 -->

## Details der Build-Umgebung {#build-environment-details}

Cloud Manager erstellt und testet Ihren Code mithilfe einer speziellen Laufzeitumgebung ****. Diese Umgebung weist die folgenden Attribute auf:

* Die Build-Umgebung ist Linux-basiert.
* Apache Maven 3.6.0 ist installiert.
* Die installierte Java-Version ist Oracle JDK 8u181.
* Es sind einige zusätzliche erforderliche Systempakete installiert:

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * graphicsmagick
   * Wenn Sie weitere Pakete benötigen, müssen Sie diese über Ihre Customer Success Engineers (CSE) anfordern.

* Maven wird immer mit folgendem Befehl ausgeführt: *mvn --batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* Maven wird auf Systemebene mit einer settings.xml-Datei konfiguriert, die automatisch das öffentliche Adobe-**Artefakt**-Repository enthält. (Weitere [Informationen finden Sie im öffentlichen Maven-Repository](https://repo.adobe.com/) von Adobe.)

## Aktivieren von Maven-Profilen in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In einigen wenigen Fällen müssen Sie den Build-Prozess möglicherweise etwas anders gestalten, wenn er in Cloud Manager und auf Entwickler-Workstations ausgeführt wird. In diesen Fällen können Sie mit [Maven-Profilen](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) definieren, wie der Build in verschiedenen Umgebungen (einschließlich Cloud Manager) abweichen soll.

Die Aktivierung eines Maven-Profils in der Cloud Manager-Build-Umgebung sollte durch die Suche nach einer Umgebungsvariablen mit dem Namen `CM_BUILD` erfolgen. Diese Variable wird immer in der Cloud Manager-Build-Umgebung festgelegt. Beim Erstellen eines Profils, das nur außerhalb der Cloud Manager-Build-Umgebung verwendet werden soll, sollte hingegen das Nichtvorhandensein dieser Variable verifiziert werden.

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

## Benutzerdefinierte Umgebungsvariablen

In einigen Fällen kann der Build-Prozess eines Kunden von bestimmten Konfigurationsvariablen abhängen, die nicht im Git-Repository platziert werden sollten. Diese Variablen können von einem Customer Success Engineer (CSE) kundenbasiert konfiguriert werden. Sie werden an einem sicheren Speicherort gespeichert und sind nur im Build-Container für den jeweiligen Kunden sichtbar. Kunden, die diese Funktion verwenden möchten, müssen diese Variablen von ihrem CSE konfigurieren lassen.

Nach der Konfiguration sind diese Variablen als Umgebungsvariablen verfügbar. Um sie als Maven-Eigenschaften zu verwenden, können Sie sie in Ihrer Datei pom.xml referenzieren, möglicherweise in einem Profil wie oben beschrieben:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>Umgebungsvariablennamen dürfen nur alphanumerische Zeichen und Unterstrich (_) enthalten. In der Regel müssen die Namen großbuchstaben sein.

## Entwickeln von Code basierend auf Best Practices {#develop-your-code-based-on-best-practices}

Adobe Engineering and Consulting Teams haben einen [umfassenden Satz an Best Practices für AEM-Entwickler entwickelt](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/best-practices.html).
