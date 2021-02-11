---
title: Versionshinweise für 2021.2.0
seo-title: Versionshinweise für AEM Cloud Manager 2021.2.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.2.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2021.2.0.
translation-type: tm+mt
source-git-commit: 67cdd39cb511763a42391c7896924a1433e4e58f
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 25%

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

* Eigenschaften, die in benutzerdefinierten `pom.xml`-Dateien mit dem Präfix Sonar festgelegt wurden, werden jetzt dynamisch entfernt, um Fehler beim Erstellen und Überprüfen von Qualität zu vermeiden.

## Fehlerbehebungen {#bug-fixes}

* Gelegentlich schlug die CI/CD-Pipeline (Bereitstellung) während eines Leistungstests fehl, da ein Container beim Ausführen des Lasttests einen Fehler aufwies.

* Gelegentlich meldet der Container für Lastentests die Ausführung als fehlgeschlagen, selbst wenn nur eine Ausnahme auftritt. Der Fehler wird nur gemeldet, wenn der Testprozess nicht wiederhergestellt werden kann.

* Bestimmte Groß- und Kleinschreibung-Diskrepanzen zwischen der Art und Weise, wie Umgebung gespeichert wurden, führen zu Leistungstestfehlern.

* Einige Pipeline-Fehler wurden fälschlicherweise als Pipeline-Fehler gemeldet.