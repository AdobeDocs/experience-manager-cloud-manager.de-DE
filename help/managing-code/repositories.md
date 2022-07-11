---
title: Cloud Manager-Repositorys
description: Erfahren Sie, wie Sie Repositorys für Ihre Cloud Manager-Programme aufrufen, erstellen und bearbeiten können.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 49%

---


# Cloud Manager-Repositorys {#cloud-manager-repos}

In Repositorys verwalten Sie Ihren Code mithilfe von Git. Erfahren Sie, wie Sie Repositorys für Ihre Cloud Manager-Programme erstellen.

## Zugriff auf Repositorys {#accessing-repos}

Sie können über Cloud Manager in einem Self-Service auf Ihre Git-Repositorys zugreifen und diese verwalten.

Um auf Ihr Repository zuzugreifen, verwenden Sie die **Zugriff auf Repo Info** in Cloud Manager verfügbar ist, insbesondere auf der Pipeline-Karte.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** und Sie sehen die **Zugriff auf Repo Info** -Option zum Zugreifen auf und Verwalten Ihres Git-Repositorys [mit dieser Pipeline konfiguriert.](/help/using/production-pipelines.md)

   ![Schaltfläche &quot;Repo Info aufrufen&quot;](/help/assets/access-repo1.png)

1. Wenn Sie zum **Nicht Produktion** Pipeline-Registerkarte, die **Zugriff auf Repo Info** ist auch dort verfügbar als [für die Pipeline konfiguriert.](/help/using/non-production-pipelines.md)

   ![Produktionsfremde Pipelines](/help/assets/access-repo-nonprod.png)

1. Klicken Sie auf **Zugriff auf Repo Info** Schaltfläche zum Öffnen eines Dialogfelds, das Folgendes enthält:

   * Die URL zum Git-Repository
   * Benutzername
   * Passwort
   * Git-Befehl zum lokalen Klonen des Repositorys ausführen

   ![Dialogfeld &quot;Repository-Informationen&quot;](/help/assets/access-repo-create.png)

Verwenden Sie die bereitgestellten Informationen, um das Repository lokal zu klonen, damit Sie mit der lokalen Entwicklung beginnen können.

>[!NOTE]
>
>Die Option **Auf Repository-Informationen zugreifen** ist für Benutzer mit den Rollen „Entwickler“ und „Implementierungs-Manager“ sichtbar.********

## Hinzufügen von Repositorys {#add-repos}

Führen Sie die folgenden Schritte aus, um Repositorys in Cloud Manager hinzuzufügen:

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Repositorys** und gehen Sie zur Seite **Repositorys**.

1. Klicken Sie auf **Repository hinzufügen**, um den Assistenten zu starten.

   >[!NOTE]
   >
   >Sie müssen über die **Bereitstellungsmanager** oder **Business Owner** Rolle zum Hinzufügen eines Repositorys.

   ![Repository hinzufügen](/help/assets/create-repo2.png)

1. Geben Sie den Namen und die Beschreibung wie verlangt ein, und klicken Sie auf **Speichern**.

   ![Details des Repo](/help/assets/repo-1.png)

1. Wählen Sie **Speichern** aus.

Ihr neu erstelltes Repo wird angezeigt.

![Neues Repo erstellt](/help/assets/create-repo3.png)

In Cloud Manager erstellte Repositorys stehen zur Auswahl zur Verfügung, wenn Sie [Pipelines erstellen.](/help/overview/ci-cd-pipelines.md)

## Anzeigen und Bearbeiten von Repositorys {#edit-repos}

Führen Sie die folgenden Schritte aus, um Repositorys in Cloud Manager zu bearbeiten und anzuzeigen:

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Repositorys** und gehen Sie zur Seite **Repositorys.** Hier können Sie die Details Ihrer vorhandenen Repositorys anzeigen.

1. Wählen Sie das Repository aus und klicken Sie auf die Suchschaltfläche ganz rechts in der Tabelle, um **Repository-URL kopieren**, **Anzeigen und Aktualisieren** oder **Löschen** Ihr Repository.

![Repo bearbeiten](/help/assets/create-repo3.png)

## Unterstützung von Git-Untermodulen {#git-submodule-support}

Git-Untermodule können verwendet werden, um den Inhalt mehrerer Verzweigungen zum Build-Zeitpunkt über Git-Repositorys hinweg zusammenzuführen.

Wenn der Build-Prozess von Cloud Manager ausgeführt wird, nachdem das für die Pipeline konfigurierte Repository geklont und die konfigurierte Verzweigung ausgecheckt wurde, wird der Befehl ausgeführt, sofern die Verzweigung eine `.gitmodules`-Datei im Stammverzeichnis enthält.

```
$ git submodule update --init
```

Dadurch wird jedes Untermodul in das entsprechende Verzeichnis eingecheckt. Diese Technik ist eine potenzielle Alternative zur [Arbeit mit mehreren Quell-Git-Repositorys](/help/managing-code/multiple-git-repos.md) für Organisationen, die mit der Verwendung von Git-Untermodulen vertraut sind und keinen externen Zusammenführungsprozess verwalten möchten.

Angenommen, es gibt drei Repositorys, die jeweils eine einzelne Verzweigung mit dem Namen `main`. Im &quot;primären&quot;Repository, d. h. dem in den Pipelines konfigurierten, wird die `main` Verzweigung hat `pom.xml` Datei, in der die in den beiden anderen Repositorys enthaltenen Projekte deklariert werden:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
   
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
   
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
   
</project>
```

Anschließend fügen Sie Untermodule für die beiden anderen Repositorys hinzu:

```shell
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectA/ project-a
$ git submodule add -b main https://git.cloudmanager.adobe.com/ProgramName/projectB/ project-b
```

Dies führt zu einer `.gitmodules`-Datei, die wie folgt aussieht:

```text
[submodule "project-a"]
    path = project-a
    url = https://git.cloudmanager.adobe.com/ProgramName/projectA/
    branch = main
[submodule "project-b"]
    path = project-b
    url = https://git.cloudmanager.adobe.com/ProgramName/projectB/
    branch = main
```

Weitere Informationen zu Git-Untermodulen finden Sie im [Git-Referenzhandbuch](https://git-scm.com/book/de/v2/Git-Tools-Submodules).

### Beschränkungen {#limitations}

Beachten Sie bei der Verwendung von Git-Untermodulen Folgendes:

* Die Git-URL muss sich genau in der oben beschriebenen Syntax befinden.
* Betten Sie aus Sicherheitsgründen keine Anmeldeinformationen in diese URLs ein.
* Es werden nur Untermodule im Stammverzeichnis der Verzweigung unterstützt.
* Für bestimmte Git-Commits werden Git-Untermodulverweise gespeichert.
   * Wenn also Änderungen am Untermodul-Repository vorgenommen werden, muss der referenzierte Commit aktualisiert werden, z. B. mithilfe von `git submodule update --remote`.
* Sofern nicht anders erforderlich, wird dringend empfohlen, „flache“ Untermodule zu verwenden.
   * Führen Sie dazu `git config -f .gitmodules submodule.<submodule path>.shallow true` für jedes Untermodul aus.
