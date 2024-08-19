---
title: Konfigurieren von Verzweigungen
description: Erfahren Sie, wie Sie Ihre erste Verzweigung in Git einrichten und wie sie von der CI/CD-Pipeline zum Bereitstellen Ihres Anwendungs-Codes verwendet wird.
exl-id: ff2ae28f-902e-4fb2-aeb1-3636cb5cd9bb
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 14%

---


# Verzweigungen konfigurieren {#configuring-branches}

Erfahren Sie, wie Sie Ihre erste Verzweigung in Git einrichten und wie sie von der CI/CD-Pipeline zum Bereitstellen Ihres Anwendungs-Codes verwendet wird.

## Einrichten der ersten Verzweigung in Git {#setting-up-your-first-branch-in-git}

Ein einziges, zunächst leeres Git-Repository wird für jedes Programm [bereitgestellt](/help/requirements/environment-provisioning.md), das in Cloud Manager eingebunden ist. Dieses Repository kann so viele Verzweigungen enthalten, wie Ihr Entwicklungsprozess erfordert. Es muss jedoch mindestens eine Verzweigung vorhanden sein, die von der CI/CD-Pipeline verwendet wird, um Anwendungscode für die Staging- und Produktionsumgebung bereitzustellen. Als Best Practice gilt, für diese Verzweigung den Namen `main` zu verwenden. Praktisch ist dieser Ansatz das Standardverhalten von Git-Clients beim Einrichten neuer Projekte.

Wenn Sie beispielsweise ein neues Projekt einrichten, führen Sie eine Reihe von Befehlen ähnlich der folgenden aus.

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
>Es ist nicht erforderlich, den Befehlszeilen-Client zu verwenden. Es gibt eine Vielzahl grafischer Git-Clients, die entweder als eigenständige Anwendungen oder als Teil einer integrierten Entwicklungsumgebung (IDE) wie Eclipse oder IntelliJ verfügbar sind. Sofern das Client-Programm das Git mit HTTPS unterstützt, sollte es mit [!UICONTROL Cloud Manager] kompatibel sein.

## Den ersten Zweig verschieben {#pushing-your-first-branch}

Wenn Sie mindestens eine Revision vorgenommen haben, können Sie das [!UICONTROL Cloud Manager]-Repository als Remote-Repository hinzufügen und dann Ihre Commits dorthin senden.

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
>Die spezifische URL wird zusammen mit Ihren Anmeldeinformationen vom Adobe CSE (Customer Success Engineer) beim Einstieg in [!UICONTROL Cloud Manager] bereitgestellt.

## Zusätzliche Zweige {#additional-branches}

Eine einzelne `main` -Verzweigung kann für sehr einfache Projekte ausreichen, aber in den meisten Fällen ist eine komplexere Verzweigungsstrategie erforderlich. Viele Kunden führen einen Prozess durch, bei dem tägliche Entwicklungsaktivitäten in einer Verzweigung mit dem Namen `develop` ausgeführt werden. Die Entwicklungsverzweigung wird dann in der `main`-Verzweigung zusammengeführt, wenn es Zeit für eine Bereitstellung ist.

>[!TIP]
>
>Allgemeine Git-Befehle finden Sie im [Git Cheat Sheet](https://training.github.com/downloads/github-git-cheat-sheet).
