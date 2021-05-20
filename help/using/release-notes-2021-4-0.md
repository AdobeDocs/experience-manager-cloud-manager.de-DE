---
title: Versionshinweise für 2021.4.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.4.0.
feature: Versionshinweise
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 5f81fdb86b1dfa6c748bb7784ef00dc062c9f8ef
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 23%

---

# Versionshinweise für 2021.4.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2021.4.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.4.0 wurde am 08. April 2021 veröffentlicht.

## Neue Funktionen {#whats-new}

* Das Zeitlimit für Anfragen für virtuelle Benutzer mit Leistungstests wurde von 20 auf 60 Sekunden erhöht.

* Die Schaltfläche Git verwalten wird auch dann auf der Karte Pipelines angezeigt, wenn keine Pipelines konfiguriert wurden.

* Während des Bereitstellungsschritts der Pipeline-Ausführungsseite können Benutzer die abgeschlossenen und künftigen Implementierungsschritte zusätzlich zum aktuellen Schritt in der Benutzeroberfläche für den Status *In Bearbeitung* sehen.

* Die Version des von Cloud Manager verwendeten AEM Projektarchetyps wurde auf Version 27 aktualisiert.

* Die Fehlermeldung beim Starten einer Pipeline beim Löschen einer Umgebung wurde geklärt.

* Von Eclipse-Projekten bereitgestellte OSGi-Bundles sind jetzt von der Regel `CQBP-84--dependencies` ausgeschlossen.

## Fehlerbehebungen {#bug-fixes}

* Seltene vorübergehende Fehler, die beim Schritt *Assets-Test* in der Produktions-Pipeline auftreten können.

* Ein nachfolgender Schrägstrich im Produktions-Pipeline-Ladetest verursachte einen 404-Fehler.

* Die `Runmode`-Prüfung erzeugte Fehlalarme auf Nicht-Ordner-Knoten.