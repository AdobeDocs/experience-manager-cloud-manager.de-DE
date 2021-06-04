---
title: Versionshinweise für 2018.9.0
seo-title: Versionshinweise für AEM Cloud Manager 2018.9.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2018.9.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2018.9.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
feature: Versionshinweise
exl-id: bf611743-ded2-4503-97c8-12b12454c7b7
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2018.9.0 {#release-notes-for}

Die [!UICONTROL Cloud Manager]-Version 2018.9.0 unterstützt nun eine Adobe I/O-basierte API, einschließlich Ereignissen, um die CI/CD-Pipeline von [!UICONTROL Cloud Manager] in andere Systeme integrieren zu können. Damit beginnt darüber hinaus das React-Rewrite der UI-Schicht.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2018.9.0 wurde am 1. November 2018 veröffentlicht.

## Neuigkeiten {#whats-new}

* **CI/CD-Pipeline**: Neue API und neues Ereignissystem zur Integration der CI/CD-Pipeline von [!UICONTROL Cloud Manager] mit anderen Systeme. Weitere Informationen finden Sie in der [!UICONTROL Cloud Manager]-API-Dokumentation (https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html).

* **Benutzeroberfläche**: Einführung einer neuen schnelleren Benutzeroberflächenschicht.

## Fehlerbehebungen {#bug-fixes}

* In [!UICONTROL Cloud Manager] 2018.8.0 wurde auf der Seite „Aktivität“ die zugehörige Dauer in Minuten und Stunden aufgelistet, aber diese Informationen wurden nicht im Tabellenkopf angezeigt.
* In seltenen Fällen konnten Kunden den neuen Assistenten für Anwendungsprojekte nicht starten.
* Die Schaltflächenzeichnung im Dialogfeld des neuen Assistenten für Anwendungsprojekte war irreführend.
* Unter bestimmten Umständen führte ein Klick auf die Schaltfläche „Details“ der Seite „Aktivität“ zur Seite „Übersicht“.
* Unter bestimmten seltenen und unerwarteten Umständen fehlte eine Karte auf der Seite „Übersicht“.
* Das Assets-Symbol wurde auf der Seite „Programmliste“ für alle Kunden angezeigt.
* Bei Back-End-Fehlern verblieb eine Pipelineausführung manchmal dauerhaft im Schritt *Validieren*.
* Unter bestimmten Umständen wurde die Länge der Programmbeschreibung falsch berechnet.

## Bekannte Probleme {#known-issues}

* Mit dem Assistenten für Anwendungsprojekte erstellte Verzweigungen dürfen keine Bindestriche enthalten.
* In der Seitenleiste für Adobe [!UICONTROL Experience Cloud]-Benachrichtigung werden Benachrichtigungen möglicherweise nicht konsistent geladen. Benachrichtigungen werden jedoch in Adobe [!UICONTROL Experience Cloud] angezeigt und, sofern konfiguriert, weiterhin per E-Mail gesendet.
