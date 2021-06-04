---
title: Versionshinweise für 2021.4.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.4.0.
feature: Versionshinweise
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 5f81fdb86b1dfa6c748bb7784ef00dc062c9f8ef
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2021.4.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2021.4.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.4.0 wurde am 8. April 2021 veröffentlicht.

## Neuigkeiten {#whats-new}

* Das Timeout bei Anfragen für den Leistungstest für virtuelle Benutzer wurde von 20 auf 60 Sekunden erhöht.

* Die Schaltfläche „Git verwalten“ wird auf der Karte „Pipelines“ angezeigt, auch wenn keine Pipelines konfiguriert wurden.

* Während des Bereitstellungsschritts auf der Seite zur Pipeline-Ausführung können die Benutzer die abgeschlossenen und zukünftigen Implementierungsschritte zusätzlich zum aktuellen Schritt auf der Benutzeroberfläche für den Status *In Bearbeitung* sehen.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 27 aktualisiert.

* Die Fehlermeldung beim Starten einer Pipeline nach dem Löschen einer Umgebung wurde klarer formuliert.

* OSGi-Pakete, die von Eclipse-Projekten bereitgestellt werden, sind nun von der Regel `CQBP-84--dependencies` ausgeschlossen.

## Fehlerbehebungen {#bug-fixes}

* Seltene vorübergehende Fehler, die beim Schritt *Assets Test* in der Produktions-Pipeline auftreten können.

* Ein nachfolgender Schrägstrich im Lasttest der Produktions-Pipeline verursachte einen 404-Fehler.

* Die `Runmode`-Prüfung ergab falschpositive Werte für Nicht-Ordner-Knoten.