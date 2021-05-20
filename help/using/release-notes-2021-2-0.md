---
title: Versionshinweise für 2021.2.0
seo-title: Versionshinweise für AEM Cloud Manager 2021.2.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.2.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2021.2.0.
exl-id: 4f3c3a63-141b-414f-a24e-1870e985873a
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 24%

---

# Versionshinweise für 2021.2.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2021.2.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.2.0 wurde am 11. Februar 2021 veröffentlicht.

## Neue Funktionen {#whats-new}

* Der AEM Projektarchetyp, der bei der Projekt- und Sandbox-Erstellung verwendet wird, wurde auf Version 25 aktualisiert.

* Die Liste veralteter APIs, die beim Codescan identifiziert werden, wurde verfeinert und enthält jetzt zusätzliche Klassen und Methoden, die in den neuesten Cloud Service SDK-Versionen nicht mehr unterstützt werden.

* Produktionsbereitstellungen werden jetzt parallel für die paarweise Veröffentlichungs- und Dispatcher-Instanzen bereitgestellt.

* Das SonarQube-Profil für Cloud Manager wurde aktualisiert, um die Sonar-Regel `squid:S2142` zu entfernen. Dies steht nicht mehr in Konflikt mit den Prüfungen zur Thread-Unterbrechung.

* Eigenschaften, die in kundenspezifischen `pom.xml` -Dateien mit dem Präfix sonar festgelegt sind, werden jetzt dynamisch entfernt, um Fehler bei der Build- und Qualitätsprüfung zu vermeiden.

* Es wurden zusätzliche Regeln für die Codequalität hinzugefügt, um Probleme mit der Kompatibilität von Cloud Services abzudecken.

## Fehlerbehebungen {#bug-fixes}

* Gelegentlich schlug die CI/CD-Pipeline (Bereitstellung) während eines Leistungstestschritts aufgrund eines Containers, der den Belastungstest durchführte, fehl und es trat ein Fehler auf.

* Gelegentlich kann der Ladetest-Container die Ausführung als fehlgeschlagen melden, selbst wenn nur eine Ausnahme auftritt. Der Fehler wird nur gemeldet, wenn der Testprozess nicht wiederhergestellt werden kann.

* Bestimmte Groß-/Kleinschreibung-Abweichungen zwischen der Art und Weise, wie Umgebungsnamen gespeichert wurden, führten zu Leistungstestfehlern.

* Einige Pipeline-Fehler wurden fälschlicherweise als Pipeline-Fehler gemeldet.
