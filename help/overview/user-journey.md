---
title: Anwendertour
description: In diesem Dokument werden die verschiedenen Onboarding-Szenarien beschrieben und die Tour mit den ersten Schritten mit Cloud Manager erklärt.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 94%

---


# Anwendertour {#user-journey}

Als Adobe Experience Manager-Anwender gibt es folgende Möglichkeiten:

* Sie sind neu bei AEM.
* Sie verwenden derzeit AEM 6.x.
* Sie benötigen ein Upgrade auf AEM Version 6.5, um [!UICONTROL Cloud Manager] nutzen zu können.

In diesem Dokument werden diese Szenarien erläutert und Ihre Tour mit den ersten Schritten mit [!UICONTROL Cloud Manager] erklärt.

>[!NOTE]
>
>[!UICONTROL Cloud Manager] ist nur für Kunden von Adobe Managed Services mit AEM 6.4 oder höher verfügbar.

## Onboarding {#onboarding}

Der Onboarding-Prozess unterscheidet sich, je nachdem, ob Sie neu bei AMS sind oder bereits Kunde bei AMS.

### Neu bei Adobe Managed Services {#new-to-ams}

Als Neukunde erhalten Sie eine Einführung in [!UICONTROL Cloud Manager] im Rahmen des Onboardings für Adobe Managed Services.

Im Rahmen des Onboarding-Prozesses erhalten Sie eine Begrüßungs-E-Mail mit folgenden Informationen:

* Die URL für den Zugriff auf [!UICONTROL Cloud Manager]
* Anleitung zur Anmeldung bei [!UICONTROL Experience Cloud]
* Anweisungen zur Verwendung der Admin Console für die Verwaltung Ihrer Anwender und der entsprechenden Berechtigungen, damit sie, falls erforderlich, auf [!UICONTROL Cloud Manager] zugreifen können.

### Bestehender Adobe Managed Services-Kunde {#existing-customer}

Als bestehender AMS-Kunde benötigen Sie zunächst ein Upgrade Ihrer vorhandenen Produktions- und produktionsfremden Umgebungen auf Version AEM 6.4 oder höher.

Wenn Sie das Upgrade durchführen, werden Sie in Cloud Manager eingeführt und erhalten die URL für den Zugriff auf [!UICONTROL Cloud Manager]. Außerdem müssen Sie für die Anwender, die auf [!UICONTROL Cloud Manager] zugreifen müssen, die Admin Console verwenden, um sie und ihre jeweiligen Berechtigungen zu verwalten.

Auch vorhandene AEM-Projekte müssen Best-Practice-Verfahren entsprechen, wenn Sie mit [!UICONTROL Cloud Manager] neue Code-Änderungen in Ihren AEM-Umgebungen bereitstellen.

Weitere Informationen zu den Vorteilen der Aktualisierung auf AEM 6.5 finden Sie im Dokument [Aktualisieren auf AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html?lang=de) .

## Zugriff auf [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Für den Zugriff auf [!UICONTROL Cloud Manager] und Ihre AEM-Umgebungen müssen Sie sich lediglich auf der [!UICONTROL Experience Cloud]-Landingpage mit Ihren Adobe Identity Management-Anmeldedaten anmelden und im Solution Switcher „AEM“ auswählen.

Nach der erstmaligen Anmeldung bei [!UICONTROL Cloud Manager] können Sie direkt über die [!UICONTROL Cloud Manager]-Benutzeroberfläche auf Ihre AEM-Umgebungen zugreifen. Jetzt sind Sie bereit, alle Möglichkeiten von [!UICONTROL Cloud Manager] zu erkunden und Ihre erste Code-Verzweigung vorzubereiten, um sie in Ihren Staging- und Produktionsumgebungen bereitzustellen.

Die ersten Schritte mit [!UICONTROL Cloud Manager] finden Sie im Dokument [Erstmalige Anmeldung](/help/getting-started/first-time-login.md) beschrieben.

Weitere Informationen zu AEM finden Sie im Dokument [Bereitstellen und Verwalten](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=de) .

## Erste Schritte mit [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Sobald Sie bei [!UICONTROL Cloud Manager] angemeldet sind, können Sie mit Ihrem AEM-Projekt beginnen, indem Sie:

1. Ihre Code-Repository-Umgebung einrichten.
1. Ihr Team und die Rollen einrichten.
   * Rollenmitgliedschaften werden zugewiesen, indem der Anwender über die Admin Console zu einem [!UICONTROL Cloud Manager]-Profil hinzugefügt wird.
1. Ihre Quell-Code-Verzweigungen im Git-Repository einrichten.
1. Ihre Ziele in Bezug auf Last- und Performance-KPIs definieren.
1. Testszenarien definieren, um Ihren Code erfolgreich in Ihrer Staging- und Produktionsumgebung bereitzustellen, sobald alle Qualitätsprüfungen erfolgreich abgeschlossen wurden.

## End-to-End-Journey {#end-to-end-journey}

Dieses Diagramm veranschaulicht die Customer Journey auf einer allgemeinen Ebene, wenn Sie die [!UICONTROL Cloud Manager]-CI/CD-Pipeline für die Bereitstellung Ihrer Codeänderungen in Ihren Staging- und Produktionsumgebungen verwenden.

![End-to-End-Journey](/help/assets/screen_shot_2018-05-15at124004pm.png)
