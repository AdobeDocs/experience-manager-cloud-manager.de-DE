---
title: Versionshinweise für 2020.8.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.8.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.8.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.8.0.
translation-type: tm+mt
source-git-commit: cff6f23a674fda2f57ea481d89644de9be3f5722
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 100%

---

# Versionshinweise für 2020.8.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.8.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2020.8.0 wurde am 06. August 2020 veröffentlicht.

## Neuerungen {#whats-new}

Authentifizierungsgebundene Private Maven-Repositorys werden jetzt unterstützt.

## Fehlerbehebungen {#bug-fixes}

* Einige unnötige und unerwünschte SonarQube-Plug-ins wurden im Rahmen der Überprüfung der Codequalität ausgeführt.

* Auf der Seite zur Ausführung der Pipeline wurde der Verzweigungsname falsch formatiert.

* Bei der Bereitstellung in Topologien mit einer einzigen Veröffentlichung, einem einzigen Dispatcher und einem Cold-Standby-Autor wurde der Dispatcher fälschlicherweise aus dem Load Balancer entfernt.

* In einigen Fällen wurden abgeschlossene Pipeline-Ausführungen nicht erfolgreich als abgeschlossen aufgezeichnet, wodurch neue Ausführungen der Pipeline verhindert wurden.

* Pipeline-Ausführungen blieben gelegentlich aufgrund interner Kommunikationsprobleme *stecken*.

* Die QuickInfo auf den Programmkarten war nicht immer korrekt.

* Auf der Übersichtsseite wurden Farbabweichungen festgestellt.

