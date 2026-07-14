---
title: Dispatcher-Konfigurationen
description: Weitere Informationen zum Bereitstellen von Dispatcher-Konfigurationsdateien mit Cloud Manager
exl-id: ffc2b60e-bde7-48ca-b268-dea0f8fd4e30
TQID: https://experienceleague.adobe.com/KpGTN-444bigrhLddGnZvxkZsThcVc1B--oEoAKTdos
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 1692390e24f8fa7d719bd8293a99586ec4ec36d4
workflow-type: tm+mt
source-wordcount: 557
ht-degree: 44%

---

# Dispatcher-Konfigurationen {#manage-your-dispatcher-configurations}

Weitere Informationen zum Bereitstellen von Dispatcher-Konfigurationsdateien mit Cloud Manager

## Bereitstellen von Dispatcher-Konfigurationen mit Cloud Manager {#deploying-dispatcher-configurations}

Cloud Manager kann Webserver- und Dispatcher-Konfigurationsdateien bereitstellen, wenn diese mit standardmäßigen AEM-Inhaltspaketen im Git-Repository gespeichert sind.

Um diese Funktion zu verwenden, erstellt der Maven-Build eine ZIP-Datei, die mindestens zwei Verzeichnisse enthält: `conf` und `conf.d`. Diese .zip-Datei kann mit dem `maven-assembly-plugin` erstellt werden.

Projekte, die von Cloud Manager mit dem integrierten [Assistenten zur Projekterstellung](/help/getting-started/using-the-wizard.md) erstellt werden, haben automatisch die richtige Maven-Projektstruktur. Dieser Ansatz wird empfohlen, wenn Sie neu bei Adobe Managed Services (AMS) sind.

Wenn Sie eine Bereitstellung in einer Dispatcher-Instanz durchführen, werden die Verzeichnisse in der Instanz durch die Verzeichnisse aus Ihrem Git-Repository ersetzt. Um die entsprechenden Umgebungsvariablen in `/etc/sysconfig/httpd` korrekt festzulegen, arbeiten Sie mit Ihrem Customer Success-Team zusammen, da Webserver- und Dispatcher-Konfigurationsdateien häufig umgebungsspezifische Details erfordern.

## Dispatcher-Konfiguration für bestehende Managed Services-Kundschaft {#steps-for-configuring-dispatcher}

Gehen Sie wie folgt vor, um die anfängliche Konfiguration von Dispatcher abzuschließen:

