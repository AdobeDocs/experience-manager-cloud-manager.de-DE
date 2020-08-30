---
title: Customer Journey
seo-title: Adobe AEM Cloud Manager – Customer Journey
description: Auf dieser Seite erfahren Sie mehr über Ihre Customer Journey, wenn Sie Cloud Manager erstmals verwenden.
seo-description: Auf dieser Seite erfahren Sie mehr über Ihre Customer Journey, wenn Sie Adobe AEM Cloud Manager erstmals verwenden.
uuid: d4468eb6-5bde-48dd-b96e-0cc61e046f96
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: bc9a0d63-ae6b-4fe9-81e5-bf9844f04e54
translation-type: tm+mt
source-git-commit: ace032fbb26235d87d61552a11996ec2bb42abce
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 74%

---


# Customer Journey {#customer-journey}

Möglicherweise sind Sie neuer Kunde von Adobe Experience Manager (AEM) und verwenden derzeit AEM 6.4 oder Sie müssen auf die AEM-Version 6.4 aktualisieren, um [!UICONTROL Cloud Manager] verwenden zu können. In den folgenden Szenarien erfahren Sie, wohin Sie Ihr Weg als neuer oder bestehender Kunde führt und welche ersten Schritte in [!UICONTROL Cloud Manager] erforderlich sind.

>[!NOTE]
>
>[!UICONTROL Cloud Manager] ist nur für Kunden von Adobe Managed Services mit AEM 6.4 oder höher verfügbar.

## Onboarding-Schritte für [!UICONTROL Cloud Manager]{#on-boarding-to-cloud-manager}

1. **Neue AEM-Kunden bei Adobe Managed Services**

   As a new customer, you will be on-boarded to [!UICONTROL Cloud Manager] as part of the on-boarding process to the Adobe Managed Services.

   The URL to access [!UICONTROL Cloud Manager] will be included in the welcome email, along with the instructions to login to [!UICONTROL Experience Cloud], and use the Adobe Admin Console for managing your users and their respective permissions, for those users who need to access [!UICONTROL Cloud Manager].

1. **Bestehende AEM-Kunden bei Adobe Managed Services**

   Als bestehender Kunde müssen Sie zunächst Ihre vorhandenen Produktions- und Nicht-Produktionsumgebungen auf Version AEM 6.4 aktualisieren. Während der Aktualisierung wird das Onboarding durchgeführt und Sie erhalten die URL für den Zugriff auf [!UICONTROL Cloud Manager]. Additionally, you will need to start using the Adobe Admin Console for managing your users and their respective permissions, for those users who need to access [!UICONTROL Cloud Manager].

   Auch vorhandene AEM-Projekte müssen Best-Practice-Verfahren entsprechen, wenn Sie mit [!UICONTROL Cloud Manager] neue Code-Änderungen in Ihren AEM-Umgebungen bereitstellen.

   Weitere Informationen zu den Vorteilen der Aktualisierung auf AEM 6.4 finden Sie unter [Upgrade auf AEM 6.4](https://helpx.adobe.com/de/experience-manager/6-4/sites/deploying/using/upgrade.html).

## Zugriff auf [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

You will get access to [!UICONTROL Cloud Manager] and your AEM environments by simply logging in to the [!UICONTROL Experience Cloud] landing page, using your Adobe Identity Management credentials, and selecting AEM from the solution switcher interface.

Nach der erstmaligen Anmeldung bei [!UICONTROL Cloud Manager] können Sie direkt über die [!UICONTROL Cloud Manager]-Benutzeroberfläche auf Ihre AEM-Umgebungen zugreifen. Sobald die erste Codeverzweigung in Ihrer Staging- und Produktionsumgebung bereitgestellt werden kann, können Sie hier alle Möglichkeiten von [!UICONTROL Cloud Manager] erkunden.

Wenn Sie [!UICONTROL Cloud Manager] besser kennenlernen und die ersten Schritte umsetzen möchten, finden Sie weitere Informationen unter [Erste Anmeldung](first-time-login.md). Weitere Informationen zu AEM finden Sie unter [Erste Schritte mit AEM 6.4](https://helpx.adobe.com/de/experience-manager/6-4/sites/deploying/using/deploy.html). Weitere Informationen finden Sie unter [AEM-Ressourcen](https://www.adobe.com/marketing-cloud/experience-manager/resources.html?promoid=759X6WV8&amp;mv=other).

## Erste Schritte mit [!UICONTROL Cloud Manager]{#getting-started-with-cloud-manager}

Nach der Anmeldung bei [!UICONTROL Cloud Manager] sollten Sie zunächst Ihre Code-Repository-Umgebung und anschließend Ihr Team und die Rollen einrichten. Specifically, the role memberships are assigned by adding the user to a [!UICONTROL Cloud Manager] profile using the Admin Console UI.

Anschließend müssen Sie Ihre Quellcodeverzweigungen im **Git-Repository** einrichten, Ihre Ziele in Bezug auf Lasten- und Leistungs-KPIs definieren und Szenarien testen, damit Sie Ihren Code nach erfolgreichem Abschluss aller Qualitätsprüfungen erfolgreich in Ihrer Staging- und Produktionsumgebung bereitstellen können.

## Durchgängige Customer Journey {#end-to-end-journey}

Das folgende Diagramm zeigt die allgemeine Customer Journey auf, wenn Sie die CI-/CD-Pipeline von [!UICONTROL Cloud Manager] für die Bereitstellung Ihrer Code-Änderungen in Ihrer Staging- und Produktionsumgebung verwenden.

![](assets/screen_shot_2018-05-15at124004pm.png)

