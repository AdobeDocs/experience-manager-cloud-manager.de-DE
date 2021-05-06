---
title: Versionshinweise für 2021.4.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.4.0.
feature: Versionshinweise
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
translation-type: tm+mt
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

* Die Zeitüberschreitung bei Anfragen für den Leistungstest für virtuelle Benutzer wurde von 20 auf 60 Sekunden erhöht.

* Die Schaltfläche &quot;Git verwalten&quot;wird auf der Pipelines-Karte angezeigt, auch wenn keine Pipelines konfiguriert wurden.

* Während des Bereitstellungsschritts auf der Seite &quot;Pipeline-Ausführung&quot;können die Benutzer die abgeschlossenen und zukünftigen Implementierungsschritte zusätzlich zum aktuellen Schritt in der Benutzeroberfläche für den Status *In Bearbeitung* sehen.

* Die Version des von Cloud Manager verwendeten AEM Projektarchivs wurde auf Version 27 aktualisiert.

* Die Fehlermeldung beim Starten einer Pipeline beim Löschen einer Umgebung wurde geklärt.

* OSGi-Pakete, die von Eclipse-Projekten bereitgestellt werden, sind nun von der Regel `CQBP-84--dependencies` ausgeschlossen.

## Fehlerbehebungen {#bug-fixes}

* Seltene, vorübergehende Fehler, die beim *Assets Test*-Schritt in der Produktions-Pipeline auftreten können.

* Ein nachfolgender Schrägstrich in der Produktionsleitung Lasttest verursachte einen 404-Fehler.

* Die `Runmode`-Prüfung ergab Falsch-Positiv-Werte für Nicht-Ordner-Knoten.