1. Rufen Sie die aktuellen Produktionskonfigurationsdateien von Ihrem Customer Success-Team ab.
1. Entfernen Sie umgebungsspezifische Daten, z. B. Veröffentlichungs-Renderer-IPs, und ersetzen Sie sie durch Variablen.
1. Definieren Sie erforderliche Variablen in Schlüssel/Wert-Paaren für jede Ziel-Dispatcher und fügen Sie sie in jeder Instanz dem Ordner [Variablen](https://experienceleague.adobe.com/en/docs/experience-manager-learn/ams/dispatcher/variables) hinzu.
1. Testen Sie die aktualisierten Konfigurationen in Ihrer Staging-Umgebung.
1. Bitten Sie nach dem Test Ihr Customer Success-Team, für die Produktion bereitzustellen.
1. Übertragen Sie die Dateien in das Git-Repository.
1. Führen Sie eine Bereitstellung über Cloud Manager durch.

>[!NOTE]
>
>Die Migration der Dispatcher- und Webserverkonfigurationen in Ihr Git-Repository erfolgt beim Cloud Manager-Onboarding, kann aber auch später durchgeführt werden.

### Beispiel {#example}

Die spezifische Datei- und Verzeichnisstruktur variiert je nach den spezifischen Vorgaben Ihres Projekts. Dieses Beispiel bietet jedoch eine klare Erklärung dafür, wie Sie Ihr Projekt strukturieren und Apache- und Dispatcher-Konfigurationen einschließen können.

1. Erstellen Sie ein Unterverzeichnis mit dem Namen `dispatcher`.

   Verwenden Sie hier einen beliebigen Namen, aber der in diesem Schritt erstellte Verzeichnisname muss mit dem in Schritt 1 verwendeten Namen übereinstimmen.

1. Dieses Unterverzeichnis enthält ein Maven-Modul, das die ZIP-Datei des Dispatchers mit dem `maven-assembly-plugin` erstellt. Erstellen Sie im Verzeichnis `dispatcher` eine Datei `pom.xml` mit diesem Inhalt, indem Sie den `parent`-Verweis, die `artifactId` und den `name` nach Bedarf ändern.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <project xmlns="http://maven.apache.org/POM/4.0.0"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
       <modelVersion>4.0.0</modelVersion>
       <parent>
           <!-- reference to your parent pom -->
       </parent>
   
       <artifactId>dispatcher</artifactId> <!-- feel free to change this -->
       <packaging>pom</packaging>
       <name>dispatcher</name> <!-- feel free to change this -->
   
       <build>
           <plugins>
               <plugin>
                   <groupId>org.apache.maven.plugins</groupId>
                   <artifactId>maven-assembly-plugin</artifactId>
                   <version>3.1.0</version>
                   <executions>
                       <execution>
                           <phase>package</phase>
                           <goals><goal>single</goal></goals>
                           <configuration>
                               <descriptors>
                                   <descriptor>assembly.xml</descriptor>
                               </descriptors>
                               <appendAssemblyId>false</appendAssemblyId>
                           </configuration>
                       </execution>
                   </executions>
               </plugin>
           </plugins>
       </build>
   </project>
   ```

   * Wie in Schritt 1 können die artifactId und der Name andere Werte sein. `dispatcher` wird hier als Beispiel verwendet.

1. Für die `maven-assembly-plugin` ist ein `descriptor` erforderlich, um zu definieren, wie die ZIP-Datei erstellt wird. Erstellen Sie zum Erstellen dieses Deskriptors eine Datei im Unterverzeichnis `dispatcher` mit dem Namen `assembly.xml`, die diesen Inhalt enthält. Beachten Sie, dass in der Datei `pom.xml` oben in Zeile 26 auf diesen Dateinamen verwiesen wird.

   ```xml
   <assembly xmlns="http://maven.apache.org/ASSEMBLY/2.0.0"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://maven.apache.org/ASSEMBLY/2.0.0 http://maven.apache.org/xsd/assembly-2.0.0.xsd">
     <id>distribution</id>
     <formats>
       <format>zip</format>
     </formats>
     <includeBaseDirectory>false</includeBaseDirectory>
     <fileSets>
       <fileSet>
         <directory>${basedir}/src</directory>
         <includes>
           <include>**/*</include>
         </includes>
         <outputDirectory></outputDirectory>
       </fileSet>
     </fileSets>
   </assembly>
   ```

1. Erstellen Sie jetzt ein Unterverzeichnis mit dem Namen `src` (wie im Assembly-Deskriptor oben in Zeile 11) innerhalb des Dispatcher-Unterverzeichnisses, um die tatsächlichen Apache- und Dispatcher-Konfigurationen zu speichern. Erstellen Sie in diesem Verzeichnis `src` weitere Verzeichnisse mit den Namen `conf`, `conf.d`, `conf.dispatcher.d` und `conf.modules.d`.

1. Befüllen Sie die `conf`, `conf.d`, `conf.dispatcher.d` und `conf.modules.d`-Verzeichnisse mit Ihren Konfigurationsdateien. Die Standardkonfiguration besteht beispielsweise aus diesen Dateien und symbolischen Links.

   ```
   dispatcher
   ├── assembly.xml
   ├── pom.xml
   └── src
       ├── conf
       │  ├── httpd.conf
       │  └── magic
       ├── conf.d
       │  ├── README
       │  ├── autoindex.conf
       │  ├── available_vhosts
       │  │  ├── aem_author.vhost
       │  │  ├── aem_flush.vhost
       │  │  ├── aem_health.vhost
       │  │  ├── aem_lc.vhost
       │  │  └── aem_publish.vhost
       │  ├── dispatcher_vhost.conf
       │  ├── enabled_vhosts
       │  │  ├── aem_author.vhost -> ../available_vhosts/aem_author.vhost
       │  │  ├── aem_flush.vhost -> ../available_vhosts/aem_flush.vhost
       │  │  └── aem_publish.vhost -> ../available_vhosts/aem_publish.vhost
       │  ├── rewrites
       │  │  ├── base_rewrite.rules
       │  │  └── xforwarded_forcessl_rewrite.rules
       │  ├── userdir.conf
       │  ├── variables
       │  │  └── ams_default.vars
       │  ├── welcome.conf
       │  └── whitelists
       │      └── 000_base_whitelist.rules
       ├── conf.dispatcher.d
       │  ├── available_farms
       │  │  ├── 000_ams_author_farm.any
       │  │  ├── 001_ams_lc_farm.any
       │  │  └── 999_ams_publish_farm.any
       │  ├── cache
       │  │  ├── ams_author_cache.any
       │  │  ├── ams_author_invalidate_allowed.any
       │  │  ├── ams_publish_cache.any
       │  │  └── ams_publish_invalidate_allowed.any
       │  ├── clientheaders
       │  │  ├── ams_author_clientheaders.any
       │  │  ├── ams_common_clientheaders.any
       │  │  ├── ams_lc_clientheaders.any
       │  │  └── ams_publish_clientheaders.any
       │  ├── dispatcher.any
       │  ├── enabled_farms
       │  │  ├── 000_ams_author_farm.any -> ../available_farms/000_ams_author_farm.any
       │  │  └── 999_ams_publish_farm.any -> ../available_farms/999_ams_publish_farm.any
       │  ├── filters
       │  │  ├── ams_author_filters.any
       │  │  ├── ams_lc_filters.any
       │  │  └── ams_publish_filters.any
       │  ├── renders
       │  │  ├── ams_author_renders.any
       │  │  ├── ams_lc_renders.any
       │  │  └── ams_publish_renders.any
       │  └── vhosts
       │      ├── ams_author_vhosts.any
       │      ├── ams_lc_vhosts.any
       │      └── ams_publish_vhosts.any
       └── conf.modules.d
           ├── 00-base.conf
           ├── 00-dav.conf
           ├── 00-lua.conf
           ├── 00-mpm.conf
           ├── 00-proxy.conf
           ├── 00-systemd.conf
           ├── 01-cgi.conf
           └── 02-dispatcher.conf
   ```

1. Fügen Sie abschließend in der `pom.xml`-Datei im Stammverzeichnis Ihres Projekts ein `<module>` hinzu, um das Dispatcher-Modul einzuschließen.

   Wenn Ihre vorhandene Modulliste beispielsweise wie folgt aussieht:

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
       </modules>
   ```

   Ändern Sie sie zu Folgendem:

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
           <module>dispatcher</module>
       </modules>
   ```

   * Wie in Schritt 1 erwähnt, muss der Wert des Elements `<module>` mit dem erstellten Verzeichnisnamen übereinstimmen.

1. Führen Sie zum Testen das `mvn clean package` im Stammverzeichnis des Projekts aus. In der Ausgabe sehen Sie Zeilen wie diese.

   ```
   [INFO] --- maven-assembly-plugin:3.1.0:single (default) @ dispatcher ---
   [INFO] Reading assembly descriptor: assembly.xml
   [INFO] Building zip: /Users/me/mycompany/dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
   ```

   Sie können diese Datei auch entpacken, um ihren Inhalt anzuzeigen.

   ```shell
   $ unzip -l dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
   Archive:  dispatcher/target/dispatcher-1.0-SNAPSHOT.zip
     Length      Date    Time    Name
   ---------  ---------- -----   ----
           0  09-12-2018 12:53   conf.modules.d/
           0  10-19-2018 10:38   conf.dispatcher.d/
           0  09-12-2018 12:53   conf.dispatcher.d/available_farms/
           0  09-12-2018 12:53   conf.dispatcher.d/filters/
           0  09-12-2018 12:53   conf.dispatcher.d/renders/
           0  09-12-2018 12:53   conf.dispatcher.d/cache/
           0  09-12-2018 12:53   conf.dispatcher.d/clientheaders/
           0  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/
           0  09-12-2018 12:53   conf.dispatcher.d/vhosts/
           0  09-12-2018 12:53   conf.d/
           0  09-12-2018 12:53   conf.d/rewrites/
           0  09-12-2018 12:53   conf.d/whitelists/
           0  09-12-2018 12:53   conf.d/variables/
           0  11-01-2018 13:53   conf.d/enabled_vhosts/
           0  09-12-2018 12:53   conf.d/available_vhosts/
           0  09-12-2018 12:53   conf/
          88  09-12-2018 12:53   conf.modules.d/00-systemd.conf
        4913  09-12-2018 12:53   conf.dispatcher.d/available_farms/999_ams_publish_farm.any
         152  09-12-2018 12:53   conf.dispatcher.d/renders/ams_lc_renders.any
         490  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_common_clientheaders.any
        1727  09-12-2018 12:53   conf.d/rewrites/base_rewrite.rules
          36  09-12-2018 12:53   conf.d/enabled_vhosts/aem_author.vhost
       11753  09-12-2018 12:53   conf/httpd.conf
         957  09-12-2018 12:53   conf.modules.d/00-proxy.conf
         944  09-12-2018 12:53   conf.dispatcher.d/available_farms/001_ams_lc_farm.any
         220  09-12-2018 12:53   conf.dispatcher.d/cache/ams_author_invalidate_allowed.any
          43  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/999_ams_publish_farm.any
         516  09-12-2018 12:53   conf.d/welcome.conf
          37  09-12-2018 12:53   conf.d/enabled_vhosts/aem_publish.vhost
       13077  09-12-2018 12:53   conf/magic
          96  09-12-2018 12:53   conf.modules.d/02-dispatcher.conf
        2601  09-12-2018 12:53   conf.dispatcher.d/available_farms/000_ams_author_farm.any
         837  09-12-2018 12:53   conf.dispatcher.d/cache/ams_author_cache.any
          42  09-12-2018 12:53   conf.dispatcher.d/enabled_farms/000_ams_author_farm.any
        2926  09-12-2018 12:53   conf.d/autoindex.conf
        2555  09-12-2018 12:53   conf.d/available_vhosts/aem_lc.vhost
          41  09-12-2018 12:53   conf.modules.d/00-lua.conf
        2234  09-12-2018 12:53   conf.dispatcher.d/filters/ams_publish_filters.any
         220  09-12-2018 12:53   conf.dispatcher.d/cache/ams_publish_invalidate_allowed.any
         402  09-12-2018 12:53   conf.dispatcher.d/dispatcher.any
         573  09-12-2018 12:53   conf.d/whitelists/000_base_whitelist.rules
         871  09-12-2018 12:53   conf.d/available_vhosts/aem_flush.vhost
         139  09-12-2018 12:53   conf.modules.d/00-dav.conf
         742  09-12-2018 12:53   conf.dispatcher.d/filters/ams_author_filters.any
         557  09-12-2018 12:53   conf.dispatcher.d/cache/ams_publish_cache.any
         105  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_lc_vhosts.any
         101  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_publish_vhosts.any
        3582  09-12-2018 12:53   conf.d/dispatcher_vhost.conf
        2529  09-12-2018 12:53   conf.d/available_vhosts/aem_publish.vhost
         742  09-12-2018 12:53   conf.modules.d/00-mpm.conf
          88  09-12-2018 12:53   conf.dispatcher.d/filters/ams_lc_filters.any
         177  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_lc_clientheaders.any
         366  09-12-2018 12:53   conf.d/README
        2723  09-12-2018 12:53   conf.d/available_vhosts/aem_author.vhost
        3739  09-12-2018 12:53   conf.modules.d/00-base.conf
         138  09-12-2018 12:53   conf.dispatcher.d/renders/ams_author_renders.any
          44  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any
         112  09-12-2018 12:53   conf.dispatcher.d/vhosts/ams_author_vhosts.any
         580  09-12-2018 12:53   conf.d/variables/ams_default.vars
          35  09-12-2018 12:53   conf.d/enabled_vhosts/aem_flush.vhost
        1252  09-12-2018 12:53   conf.d/userdir.conf
         451  09-12-2018 12:53   conf.modules.d/01-cgi.conf
         321  09-12-2018 12:53   conf.dispatcher.d/renders/ams_publish_renders.any
         170  09-12-2018 12:53   conf.dispatcher.d/clientheaders/ams_author_clientheaders.any
         220  09-12-2018 12:53   conf.d/rewrites/xforwarded_forcessl_rewrite.rules
        1753  09-12-2018 12:53   conf.d/available_vhosts/aem_health.vhost
   ---------                     -------
       69017                     66 files
   ```
