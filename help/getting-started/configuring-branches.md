---
title: Konfigurieren von Verzweigungen
description: Erfahren Sie, wie Sie Ihre erste Verzweigung in Git einrichten und wie sie von der CI/CD-Pipeline zum Bereitstellen des Programm-Codes verwendet wird.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 4c051cd1696f8a00d0278131c9521ad4dcb956a3
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 100%

---


# Konfigurieren von Verzweigungen {#configuring-branches}

Erfahren Sie, wie Sie Ihre erste Verzweigung in Git einrichten und wie sie von der CI/CD-Pipeline zum Bereitstellen des Programm-Codes verwendet wird.

## Einrichten der ersten Verzweigung in Git {#setting-up-your-first-branch-in-git}

Ein einziges, zunächst leeres Git-Repository wird für jedes Programm [bereitgestellt](/help/requirements/environment-provisioning.md), das in Cloud Manager eingebunden ist. Dieses Repository kann so viele Verzweigungen enthalten, wie es der Entwicklungsprozesses erfordert. Es muss jedoch mindestens eine Verzweigung vorhanden sein, die von der CI/CD-Pipeline verwendet wird, um Programm-Code für die Staging- und Produktionsumgebung bereitzustellen. Als Best Practice gilt, für diese Verzweigung den Namen `main` zu verwenden. Praktischerweise ist dies die standardmäßige Verhaltensweise von Git-Clients beim Einrichten neuer Projekte.

Wenn Sie beispielsweise ein neues Projekt einrichten, führen Sie eine Reihe von Befehlen aus, die den folgenden ähnlich sind:

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
>Sie müssen keinen Befehlszeilen-Client verwenden. Es gibt eine Vielzahl grafischer Git-Clients, die als eigenständige Programme oder als Teil einer integrierten Entwicklungsumgebung (IDE), wie z. B. Eclipse oder IntelliJ, verfügbar sind. Sofern das Client-Programm das Git mit HTTPS unterstützt, sollte es mit [!UICONTROL Cloud Manager] kompatibel sein.

## Push-Veröffentlichung der ersten Verzweigung {#pushing-your-first-branch}

Sobald Sie sich für mindestens eine Revision entschieden haben, können Sie das [!UICONTROL Cloud Manager]-Repository als Remote-Datenquelle hinzufügen und dann Ihre Commits dorthin senden.

```shell
$ git remote add adobe <url>
$ git push adobe master
Counting objects: 36, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (27/27), done.
Writing objects: 100% (36/36), 7.31 KiB | 1.83 MiB/s, done.
Total 36 (delta 6), reused 0 (delta 0)
To <url>
 * [new branch]      main -> main
```

>[!NOTE]
>
>Sie erhalten die spezifische URL (zusammen mit Ihren Anmeldeinformationen) beim [!UICONTROL Cloud Manager]-Onboarding von Ihrem Customer Success Engineering.

## Zusätzliche Verzweigungen {#additional-branches}

Eine einzelne `main`-Verzweigung kann für sehr einfache Projekte ausreichend sein. In den meisten Fällen ist jedoch eine komplexere Verzweigungsstrategie erforderlich. Viele Kunden gehen wie folgt vor: Die täglichen Entwicklungsaktivitäten werden an einer Verzweigung mit dem Namen `develop` durchgeführt und diese Entwicklungsverzweigung wird für die Bereitstellung mit der Verzweigung `main` zusammengeführt.

>[!TIP]
>
>Die gebräuchlichen Git-Befehle finden Sie in der [Git-Schnellübersicht](https://github.github.com/training-kit/downloads/github-git-cheat-sheet).
