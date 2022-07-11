---
title: Verwalten von Umgebungen
description: Erfahren Sie, wie Sie Ihre Umgebungen mit Cloud Manager verwalten können.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 80f8707e00357f5a08dd835b846c9ee610f3e573
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 41%

---


# Verwalten von Umgebungen {#managing-environments}

Erfahren Sie, wie Sie Ihre Umgebungen mit Cloud Manager verwalten können.

## Übersichtsseite {#overview-page}

Auf der Seite **Übersicht** von Cloud Manager finden Sie die Kachel **Umgebungen** mit allen verwalteten AEM-Umgebungen.

Jede Umgebung wird mit ihrem zugehörigen Status angezeigt.

![Übersichtsseite](/help/assets/Manage-Environ-Overview.png)

## Kachel &quot;Umgebungen&quot; {#environments-tile}

Die **Umgebungen** -Kachel zeigt die in Ihrem Programm bereitgestellten Produktions- und Staging-Umgebungen zusammen mit dem Status an.

Der Status ist der aggregierte Leistungsstatus über die Knoten in der Umgebung in der folgenden Prioritätsreihenfolge hinweg.

* Grün: Alle Knoten werden ausgeführt
* Rot - Ein oder mehrere Knoten werden angehalten.
* Blau - Es wird ein oder mehrere Knoten angezeigt.
* Gelb - Ein oder mehrere Knoten verfügen über keinen Leistungsstatus.

![Umgebungskachel](/help/assets/Environments-card-new.png)

## Verwalten von Umgebungen {#managing-environments-with-cloud-manager}

Im **Umgebungen** tile, click **Verwalten** , um **Umgebungen** angezeigt.

Die **Umgebungen** -Bildschirm zeigt eine Karte für Produktions- und Staging-Umgebungen (falls zutreffend) in Ihrem Programm an. Der Name der Umgebung wird über jeder Karte angezeigt. Die Karte enthält eine Tabelle der Knoten in der Umgebung sowie die Größe der CPU, den Speicher, die Region und den Status.

>[!NOTE]
>
>Der **STATUS** des Knotens stellt den Leistungsstatus der VM dar und spiegelt nicht den Status von AEM auf dem Server wider. Der Status kann wie folgt lauten:

* Green - Running
* Rot - Angehalten
* Blue - Coming up
* Gelb - nicht verfügbar

![Registerkarte Umgebungen](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Wenn Sie Ihre Umgebungsprotokolle benötigen, können Sie diese von Ihrem Customer Success Engineer anfordern.

## Video-Tutorial {#video-tutorial}

Dieses Video bietet einen Überblick über Cloud Manager-Umgebungen, die aus AEM Authoring-, Publishing- und Dispatcher-Instanzen bestehen.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)
