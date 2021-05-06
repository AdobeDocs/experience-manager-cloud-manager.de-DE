---
title: Versionshinweise für 2021.2.0
seo-title: Versionshinweise für AEM Cloud Manager 2021.2.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.2.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2021.2.0.
translation-type: tm+mt
source-git-commit: b5233e1932888b515d8dc26a6493cbd26686bc3c
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 24%

---

# Versionshinweise für 2021.2.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2021.2.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.2.0 wurde am 11. Februar 2021 veröffentlicht.

## Neue Funktionen {#whats-new}

* Der AEM Projektarchiv, der in Project und Sandbox Creation verwendet wird, wurde auf Version 25 aktualisiert.

* Die Liste veralteter APIs, die während der Codeprüfung identifiziert wurden, wurde optimiert und enthält nun weitere Klassen und Methoden, die in den neuesten Cloud Service SDK-Versionen nicht mehr unterstützt werden.

* Produktionsimplementierungen werden jetzt parallel für die paarweise Instanz im Veröffentlichungs- und Dispatcher bereitgestellt.

* SonarQube-Profil für Cloud Manager wurde aktualisiert, um die Sonar-Regel `squid:S2142` zu entfernen. Dies steht nicht mehr im Konflikt mit den Thread-Unterbrechungsüberprüfungen.

* Eigenschaften, die in benutzerdefinierten Dateien mit dem Präfix &quot;sonar&quot;festgelegt wurden, werden nun dynamisch entfernt, um Fehler beim Erstellen und Überprüfen von Qualität zu vermeiden.`pom.xml`

* Es wurden zusätzliche Regeln zur Codequalität hinzugefügt, um Probleme mit der Kompatibilität von Cloud Services zu behandeln.

## Fehlerbehebungen {#bug-fixes}

* Gelegentlich schlug die CI/CD-Pipeline (Bereitstellung) während eines Leistungstests fehl, da ein Container beim Ausführen des Lasttests einen Fehler aufwies.

* Gelegentlich meldet der Container für Lastentests die Ausführung als fehlgeschlagen, selbst wenn nur eine Ausnahme auftritt. Der Fehler wird nur gemeldet, wenn der Testprozess nicht wiederhergestellt werden kann.

* Bestimmte Groß- und Kleinschreibung-Diskrepanzen zwischen der Art und Weise, wie Umgebung gespeichert wurden, führen zu Leistungstestfehlern.

* Einige Pipeline-Fehler wurden fälschlicherweise als Pipeline-Fehler gemeldet.