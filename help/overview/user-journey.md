---
title: Anwendertour
description: Lernen Sie die verschiedenen Onboarding-Szenarien kennen und lernen Sie die ersten Schritte mit Cloud Manager kennen.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 6a5615c0db91c62fc8858b967021b46c7b383aa0
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 24%

---


# Journey {#user-journey}

Als AEM (Adobe Experience Manager)-Benutzer passen Sie wahrscheinlich eines der folgenden Szenarien an:

* Du bist neu AEM.
* Sie verwenden derzeit AEM 6.x.
* Sie müssen auf AEM 6.5 aktualisieren, um [!UICONTROL Cloud Manager] zu verwenden.

In diesem Dokument werden diese drei Szenarien beschrieben und Ihre Journey für die ersten Schritte mit [!UICONTROL Cloud Manager] erläutert.

>[!NOTE]
>
>[!UICONTROL Cloud Manager] ist nur für Kunden von Adobe Managed Services mit AEM 6.4 oder höher verfügbar.

## Onboarding {#onboarding}

Der Onboarding-Prozess unterscheidet sich, je nachdem, ob Sie neu bei AMS sind oder bereits Kunde bei AMS.

### Neu bei Adobe Managed Services {#new-to-ams}

Als neuer Kunde werden Sie als Teil des Onboarding-Prozesses an Adobe Managed Services in [!UICONTROL Cloud Manager] integriert.

Im Rahmen des Onboarding-Prozesses erhalten Sie eine Begrüßungs-E-Mail mit folgenden Informationen:

* Die URL für den Zugriff auf [!UICONTROL Cloud Manager].
* Anweisungen zum Anmelden bei [!UICONTROL Experience Cloud].
* Anweisungen zur Verwendung der Admin Console für die Verwaltung Ihrer Anwender und der entsprechenden Berechtigungen, damit sie, falls erforderlich, auf [!UICONTROL Cloud Manager] zugreifen können.

### Aktueller Adobe Managed Services-Kunde {#existing-customer}

Als bestehender AMS-Kunde müssen Sie zunächst Ihre bestehenden Produktions- und Nicht-Produktionsumgebungen auf AEM 6.4 oder höher aktualisieren.

Während des Upgrades werden Sie in Cloud Manager integriert und erhalten die URL für den Zugriff auf [!UICONTROL Cloud Manager]. Darüber hinaus müssen Sie für Benutzer, die auf [!UICONTROL Cloud Manager] zugreifen müssen, die Admin Console verwenden, um sie und ihre jeweiligen Berechtigungen zu verwalten.

Ihr vorhandenes AEM-Projekt muss auch den empfohlenen Best Practices entsprechen, da Sie beginnen, [!UICONTROL Cloud Manager] für die Bereitstellung neuer Codeänderungen in Ihren AEM-Umgebungen zu verwenden.

Weitere Informationen zu den Vorteilen der Aktualisierung auf AEM 6.5 finden Sie unter [Upgrade auf AEM 6.5](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Zugriff auf [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Melden Sie sich mit Ihren Adobe Identity Management-Anmeldedaten bei der Landingpage [!UICONTROL Experience Cloud] an. Wählen Sie von dort AEM aus dem Lösungsschalter aus, um auf [!UICONTROL Cloud Manager] und Ihre AEM Umgebungen zuzugreifen.

Nach der erstmaligen Anmeldung bei [!UICONTROL Cloud Manager] haben Sie direkt über die Benutzeroberfläche von [!UICONTROL Cloud Manager] Zugriff auf Ihre AEM-Umgebungen. Jetzt sind Sie bereit, alle Möglichkeiten von [!UICONTROL Cloud Manager] zu erkunden und Ihre erste Code-Verzweigung vorzubereiten, um sie in Ihren Staging- und Produktionsumgebungen bereitzustellen.

Informationen zu den ersten Schritten mit [!UICONTROL Cloud Manager] finden Sie unter [Erste Anmeldung](/help/getting-started/first-time-login.md).

Weitere Informationen zu AEM finden Sie unter [Bereitstellen und Warten](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Erste Schritte mit [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Nachdem Sie sich bei [!UICONTROL Cloud Manager] angemeldet haben, können Sie mit Ihrem AEM-Projekt wie folgt beginnen:

1. Richten Sie Ihre Code-Repository-Umgebung ein.
1. Richten Sie Ihr Team und Ihre Rollen ein. Rollenmitgliedschaften werden zugewiesen, indem der Anwender über die Admin Console zu einem [!UICONTROL Cloud Manager]-Profil hinzugefügt wird.
1. Richten Sie Ihre Quellcodeverzweigungen im Git-Repository ein.
1. Definieren Sie Ihre Ziele in Bezug auf Auslastungs- und Leistungs-KPIs (Key Performance Indicators).
1. Definieren Sie Testszenarien, um Ihren Code erfolgreich in Ihrer Staging- und Produktionsumgebung bereitzustellen, nachdem alle Qualitätsprüfungen abgeschlossen sind.

## Durchgängige Journey {#end-to-end-journey}

Dieses Diagramm veranschaulicht die Journey auf hoher Ebene des Kunden, wenn die CI/CD-Pipeline von [!UICONTROL Cloud Manager] für die Bereitstellung Ihrer Codeänderungen in Ihren Staging- und Produktionsumgebungen verwendet wird.

![End-to-End-Journey](/help/assets/screen_shot_2018-05-15at124004pm.png)
