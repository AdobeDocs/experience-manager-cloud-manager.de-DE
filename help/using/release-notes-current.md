---
title: Versionshinweise für 2020.8.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.8.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.8.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.8.0.
translation-type: tm+mt
source-git-commit: c0881ccf602a14b00b7cc68c3d1fc60e7b6954ed
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2020.8.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.8.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2020.8.0 wurde am 06. August 2020 veröffentlicht.

## Neuerungen {#whats-new}

* Der Site-Leistungstest unterstützt jetzt die optionale Verwendung der Authentifizierung.

   Informationen zum Authentifizieren von AEM Sites-Leistungstests finden Sie unter [Authentifizierte Sites - Leistungstests](configuring-pipeline.md#authenticated-sites-performance) .

* Authentifizierungsgebundene private Maven-Repositorys werden jetzt unterstützt.

## Fehlerbehebungen {#bug-fixes}

* Einige unnötige und unerwünschte SonarQube-Plugins wurden im Rahmen der Überprüfung der Codequalität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Zweigname falsch formatiert.

* Bei der Bereitstellung auf Topologien mit einer einzigen Veröffentlichung, einem einzelnen Dispatcher und einem kalten Standby-Autor wurde der Dispatcher fälschlicherweise aus dem Lastenausgleich entfernt.

* In einigen Fällen wurden abgeschlossene Pipeline-Hinrichtungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Hinrichtungen der Pipeline verhindert wurden.

* Hinrichtungen von Pipeline würden gelegentlich aufgrund interner Kommunikationsprobleme *feststecken* .

* Die QuickInfo auf den Programm-Karten waren nicht einheitlich korrekt.

* Auf der Übersichtsseite wurden Farbabweichungen festgestellt.

