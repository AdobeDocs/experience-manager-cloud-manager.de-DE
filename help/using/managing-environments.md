---
title: Verwalten von Umgebungen
description: Erfahren Sie, wie Sie Ihre Umgebungen mit Cloud Manager erstellen.
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 0b7c926120798e2fdb635752192f4ab2e12c1e24
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 100%

---


# Verwalten von Umgebungen {#managing-environments}

Erfahren Sie, wie Sie Ihre Umgebungen mit Cloud Manager erstellen.

## Übersichtsseite {#overview-page}

Auf der Seite **Übersicht** von Cloud Manager finden Sie die Kachel **Umgebungen** mit allen verwalteten AEM-Umgebungen.

Jede Umgebung wird mit ihrem zugehörigen Status angezeigt.

![Übersichtsseite](/help/assets/Manage-Environ-Overview.png)

## Kachel „Umgebungen“ {#environments-tile}

Auf der Kachel **Umgebungen** werden die in Ihrem Programm bereitgestellten Produktions- und Staging-Umgebungen zusammen mit dem Status angezeigt.

Der Status ist der aggregierte Leistungsstatus über alle Knoten in der Umgebung, in der folgenden Prioritätsreihenfolge.

* Grün: Alle Knoten werden ausgeführt
* Rot: Ein oder mehrere Knoten sind angehalten.
* Blau: Ein oder mehrere Knoten sind im Entstehen.
* Gelb: Ein oder mehrere Knoten verfügen über keinen Leistungsstatus.

![Kachel „Umgebungen“](/help/assets/Environments-card-new.png)

## Verwalten von Umgebungen {#managing-environments-with-cloud-manager}

Klicken Sie auf der Kachel **Umgebungen** auf die Zeile einer beliebigen Umgebung, um den Bildschirm **Umgebungen** anzuzeigen.

Der Bildschirm **Umgebungen** zeigt jede Produktions- und Staging-Umgebung in Ihrem Programm an. Der Name der Umgebung wird über jeder Karte angezeigt. Die Karte enthält eine Tabelle der Knoten in der Umgebung sowie die Größe der CPU, den Speicher, die Region und den Status.

>[!NOTE]
>
>Der **STATUS** des Knotens stellt den Leistungsstatus der VM dar und spiegelt nicht den Status von AEM auf dem Server wider. Der Status kann wie folgt lauten:

* Grün: Wird ausgeführt
* Rot: Angehalten
* Blau: Anstehend
* Gelb: Nicht verfügbar

![Registerkarte „Umgebungen“](/help/assets/Environments-tab.png)

>[!NOTE]
>
>Umgebungsdetails wie der Name können nach der Bereitstellung nicht mehr geändert werden.

>[!NOTE]
>
>Fordern Sie Ihre Umgebungsprotokolle bei Ihrem Customer Success Engineer an.

## Video-Tutorial {#video-tutorial}

Dieses Video bietet einen Überblick über Cloud Manager-Umgebungen, die aus AEM-Autoren-, -Veröffentlichungs- und -Dispatcher-Instanzen bestehen.

>[!VIDEO](https://video.tv.adobe.com/v/34566?captions=ger)

*(3 Minuten, 1 Sekunde)*
