---
source-git-commit: 4ff440250b4ed0770c34a7042ec7d22c79ffe05e
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 0%

---
# Snippets (#snippets)

## Bekannte Probleme bei der Inhaltskopie {#content-copy-known-issues}

Beachten Sie das folgende bekannte Problem bei der Verwendung der Funktion zum Kopieren von [Inhalten.](/help/using/content-copy.md)

* Wenn eine Ressource in der Quellumgebung umbenannt wird, kann dies dazu führen, dass der Vorgang zum Kopieren des Inhalts aufgrund widersprüchlicher UUIDs in der Zielumgebung fehlschlägt.
   * Um diesen Fehler zu vermeiden, müssen Sie Ressourcen zunächst löschen und dann mit dem gewünschten neuen Ressourcennamen neu erstellen, anstatt sie umzubenennen.
