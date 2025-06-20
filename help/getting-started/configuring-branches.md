---
title: Konfigurieren von Verzweigungen
description: Erfahren Sie, wie Sie Ihre erste Verzweigung in Git einrichten und wie sie von der CI/CD-Pipeline zum Bereitstellen des Anwendungs-Codes verwendet wird.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 95%

---


# Konfigurieren von Verzweigungen {#configuring-branches}

Erfahren Sie, wie Sie Ihre erste Verzweigung in Git einrichten und wie sie von der CI/CD-Pipeline zum Bereitstellen des Anwendungs-Codes verwendet wird.

## Einrichten der ersten Verzweigung in Git {#setting-up-your-first-branch-in-git}

Ein einziges, zunächst leeres Git-Repository wird für jedes in Cloud Manager eingebundene Programm [bereitgestellt](/help/requirements/environment-provisioning.md). Dieses Repository kann so viele Verzweigungen enthalten, wie es der Entwicklungsprozess erfordert. Es muss jedoch mindestens eine Verzweigung vorhanden sein, die von der CI/CD-Pipeline verwendet wird, um Anwendungs-Code für die Staging- und Produktionsumgebung bereitzustellen. Als Best Practice gilt, für diese Verzweigung den Namen `main` zu verwenden. Praktischerweise entspricht dieser Ansatz der standardmäßigen Verhaltensweise von Git-Clients beim Einrichten neuer Projekte.

Wenn Sie beispielsweise ein neues Projekt einrichten, führen Sie eine Reihe von Befehlen wie den folgenden aus:

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
>Sie müssen keinen Befehlszeilen-Client verwenden. Es gibt eine Vielzahl grafischer Git-Clients, die als eigenständige Anwendungen oder als Teil einer integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) wie Eclipse oder IntelliJ verfügbar sind. Sofern die Client-Anwendung das Git mit HTTPS unterstützt, sollte es mit [!UICONTROL Cloud Manager] kompatibel sein.

## Push-Übertragung der ersten Verzweigung {#pushing-your-first-branch}

Wenn Sie sich für mindestens eine Version entschieden haben, können Sie das [!UICONTROL Cloud Manager]-Repository als Remote-Datenquelle hinzufügen und dann Ihre Commits dorthin senden.

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
>Sie erhalten die spezifische URL (zusammen mit Ihren Anmeldedaten) beim [!UICONTROL Cloud Manager]-Onboarding vom Customer Success Engineer(CSE)-Team.

## Zusätzliche Verzweigungen {#additional-branches}

Eine einzelne `main`-Verzweigung kann für sehr einfache Projekte ausreichend sein. In den meisten Fällen ist jedoch eine komplexere Verzweigungsstrategie erforderlich. Viele Kundinnen und Kunden folgen einem Prozess, bei dem tägliche Entwicklungsaktivitäten in einer Verzweigung mit dem Namen `develop` durchgeführt werden. Die `develop` Verzweigung wird dann mit der `main` zusammengeführt, wenn es Zeit für eine Bereitstellung ist.

>[!TIP]
>
>Gebräuchliche Git-Befehle finden Sie auf dem [Git-Spickzettel](https://training.github.com/downloads/github-git-cheat-sheet).
