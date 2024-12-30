---
title: User Journey
description: Lernen Sie die verschiedenen Onboarding-Szenarien und die ersten Schritte mit Cloud Manager kennen.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 100%

---


# User Journey {#user-journey}

Wenn Sie AEM (Adobe Experience Manager) verwenden, trifft auf Sie wahrscheinlich eines der folgenden Szenarien zu:

* Sie verwenden AEM zum ersten Mal.
* Sie verwenden derzeit AEM 6.x.
* Sie müssen auf AEM 6.5 aktualisieren, um [!UICONTROL Cloud Manager] verwenden zu können.

In diesem Dokument werden diese drei Szenarien erläutert und Ihre Journey für die ersten Schritte mit [!UICONTROL Cloud Manager] erklärt.

>[!NOTE]
>
>[!UICONTROL Cloud Manager] ist nur für Kunden von Adobe Managed Services mit AEM 6.4 oder höher verfügbar.

## Onboarding {#onboarding}

Der Onboarding-Prozess unterscheidet sich, je nachdem, ob Sie neu bei AMS sind oder bereits Kunde bei AMS.

### Neu bei Adobe Managed Services {#new-to-ams}

Als Neukundin oder Neukunde erfolgt Ihr Onboarding für [!UICONTROL Cloud Manager] im Rahmen des Onboardings für Adobe Managed Services.

Im Zuge dieses Onboarding-Prozesses erhalten Sie eine Begrüßungs-E-Mail mit folgenden Informationen:

* URL für den Zugriff auf [!UICONTROL Cloud Manager]
* Anleitung zur Anmeldung bei [!UICONTROL Experience Cloud]
* Anweisungen zur Verwendung der Admin Console für die Verwaltung Ihrer Benutzenden und der entsprechenden Berechtigungen, damit sie, falls erforderlich, auf [!UICONTROL Cloud Manager] zugreifen können.

### Aktuelle Adobe Managed Services-Kundschaft {#existing-customer}

Als AMS-Bestandskundin oder -Bestandskunde müssen Sie zunächst Ihre vorhandenen Produktions- und produktionsfremden Umgebungen auf AEM 6.4 oder höher aktualisieren.

Während des Upgrades erfolgt Ihr Cloud Manager-Onboarding und Sie erhalten die URL für den Zugriff auf [!UICONTROL Cloud Manager]. Außerdem müssen Sie für die Benutzenden, die auf [!UICONTROL Cloud Manager] zugreifen müssen, die Admin Console verwenden, um sie und ihre jeweiligen Berechtigungen zu verwalten.

Auch vorhandene AEM-Projekte müssen den empfohlenen Best Practices entsprechen, weil Sie mit [!UICONTROL Cloud Manager] neue Code-Änderungen in Ihren AEM-Umgebungen bereitstellen.

Weitere Informationen zu den Vorteilen der Aktualisierung auf AEM 6.5 finden Sie unter [Upgrade auf AEM 6.5](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/upgrading/upgrade).

## Zugreifen auf [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Melden Sie sich mit Ihren Adobe Identity Management-Anmeldedaten bei der Landingpage von [!UICONTROL Experience Cloud] an. Wählen Sie dort AEM aus der Lösungsauswahl aus, um auf [!UICONTROL Cloud Manager] und Ihre AEM-Umgebungen zuzugreifen.

Nach der erstmaligen Anmeldung bei [!UICONTROL Cloud Manager] können Sie direkt über die [!UICONTROL Cloud Manager]-Benutzeroberfläche auf Ihre AEM-Umgebungen zugreifen. Jetzt sind Sie bereit, alle Möglichkeiten von [!UICONTROL Cloud Manager] zu erkunden und Ihre erste Code-Verzweigung vorzubereiten, um sie in Ihren Staging- und Produktionsumgebungen bereitzustellen.

Die ersten Schritte mit [!UICONTROL Cloud Manager] werden unter [Erste Anmeldung](/help/getting-started/first-time-login.md) beschrieben.

Weitere Informationen zu AEM finden Sie unter [Bereitstellen und Verwalten](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/deploying/deploy).

## Erste Schritte mit [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Sobald Sie bei [!UICONTROL Cloud Manager] angemeldet sind, können Sie mit Ihrem AEM-Projekt beginnen, indem Sie wie folgt vorgehen:

1. Richten Sie Ihre Code-Repository-Umgebung ein.
1. Richten Sie Ihr Team und die zugehörigen Rollen ein. Rollenmitgliedschaften werden zugewiesen, indem die Benutzenden über die Admin Console zu einem [!UICONTROL Cloud Manager]-Profil hinzugefügt werden.
1. Richten Sie Ihre Quell-Code-Verzweigungen im Git-Repository ein.
1. Definieren Sie Ihre Ziele in Bezug auf Last- und Performance-KPIs (Key Performance Indicators).
1. Definieren Sie Testszenarien, um Ihren Code erfolgreich in Ihren Staging- und Produktionsumgebungen bereitzustellen, nachdem alle Qualitätsprüfungen bestanden wurden.

## End-to-End-Journey {#end-to-end-journey}

Dieses Diagramm veranschaulicht die Customer Journey auf allgemeiner Ebene, wenn Sie die [!UICONTROL Cloud Manager]-CI/CD-Pipeline zur Bereitstellung Ihrer Code-Änderungen in Ihren Staging- und Produktionsumgebungen verwenden.

![End-to-End-Journey](/help/assets/screen_shot_2018-05-15at124004pm.png)
