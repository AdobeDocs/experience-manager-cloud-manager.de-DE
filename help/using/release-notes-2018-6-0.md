---
title: Versionshinweise für 2018.6.0
seo-title: AEM Cloud Manager Release Notes for 2018.6.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2018.6.0.
seo-description: Follow this page to get information for AEM Cloud Manager Release 2018.6.0.
uuid: 211b6e1b-10fb-46b0-b591-44d5e44abd77
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: release-notes
discoiquuid: 8584f467-3e61-41ea-98e4-f79e68c86469
feature: Release Information
exl-id: 456f7892-c64c-4b3f-b845-15682d034aaa
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 89%

---

# Versionshinweise für 2018.6.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2018.6.0. Diese Version unterstützt nun Dispatcherinvalidierungen bei Bereitstellungen, bietet zusätzliche Benachrichtigungen und Verbesserungen an der Benutzerfreundlichkeit.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2018.6.0 wurde am 9. August 2018 veröffentlicht.

## Neue Funktionen {#what-s-new}

* **CI/CD-Pipeline**: Konfigurierbare Dispatcherinvalidierung und Cacheflushing in der Staging- und Produktionsumgebung während der CI/CD-Pipelineausführung. Weitere Informationen finden Sie im Dokument . [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md) , um mehr zu erfahren.

* **CI/CD-Pipeline**: Während der Pipelineeinrichtung können Sie nun definieren, wie sich die Pipeline verhält, wenn ein wesentlicher Fehler an einem der Quality Gates auftritt. Weitere Informationen finden Sie im Dokument . [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md) , um mehr zu erfahren.

* **CI/CD-Pipeline**: Während der Pipelineeinrichtung können Sie nun festlegen, ob der für Sie zuständige oder ein beliebiger CSE eine CSE-Überwachung durchführen soll. Weitere Informationen finden Sie im Dokument . [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md) , um mehr zu erfahren.

* **CI/CD-Pipeline**: Wenn die CI/CD-Pipeline den Schritt „Geschäftsgenehmigung“ erreicht, wird eine Benachrichtigung an die Anwender gesendet, die zur Genehmigung der Bereitstellung berechtigt sind. Weitere Informationen finden Sie unter [Benachrichtigungen](notifications.md).

* **CI/CD-Pipeline**: Wenn die CI/CD-Pipeline den Schritt „Zeitplan“ erreicht, wird eine Benachrichtigung an die Anwender gesendet, die zum Festlegen des Zeitplans berechtigt sind. Weitere Informationen finden Sie unter [Benachrichtigungen](notifications.md).

* **Analyse der Code-Qualität**: Neue Regeln zur Erkennung falsch konfigurierter ausgehender HTTP/HTTPS-Anforderungen. Weitere Informationen finden Sie unter [Qualitätsregeln für benutzerdefinierten Code](custom-code-quality-rules.md).

## Fehlerbehebungen {#bug-fixes}

* In einigen Fällen wurde der Leistungstest nicht vollständig über mehrere Dispatcher- und Veröffentlichungsinstanzen verteilt.
* In schmalen Browserfenstern wurde die Kopfzeilennavigation nicht mehr angezeigt.
* Einige Pipelineeinstellungen wurden während der Pipelineausführung nicht deaktiviert.
* Die Links zu „AEM“ und „Überwachung“ auf dem Bildschirm „Programmliste“ ersetzten die aktuelle Browserregisterkarte und riefen eine neue Registerkarte auf.
* Unter bestimmten Umständen führte ein langer Genehmigungszeitraum zu einer fehlgeschlagenen Bereitstellung.
