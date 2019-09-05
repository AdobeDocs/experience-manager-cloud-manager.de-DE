---
title: Konfigurieren von Release-Verzweigungen
seo-title: Konfigurieren von Release-Verzweigungen
description: Konfigurieren von Release-Verzweigungen in Git für AEM Cloud Manager
seo-description: Auf dieser Seite erfahren Sie, wie Sie Release-Verzweigungen in Git konfigurieren.
uuid: d12a8b85-b7fd-4b55-a05a-a0f874ce598c
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: Erste Schritte
discoiquuid: 53807ea6-9464-429d-9322-85c9f405dff6
translation-type: ht
source-git-commit: 9c0df236c1e800802d62dea09996bb8e1e7033f7

---


# Konfigurieren von Release-Verzweigungen {#configure-your-release-branches}

## Einrichten der ersten Verzweigung in Git {#setting-up-your-first-branch-in-git}

Für jedes Programm, das erstmals in Cloud Manager hinzugefügt wird, wird in Cloud Manager ein einziges, zunächst leeres **Git-Repository** bereitgestellt. Dieses Repository kann im Verlauf des Entwicklungsprozesses beliebig viele (oder wenige) Verzweigungen enthalten. Es muss jedoch mindestens eine Verzweigung vorhanden sein, die von der CI-/CD-Pipeline verwendet wird, um Anwendungscode für die Staging- und Produktionsumgebung bereitzustellen. Als Best Practice gilt, für diese Verzweigung den Namen `master` zu verwenden. Praktischerweise ist dies die standardmäßige Verhaltensweise von Git-Clients beim Einrichten neuer Projekte.

Wenn Sie ein neues Projekt einrichten, führen Sie eine Reihe von Befehlen aus, zum Beispiel:

```shell
$ git init
Initialized empty Git repository in /Users/myname/workspace/new-project/.git/
... steps which add Maven build files and source code ...
$ git add pom.xml core/pom.xml core/src ui.apps/pom.xml ui.apps/src
$ git commit -m "initial commit"
 19 files changed, 777 insertions(+)
 create mode 100644 core/pom.xml
 create mode 100644 pom.xml
 create mode 100644 ui.apps/pom.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/config.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/definition/.content.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/filter.xml
 create mode 100644 ui.apps/src/main/content/META-INF/vault/nodetypes.cnd
 create mode 100644 ui.apps/src/main/content/META-INF/vault/properties.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/apps/my-aem-project/install/.vltignore
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/policies/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/template-types/_rep_policy.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/.content.xml
 create mode 100644 ui.apps/src/main/content/jcr_root/conf/my-aem-project/settings/wcm/templates/_rep_policy.xml
```

>[!NOTE]
>
>Sie müssen keinen Befehlszeilen-Client verwenden. Es gibt eine Vielzahl grafischer Git-Clients, die als eigenständige Anwendungen oder als Teil einer integrierten Entwicklungsumgebung (z. B. Eclipse oder IntelliJ) verfügbar sind. Sofern die Client-Anwendung das Git mit HTTPS unterstützt, sollte sie mit [!UICONTROL Cloud Manager kompatibel] sein.

## Push-Veröffentlichung der ersten Verzweigung {#pushing-your-first-branch}

Sobald Sie mindestens eine Revision eingereicht haben, können Sie das [!UICONTROL Cloud Manager]-Repository als **Remote**-Datenquelle hinzufügen und dann Ihre Commits dorthin senden:

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      master -> master
```

>[!NOTE]
>
>Sie erhalten die spezifische URL (zusammen mit Ihren Anmeldeinformationen) beim [!UICONTROL Cloud Manager]-Onboarding von Ihrem Customer Success Engineering.

## Zusätzliche Verzweigungen {#additional-branches}

Eine einzelne `master`-Verzweigung kann für sehr einfache Projekte ausreichend sein. In den meisten Fällen ist jedoch eine komplexere Verzweigungsstrategie erforderlich. Viele Kunden gehen wie folgt vor: Die täglichen Entwicklungsaktivitäten werden an einer Verzweigung mit dem Namen `develop` durchgeführt und diese Entwicklungsverzweigung wird für die Bereitstellung mit der Verzweigung `master` zusammengeführt.

>[!NOTE]
>
>Die gebräuchlichen GitBefehle finden Sie im [Git Cheat Sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
