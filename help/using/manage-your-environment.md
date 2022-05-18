---
title: Verwalten von Umgebungen
seo-title: Manage your Environments
description: Informationen zur Cloud Manager-Umgebung
seo-description: Follow this page to view the list of production and non-production environments that are used for setting up and running the CI/CD pipeline in Cloud Manager.
uuid: 04e67572-11db-4d5d-acf3-fd7f644a95f0
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: c5b39de2-3a9b-437f-98e8-e6e6249a5b3a
feature: Environments
exl-id: 700b0b4c-1e1a-4993-b366-426b14a98f8e
source-git-commit: 6ff704ec11dd4a5f73d5b5df5721c4fee649527b
workflow-type: ht
source-wordcount: '280'
ht-degree: 100%

---

# Verwalten von Umgebungen {#manage-your-environments}

>[!NOTE]
>Informationen zum Verwalten von Umgebungen für Cloud Manager in AEM as a Cloud Service finden Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de#using-cloud-manager).

Auf der Seite **Übersicht** von Cloud Manager finden Sie die Kachel **Umgebungen** mit allen verwalteten AEM-Umgebungen.

Jede Umgebung wird mit ihrem zugehörigen Status angezeigt.

![](assets/Manage-Environ-Overview.png)

## Video-Tutorial {#video-tutorial}

### Überblick über die Cloud Manager-Umgebung {#environ-video}

Das folgende Video bietet einen Überblick über Cloud Manager-Umgebungen, die aus AEM-Autoren-, AEM-Veröffentlichungs- und Dispatcher-Instanz bestehen.

>[!VIDEO](https://video.tv.adobe.com/v/26318/)

## Zugreifen auf Umgebungen in Cloud Manager {#accessing-environments-in-cloud-manager}

Auf der Kachel **Umgebungen** werden die in Ihrem Programm bereitgestellten Produktions- und Staging-Umgebungen zusammen mit dem Status angezeigt.

Der Status entspricht dem aggregierten Leistungsstatus für alle Knoten in der Umgebung. Der Status leuchtet grün, wenn alle Knoten ausgeführt werden, rot, wenn auch nur ein Knoten angehalten wurde, blau, wenn auch nur ein Knoten aktiv wird, und gelb, wenn auch nur für ein Knoten kein Leistungsstatus verfügbar ist (in dieser Prioritätsreihenfolge).

![](assets/Environments-card-new.png)

### Umgebungen {#environments}

Klicken Sie auf **Verwalten**, um den Bildschirm **Umgebungen** anzuzeigen.

Auf dem Bildschirm **Umgebungen** wird jeweils eine Karte für *Produktions-* und *Staging-Umgebungen* (sofern zutreffend) in Ihrem Programm angezeigt. Der Name der Umgebung wird über jeder Karte angezeigt. Die Karte enthält eine Tabelle der Knoten in der Umgebung sowie die Größe der CPU, den Speicher, die Region und den Status.

>[!NOTE]
>
>Der **STATUS** des Knotens stellt den Leistungsstatus der VM dar und spiegelt nicht den Status von AEM auf dem Server wider. Der Status kann wie folgt lauten: **Aktiv** (grüner Kreis), **Angehalten** (roter Kreis), **Demnächst aktiv** (blauer Kreis) oder **Nicht verfügbar** (gelber Kreis).

![](assets/Environments-tab.png)

>[!NOTE]
>
>Wenn Sie Ihre Umgebungsprotokolle benötigen, können Sie diese von Ihrem Customer Success Engineer anfordern.
