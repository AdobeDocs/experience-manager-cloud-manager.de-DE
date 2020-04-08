---
title: Versionshinweise für 2020.4.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.4.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.4.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.4.0.
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d

---

# Versionshinweise für 2020.4.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.4.0.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.4.0 is April 09, 2020.

## Neuerungen {#whats-new}

* Änderungen an der Übersichtsseite des CM-Navigationssystems, damit der Benutzer das Programm von der Übersichtsseite CM bearbeiten oder wechseln kann.
* Änderungen, die es dem Benutzer erlauben, Programm von der Programm-Karte auf der CM-Landingpage zu bearbeiten.
* Der neue Pipeline-Status &quot;Pipeline Running&quot;wird gegen die Umgebung angezeigt, mit der er verbunden ist.
* Verbesserte Verständlichkeit der Pipeline-Ausführungsseite. Dazu gehören die Anzeige des Pipeline-Namens (nur nicht in der Produktion) und des Typs sowie eine Markierung, mit der angegeben wird, ob der Pipeline-Status in Bearbeitung/Abgebrochen/Fehlgeschlagen ist.
* Der zur Erstellung von Git-Passwörtern verwendete Prozess wurde für Probleme in der zugrunde liegenden Service-Ebene widerstandsfähiger gemacht.

## Fehlerbehebungen {#bug-fixes}

* Überwachungsdaten könnten manchmal auf falsche Weise oder gar nicht aufgrund kleiner Abweichungen bei technischen Werten angezeigt werden.
* Die Maven-Konfiguration, die im Build-Container verwendet wird, wurde aktualisiert, um Deadlocks beim Herunterladen von Artefaktmetadaten zu vermeiden.
* Der Prozess zum Testen der Assets-Leistung konnte gelegentlich das AEM-Kennwort nicht entschlüsseln, wodurch der Test fehlschlug.
* Bestimmte Topologien mit Standby-Instanzen könnten bei Sicherheitstests falsche Negative aufweisen.
* Wenn die stage-Umgebung eine gestoppte Instanz enthielt, schlägt der Sicherheitstestschritt manchmal fehl.
* Experience Cloud-Benachrichtigungen wurden nicht konsistent empfangen.

