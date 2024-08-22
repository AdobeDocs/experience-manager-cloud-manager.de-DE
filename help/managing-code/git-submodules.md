---
title: Unterstützung von Git-Untermodulen
description: Erfahren Sie, wie Sie mit Git-Untermodulen den Inhalt mehrerer Verzweigungen zum Zeitpunkt der Erstellung über Git-Repositorys hinweg zusammenführen können.
exl-id: f946d7e7-114a-4e33-bb82-2625d37bba2f
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 20%

---

# Git-Untermodulunterstützung für Adobe-Repositorys {#git-submodule-support}

Git-Untermodule können verwendet werden, um den Inhalt mehrerer Verzweigungen zum Zeitpunkt der Erstellung über Git-Repositorys hinweg zusammenzuführen.

Wenn der Build-Prozess von Cloud Manager ausgeführt wird, klont er zunächst das Repository der Pipeline und checkt die konfigurierte Verzweigung aus. Wenn die Verzweigung eine `.gitmodules` -Datei im Stammverzeichnis enthält, wird der Befehl ausgeführt.

```
$ git submodule update --init
```

Dieser Prozess checkt jedes Untermodul in das entsprechende Verzeichnis aus. Diese Technik ist eine potenzielle Alternative zu [Arbeiten mit mehreren Quell-Git-Repositorys](/help/managing-code/multiple-git-repos.md) für Unternehmen, die mit Git-Untermodulen vertraut sind und keinen externen Zusammenführungsprozess verwalten möchten.

Angenommen, es gibt drei Repositorys, die jeweils eine einzige Verzweigung mit dem Namen `main` enthalten. Im &quot;primären&quot;Repository, d. h. dem in den Pipelines konfigurierten, verfügt die `main` -Verzweigung über eine `pom.xml` -Datei, die die in den anderen beiden Repositorys enthaltenen Projekte deklariert:

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

* Die Git-URL muss sich genau in der oben beschriebenen Syntax befinden.
* Betten Sie aus Sicherheitsgründen keine Anmeldeinformationen in diese URLs ein.
* Es werden nur Untermodule im Stammverzeichnis der Verzweigung unterstützt.
* Git-Untermodulverweise werden für bestimmte Git-Commits gespeichert. Wenn also Änderungen am Submodul-Repository vorgenommen werden, muss der referenzierte Commit aktualisiert werden. Verwenden Sie beispielsweise &quot;`git submodule update --remote`&quot;.
* Sofern nicht anders erforderlich, empfiehlt Adobe, &quot;flache&quot;Untermodule zu verwenden, indem Sie für jedes Untermodul `git config -f .gitmodules submodule.<submodule path>.shallow true` ausführen.


## Git-Untermodulunterstützung für private Repositorys {#private-repositories}

Die Unterstützung für Git-Untermodule bei Verwendung von [privaten Repositorys](private-repositories.md) ist weitgehend identisch mit der Verwendung von Adobe-Repositorys.

Nachdem Sie Ihre Datei `pom.xml` eingerichtet haben und die `git submodule`-Befehle ausgeführt werden, müssen Sie jedoch eine `.gitmodules`-Datei zum Stammverzeichnis des Aggregator-Repositorys hinzufügen, damit Cloud Manager die Einrichtung des Untermoduls erkennt.

![.gitmodules-Datei](assets/gitmodules.png)

![Aggregator](assets/aggregator.png)

### Einschränkungen und Empfehlungen {#limitations-recommendations-private-repos}

Beachten Sie bei der Verwendung von Git-Untermodulen mit privaten Repositorys die folgenden Einschränkungen.

* Die Git-URLs für die Untermodule können entweder im HTTPS- oder im SSH-Format vorliegen, müssen jedoch mit einem Github.com-Repository verknüpft werden. Das Hinzufügen eines Adobe-Repository-Untermoduls zu einem GitHub-Aggregator-Repository oder umgekehrt funktioniert nicht.
* Die GitHub-Untermodule müssen für die Adobe-GitHub-App zugänglich sein.
* [Die Einschränkungen bei der Verwendung von Git-Untermodulen mit von Adobe verwalteten Repositorys](#limitations-recommendations) gelten ebenfalls.
