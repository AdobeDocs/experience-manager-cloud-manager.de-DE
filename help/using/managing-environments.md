---
title: Verwalten von Umgebungen
description: Erfahren Sie, wie Sie Ihre Umgebungen mit Cloud Manager erstellen.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
TQID: https://experienceleague.adobe.com/Dz3Z5i-gSNSorc7Na74RKgm3e0P9b-3vjVRdJvu6a0c
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 0dde660205ad28bc5924a5cc14404c48a0533ceb
workflow-type: tm+mt
source-wordcount: 261
ht-degree: 57%

---

# Verwalten von Umgebungen {#managing-environments}

Erfahren Sie, wie Sie Ihre Umgebungen mit Cloud Manager erstellen.

## Übersichtsseite {#overview-page}

Auf der Seite **Übersicht** von Cloud Manager finden Sie die Kachel **Umgebungen** mit allen verwalteten AEM-Umgebungen.

Jede Umgebung wird mit ihrem zugehörigen Status angezeigt.

![Übersichtsseite](/help/assets/Manage-Environ-Overview.png)

## Kachel „Umgebungen“ {#environments-tile}

Auf der Kachel **Umgebungen** werden die in Ihrem Programm bereitgestellten Produktions- und Staging-Umgebungen zusammen mit dem Status angezeigt.

Der Status ist der aggregierte Leistungsstatus über alle Umgebungsknoten in der richtigen Reihenfolge.

* Grün: Alle Knoten werden ausgeführt
* Rot: Ein oder mehrere Knoten wurden angehalten.
* Blau: Ein oder mehrere Knoten werden gestartet.
* Gelb: Ein oder mehrere Knoten verfügen über keinen Leistungsstatus.

![Kachel „Umgebungen“](/help/assets/Environments-card-new.png)

## Verwalten von Umgebungen {#managing-environments-with-cloud-manager}

Klicken Sie auf der Kachel **Umgebungen** auf die Zeile einer beliebigen Umgebung, um den Bildschirm **Umgebungen** anzuzeigen.

Der **Umgebungen** zeigt alle Produktions- und Staging-Umgebungen in Ihrem Programm an. Der Name der Umgebung wird über jeder Karte angezeigt. Die Karte enthält eine Tabelle mit den Knoten in der Umgebung sowie die Größe von CPU, Speicher, Region und Status.

>[!NOTE]
>
>Der **STATUS** des Knotens stellt den Leistungsstatus der VM dar und spiegelt nicht den Status von AEM auf dem Server wider. Der Status kann wie folgt lauten:

* Grün: Wird ausgeführt
* Rot: Angehalten
* Blau: Start
* Gelb: Nicht verfügbar

![Registerkarte „Umgebungen“](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Umgebungsdetails wie der Name können nach der Bereitstellung nicht mehr geändert werden.

>[!NOTE]
>
>Fordern Sie Ihre Umgebungsprotokolle über Ihren Customer Success-Mitarbeiter an.

## Video-Tutorial {#video-tutorial}

In diesem Video erhalten Sie eine Einführung in Cloud Manager-Umgebungen, die aus Authoring-, Publishing- und Dispatcher-Instanzen von AEM bestehen.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

*(3 Minuten, 1 Sekunde)*
