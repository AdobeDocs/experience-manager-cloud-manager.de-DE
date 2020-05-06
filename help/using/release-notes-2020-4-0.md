---
title: Versionshinweise für 2020.4.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.4.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.4.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.4.0.
translation-type: tm+mt
source-git-commit: 278858465592482449080fedc3c0165805db223d
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 100%

---

# Versionshinweise für 2020.4.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.4.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2020.4.0 wurde am 09. April 2020 veröffentlicht.

## Neuerungen {#whats-new}

* Änderungen an der Navigation: Cloud Manager-Übersichtsseite, mit der Benutzer das Programm bearbeiten oder wechseln können.
* Änderungen, die es Benutzern erlauben, das Programm über die Programmkarte auf der Startseite von Cloud Manager zu bearbeiten.
* Neuer Pipeline-Status: **Pipeline wird ausgeführt** wird in der Umgebung angezeigt, der sie zugewiesen ist.
* Bessere Verständlichkeit der Pipeline-Ausführungsseite. Dazu gehören die Anzeige des Pipeline-Namens (nur produktionsfremde Pipelines) und des Typs sowie ein Zeichen mit dem Pipeline-Status (Wird ausgeführt/Abgebrochen/Fehlgeschlagen).
* Der zur Erstellung von Git-Kennwörtern Prozess ist jetzt weniger anfällig für Probleme in der zugrunde liegenden Service-Ebene.

## Fehlerbehebungen {#bug-fixes}

* Überwachungsdaten wurden gelegentlich aufgrund kleiner Abweichungen bei technischen Werten falsch oder gar nicht angezeigt.
* Die Maven-Konfiguration, die im Build-Container verwendet wird, wurde aktualisiert, um Deadlocks beim Download von Artefaktmetadaten zu vermeiden.
* Der Prozess zum Testen der Performance von Assets konnte gelegentlich das AEM-Kennwort nicht entschlüsseln, wodurch der Test fehlschlug.
* Bestimmte Topologien mit Standby-Instanzen wiesen bei Sicherheitstests manchmal falsch negative Werte auf.
* Wenn die Staging-Umgebung eine angehaltene Instanz enthielt, schlug der Sicherheitstestschritt manchmal fehl.
* Experience Cloud-Benachrichtigungen wurden nicht konsistent empfangen.

