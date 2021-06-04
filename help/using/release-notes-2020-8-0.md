---
title: Versionshinweise für 2020.8.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.8.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.8.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.8.0.
feature: Versionshinweise
exl-id: 94163e28-5c29-4a00-9a2b-e45bf6f71098
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2020.8.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2020.8.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2020.8.0 wurde am 6. August 2020 veröffentlicht.

## Neuigkeiten {#whats-new}

Authentifizierungsgebundene Private Maven-Repositorys werden jetzt unterstützt.

## Fehlerbehebungen {#bug-fixes}

* Einige unnötige und unerwünschte SonarQube-Plug-ins wurden im Rahmen der Überprüfung der Code-Qualität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Verzweigungsname falsch formatiert.

* Bei der Bereitstellung in Topologien mit einer einzigen Veröffentlichung, einem einzigen Dispatcher und einem Cold-Standby-Autor wurde der Dispatcher fälschlicherweise aus dem Load Balancer entfernt.

* In einigen Fällen wurden abgeschlossene Pipeline-Ausführungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Ausführungen der Pipeline verhindert wurden.

* Pipeline-Ausführungen blieben gelegentlich aufgrund interner Kommunikationsprobleme *stecken*.

* Die QuickInfo auf den Programmkarten war nicht immer korrekt.

* Auf der **Übersichtsseite** wurden Farbabweichungen festgestellt.

* Die Sites-Leistungstests unterstützen jetzt die optionale Verwendung der Authentifizierung.

* Dispatcher-Caches für Autoreninstanzen werden automatisch gelöscht, wenn Dispatcher-Konfigurationen über Cloud Manager bereitgestellt werden.
