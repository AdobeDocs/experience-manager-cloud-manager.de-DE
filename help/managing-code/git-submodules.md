---
title: Unterstützung von Git-Untermodulen
description: Erfahren Sie, wie Sie Git-Untermodule dazu verwenden können, den Inhalt mehrerer Verzweigungen zum Build-Zeitpunkt über Git-Repositorys hinweg zusammenzuführen.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
TQID: https://experienceleague.adobe.com/W9-oYHPdxHPJgwKxguEEkRgf3JDo8iHQRnnsSPYbHCI
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: c2a6d2f87cf9f9c98f2af818f73b1fb2793c2e46
workflow-type: tm+mt
source-wordcount: 420
ht-degree: 82%

---

# Unterstützung von Git-Untermodulen für Adobe-Repositorys {#git-submodule-support}

Git-Untermodule können verwendet werden, um zum Build-Zeitpunkt den Inhalt mehrerer Verzweigungen über Git-Repositorys hinweg zusammenzuführen.

Wenn der Build-Prozess von Cloud Manager ausgeführt wird, klont er zunächst das Repository der Pipeline und prüft dann die konfigurierte Verzweigung. Wenn die Verzweigung eine `.gitmodules` im Stammverzeichnis enthält, wird der Befehl ausgeführt.

```
$ git submodule update --init
```

Dadurch wird jedes Untermodul im entsprechenden Verzeichnis geprüft. Diese Technik ist eine potenzielle Alternative zur [Arbeit mit mehreren Quell-Git-Repositorys](/help/managing-code/multiple-git-repos.md) für Organisationen, die mit der Verwendung von Git-Untermodulen vertraut sind und keinen externen Zusammenführungsprozess verwalten möchten.

Angenommen, es gibt drei Repositorys, die jeweils eine einzige Verzweigung mit dem Namen `main` enthalten. Im „primären“ Repository, d. h. dem in den Pipelines konfigurierten, verfügt die Verzweigung `main` über eine Datei `pom.xml`, in der die in den beiden anderen Repositorys enthaltenen Projekte deklariert werden.

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

Die Ergebnisse in der Datei `.gitmodules` sehen wie folgt aus:

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

Weitere Informationen zu Git-Untermodulen finden Sie im [Git-Referenzhandbuch](https://git-scm.com/book/de/v2/Git-Tools-Submodules) .

## Einschränkungen {#limitations}

Beachten Sie bei der Verwendung von Git-Untermodulen Folgendes:

* Die Git-URL muss sich genau an die oben beschriebene Syntax halten.
* Schließen Sie aus Sicherheitsgründen keine Anmeldeinformationen in diese URLs ein.
* Es werden nur Untermodule im Stammverzeichnis der Verzweigung unterstützt.
* Für bestimmte Git-Commits werden Git-Untermodulverweise gespeichert. Wenn also Änderungen am Untermodul-Repository vorgenommen werden, müssen Sie den referenzierten Commit aktualisieren. Zum Beispiel mit `git submodule update --remote`
* Sofern nicht anders erforderlich, empfiehlt Adobe, „flache“ Untermodule zu verwenden, indem Sie für jedes Untermodul `git config -f .gitmodules submodule.<submodule path>.shallow true` ausführen.


## Unterstützung von Git-Untermodulen für private Repositorys {#private-repositories}

Die Unterstützung für Git-Untermodule bei Verwendung von [privaten Repositorys](private-repositories.md) ist weitgehend dieselbe wie bei Verwendung von Adobe-Repositorys.

Damit Cloud Manager die Untermoduleinrichtung erkennt, müssen Sie jedoch eine `.gitmodules`-Datei zum Stammverzeichnis des Aggregator-Repositorys hinzufügen, nachdem Sie Ihre `pom.xml` eingerichtet und die `git submodule`-Befehle ausgeführt haben.

![.gitmodules-Datei](assets/gitmodules.png)

![Aggregator](assets/aggregator.png)

### Einschränkungen und Empfehlungen {#limitations-recommendations-private-repos}

Beachten Sie bei der Verwendung von Git-Untermodulen mit privaten Repositorys die folgenden Einschränkungen.

* Die Git-URLs für die Untermodule können entweder im HTTPS- oder im SSH-Format vorliegen, müssen jedoch mit einem Github.com-Repository verknüpft sein. Das Hinzufügen eines Adobe-Repository-Untermoduls zu einem GitHub-Aggregator-Repository oder umgekehrt funktioniert nicht.
* Die GitHub-Untermodule müssen für die Adobe-GitHub-App zugänglich sein.
* [Die Einschränkungen bei der Verwendung von Git-Untermodulen mit von Adobe verwalteten Repositorys](#limitations-recommendations) gelten ebenfalls.
