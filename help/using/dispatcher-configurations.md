---
title: Verwalten von Dispatcher-Konfigurationen
seo-title: Verwalten von Dispatcher-Konfigurationen
description: 'null'
seo-description: Auf dieser Seite erhalten Sie Informationen zum Konfigurieren des Dispatchers.
uuid: 3ecd8ca3-5241-4811-87fd-3284a8012eda
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: Erste Schritte
discoiquuid: 8888dd80-d908-464e-927d-779db1a832a4
translation-type: ht
source-git-commit: e0a280efddb1e31f5aef65f0f52fc5b4e71de3da

---


# Verwalten von Dispatcher-Konfigurationen {#manage-your-dispatcher-configurations}

## Verwenden von Cloud Manager zum Bereitstellen von Dispatcher-Konfigurationsdateien {#using-cloud-manager-to-deploy-dispatcher-configuration-files}

Cloud Manager kann Webserver- und Dispatcher-Konfigurationsdateien bereitstellen, sofern diese nicht nur in den normalen AEM-Inhaltspaketen, sondern auch im **Git-Repository** gespeichert sind.

Um diese Funktion nutzen zu können, sollte der Maven-Build eine ZIP-Datei erstellen, die mindestens zwei Verzeichnisse enthält – ***conf*** und ***conf.d***. Diese ZIP-Datei kann mit dem Maven-Assembly-Plug-in erstellt werden. Projekte, die von Cloud Manager mithilfe des integrierten [Assistenten](create-an-application-project.md) erstellt wurden, haben die korrekte Maven-Projektstruktur, da diese bei der Projekterstellung erstellt wurde. Dies ist der empfohlene Pfad für neue Managed Services-Kunden.

Beim Bereitstellen einer **Dispatcher-Instanz** ersetzt der Inhalt dieser Verzeichnisse den Inhalt der entsprechenden Verzeichnisse in der Dispatcher-Instanz. Da Webserver- und Dispatcher-Konfigurationsdateien häufig umgebungsspezifische Informationen benötigen, müssen Sie zur korrekten Nutzung dieser Funktion zunächst diese Umgebungsvariablen in ***/etc/sysconfig/httpd*** mithilfe Ihrer Customer Success Engineers (CSE) festlegen.

### Schritte zur Dispatcher-Konfiguration für bestehende Managed Services-Kunden {#steps-for-configuring-dispatcher}

Führen Sie die folgenden Schritte aus, um den ersten Prozess bei der Dispatcherkonfiguration abzuschließen:

1. Beziehen Sie die aktuellen Produktionskonfigurationsdateien von Ihrem CSE.
1. Entfernen Sie hartcodierte umgebungsspezifische Daten (z. B. Publish-Renderer-IP-Adresse) und ersetzen Sie sie durch Variablen.
1. Definieren Sie erforderliche Variablen in Schlüssel/Wert-Paaren für jeden Ziel-Dispatcher und bitten Sie Ihren CSE, diese in jeder Instanz zu ***/etc/sysconfig/httpd*** hinzuzufügen.
1. Testen Sie die aktualisierten Konfigurationen in Ihrer Staging-Umgebung und lassen Sie sie dann von Ihrem CSE in der Produktion bereitstellen.
1. Übertragen Sie die Dateien in das **Git-Repository**.

1. Führen Sie eine Bereitstellung über Cloud Manager durch.

>[!NOTE]
>
>Die Migration der Dispatcher- und Webserver-Konfigurationen in das **Git-Repository** kann beim Cloud Manager-Onboarding, aber auch zu einem späteren Zeitpunkt durchgeführt werden.

### Beispiel {#example}

Die spezifische Datei- und Verzeichnisstruktur kann abhängig von den spezifischen Vorgaben Ihres Projekts variieren. Dieses Beispiel soll jedoch als konkrete Anleitung für die Strukturierung Ihres Projekts und die Einbeziehung der Apache- und Dispatcher-Konfigurationen dienen.

1. Erstellen Sie ein Unterverzeichnis mit dem Namen `dispatcher`.

   >[!NOTE]
   Sie können hier beliebige Namen verwenden, aber der in diesem Schritt erstellte Verzeichnisname muss mit dem in Schritt 6 verwendeten Namen übereinstimmen.

1. Dieses Unterverzeichnis enthält ein Maven-Modul, das die Dispatcher-ZIP-Datei mit dem Maven-Assembly-Plugin erstellt. Erstellen Sie hierzu zunächst im Verzeichnis `dispatcher` eine Datei `pom.xml` mit diesem Inhalt, indem Sie den übergeordneten Verweis, die artifactId und den Namen nach Bedarf ändern.

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

   >[!NOTE]
   Wie in Schritt 1 können Sie hier für die artifactId und den Namen beliebige Werte verwenden. `dispatcher` dient hier nur zur Vereinfachung als Beispiel.

1. Für das Maven-Assembly-Plug-in ist ein *Deskriptor* erforderlich, mit dem definiert wird, wie die ZIP-Datei erstellt wird. Erstellen Sie zum Erstellen dieses Deskriptors eine Datei (erneut im Unterverzeichnis `dispatcher`) mit dem Namen `assembly.xml`, die diesen Inhalt enthält. Beachten Sie, dass in der Datei `pom.xml` oben in Zeile 26 auf diesen Dateinamen verwiesen wird.

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

1. Erstellen Sie jetzt ein Unterverzeichnis mit dem Namen `src` (wie im Assemblierungsdeskriptor oben in Zeile 11) innerhalb des Dispatcher-Unterverzeichnisses, um die tatsächlichen Apache- und Dispatcher-Konfigurationen zu speichern. Erstellen Sie in diesem Verzeichnis `src` weitere Verzeichnisse mit den Namen `conf`, `conf.d`, `conf.dispatcher.d` und `conf.modules.d`.
1. Jetzt können Sie die Verzeichnisse `conf`, `conf.d`, `conf.dispatcher.d` und `conf.modules.d` mit Ihren Konfigurationsdateien füllen. Die Standardkonfiguration besteht beispielsweise aus diesen Dateien und symbolischen Links.

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

1. Fügen Sie abschließend die Datei „pom.xml“ in das Stammverzeichnis Ihres Projekts ein und fügen Sie das Element `<module>` hinzu, um das Dispatcher-Modul einzuschließen.

   Wenn Ihre vorhandene Modulliste beispielsweise wie folgt aussieht:

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
       </modules>
   ```

   Sollten Sie diese ändern in:

   ```xml
       <modules>
           <module>core</module>
           <module>ui.apps</module>
           <module>ui.content</module>
           <module>dispatcher</module>
       </modules>
   ```

   >[!NOTE]
   Wie in Schritt 1 erwähnt, **muss** der Wert des Elements `<module>` mit dem erstellten Verzeichnisnamen übereinstimmen.

1. Führen Sie abschließend das Paket „mvn clean“ im Projektstammverzeichnis aus. In der Ausgabe sollten Zeilen wie die folgende angezeigt werden.

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

