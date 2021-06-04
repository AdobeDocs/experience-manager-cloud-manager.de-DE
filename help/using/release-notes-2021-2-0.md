---
title: Versionshinweise für 2021.2.0
seo-title: Versionshinweise für AEM Cloud Manager 2021.2.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.2.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2021.2.0.
exl-id: 4f3c3a63-141b-414f-a24e-1870e985873a
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2021.2.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2021.2.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.2.0 wurde am 11. Februar 2021 veröffentlicht.

## Neuigkeiten {#whats-new}

* Der AEM-Projektarchetyp, der bei der Projekt- und Sandbox-Erstellung verwendet wird, wurde auf Version 25 aktualisiert.

* Die Liste veralteter APIs, die während der Code-Prüfung identifiziert wurden, wurde verfeinert und enthält nun weitere Klassen und Methoden, die in den neuesten Cloud Service SDK-Versionen nicht mehr unterstützt werden.

* Produktionsimplementierungen werden jetzt parallel für die paarweise Veröffentlichungs- und Dispatcher-Instanz bereitgestellt.

* SonarQube-Profil für Cloud Manager wurde aktualisiert und die Sonar-Regel `squid:S2142` entfernt. So werden Konflikte mit Thread-Unterbrechungsüberprüfungen unterbunden.

* Eigenschaften, die in `pom.xml`-Kundendateien mit dem Präfix „sonar“ festgelegt wurden, werden nun dynamisch entfernt, um Build- und Qualitätsprüfungsfehler zu vermeiden.

* Es wurden zusätzliche Code-Qualitätsregeln hinzugefügt, um Probleme mit der Kompatibilität von Cloud Services zu behandeln.

## Fehlerbehebungen {#bug-fixes}

* Gelegentlich schlug die CI/CD-Pipeline (Bereitstellung) während eines Leistungstests fehl, da ein Container beim Ausführen des Lasttests einen Fehler aufwies.

* Gelegentlich meldet der Lasttest-Container die Ausführung als fehlgeschlagen, obwohl nur eine Ausnahme auftritt. Der Fehler wird nur gemeldet, wenn der Testprozess nicht wiederhergestellt werden kann.

* Bestimmte Diskrepanzen bei der Groß- und Kleinschreibung gespeicherter Umgebungsnamen führen zu Leistungstestfehlern.

* Einige Pipeline-Fehler wurden fälschlicherweise als Pipeline-Fehler gemeldet.
