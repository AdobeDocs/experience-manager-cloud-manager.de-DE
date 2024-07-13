---
title: Unterstützung von Git-Untermodulen
description: Erfahren Sie, wie Sie Git-Untermodule dazu verwenden können, den Inhalt mehrerer Verzweigungen zum Build-Zeitpunkt über Git-Repositorys hinweg zusammenzuführen.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: e93285f7c7495ec9d2f11d289adaf6aaba7e58ea
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 100%

---

# Unterstützung von Git-Untermodulen für Adobe-Repositorys {#git-submodule-support}

Git-Untermodule können verwendet werden, um den Inhalt mehrerer Verzweigungen zum Build-Zeitpunkt über Git-Repositorys hinweg zusammenzuführen.

Wenn der Build-Prozess von Cloud Manager ausgeführt wird, nachdem das für die Pipeline konfigurierte Repository geklont und die konfigurierte Verzweigung ausgecheckt wurde, wird der Befehl ausgeführt, sofern die Verzweigung eine `.gitmodules`-Datei im Stammverzeichnis enthält.

```
$ git submodule update --init
```

Dadurch wird jedes Untermodul in das entsprechende Verzeichnis eingecheckt. Diese Technik ist eine potenzielle Alternative zur [Arbeit mit mehreren Quell-Git-Repositorys](/help/managing-code/multiple-git-repos.md) für Organisationen, die mit der Verwendung von Git-Untermodulen vertraut sind und keinen externen Zusammenführungsprozess verwalten möchten.

Angenommen, es gibt drei Repositorys, die jeweils eine einzige Verzweigung mit dem Namen `main` enthalten. Im „primären“ Repository, d. h. dem in den Pipelines konfigurierten, verfügt die Verzweigung `main` über eine `pom.xml`-Datei, in der die in den beiden anderen Repositorys enthaltenen Projekte deklariert werden:

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

## Beschränkungen {#limitations}

Beachten Sie bei der Verwendung von Git-Untermodulen Folgendes:

* Die Git-URL muss sich genau an die oben beschriebene Syntax halten.
* Betten Sie aus Sicherheitsgründen keine Anmeldeinformationen in diese URLs ein.
* Es werden nur Untermodule im Stammverzeichnis der Verzweigung unterstützt.
* Für bestimmte Git-Commits werden Git-Untermodulverweise gespeichert.
   * Wenn also Änderungen am Untermodul-Repository vorgenommen werden, muss der referenzierte Commit aktualisiert werden, z. B. mithilfe von `git submodule update --remote`.
* Sofern nicht anders erforderlich, wird dringend empfohlen, „flache“ Untermodule zu verwenden.
   * Führen Sie dazu `git config -f .gitmodules submodule.<submodule path>.shallow true` für jedes Untermodul aus.


## Unterstützung von Git-Untermodulen für private Repositorys {#private-repositories}

Die Unterstützung für Git-Untermodule bei Verwendung von [privaten Repositorys](private-repositories.md) ist weitgehend dieselbe wie bei Verwendung von Adobe-Repositorys.

Nachdem Sie Ihre Datei `pom.xml` eingerichtet haben und die `git submodule`-Befehle ausgeführt werden, müssen Sie jedoch eine `.gitmodules`-Datei zum Stammverzeichnis des Aggregator-Repositorys hinzufügen, damit Cloud Manager die Einrichtung des Untermoduls erkennt.

![.gitmodules-Datei](assets/gitmodules.png)

![Aggregator](assets/aggregator.png)

### Einschränkungen und Empfehlungen {#limitations-recommendations-private-repos}

Beachten Sie bei der Verwendung von Git-Untermodulen mit privaten Repositorys die folgenden Einschränkungen.

* Die Git-URLs für die Untermodule können entweder im HTTPS- oder im SSH-Format vorliegen, müssen jedoch mit einem github.com-Repository verknüpft sein
   * Das Hinzufügen eines Adobe-Repository-Untermoduls zu einem GitHub-Aggregator-Repository oder umgekehrt funktioniert nicht.
* Die GitHub-Untermodule müssen für die Adobe-GitHub-App zugänglich sein.
* [Die Einschränkungen bei der Verwendung von Git-Untermodulen mit von Adobe verwalteten Repositorys](#limitations-recommendations) gelten ebenfalls.
