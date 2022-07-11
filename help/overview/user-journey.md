---
title: Journey
description: In diesem Dokument werden die verschiedenen Onboarding-Szenarien beschrieben und Ihre ersten Schritte zum Journey mit Cloud Manager erläutert.
exl-id: deb3429c-dfcf-4e52-9aba-d9368aa240e6
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 11%

---


# Journey {#user-journey}

Als Adobe Experience Manager-Benutzer haben Sie folgende Möglichkeiten:

* Sei neu zu AEM.
* Verwenden Sie derzeit AEM 6.x.
* Sie müssen auf AEM Version 6.5 aktualisieren, um [!UICONTROL Cloud Manager].

In diesem Dokument werden diese Szenarien erläutert und Ihre Journey erläutert, um mit [!UICONTROL Cloud Manager].

>[!NOTE]
>
>[!UICONTROL Cloud Manager] ist nur für Adobe Managed Services-Kunden (AMS) mit AEM 6.4 oder höher verfügbar.

## Einstieg  {#onboarding}

Der Integrationsprozess unterscheidet sich je nachdem, ob Sie neu bei AMS sind oder ein bestehender AMS-Kunde sind.

### Neu bei Adobe Managed Services {#new-to-ams}

Als neuer Kunde sind Sie bei [!UICONTROL Cloud Manager] als Teil des Onboarding-Prozesses für Adobe Managed Services.

Im Rahmen des Onboarding-Prozesses erhalten Sie eine Begrüßungs-E-Mail mit folgenden Informationen:

* Die URL für den Zugriff [!UICONTROL Cloud Manager]
* Anleitung zur Anmeldung bei [!UICONTROL Experience Cloud]
* Anweisungen zur Verwendung der Admin Console für die Verwaltung Ihrer Benutzer und der entsprechenden Berechtigungen, damit sie darauf zugreifen können [!UICONTROL Cloud Manager] falls erforderlich.

### Bestehender Adobe Managed Services-Kunde {#existing-customer}

Als bestehender AMS-Kunde müssen Sie zunächst Ihre bestehenden Produktions- und Nicht-Produktionsumgebungen auf AEM 6.4 oder höher aktualisieren.

Während der Aktualisierung werden Sie in Cloud Manager integriert und über die URL für den Zugriff auf [!UICONTROL Cloud Manager]. Zusätzlich für die Benutzer, die auf [!UICONTROL Cloud Manager]müssen Sie die Admin Console verwenden, um sie und ihre jeweiligen Berechtigungen zu verwalten.

Auch vorhandene AEM-Projekte müssen Best-Practice-Verfahren entsprechen, wenn Sie mit [!UICONTROL Cloud Manager] neue Code-Änderungen in Ihren AEM-Umgebungen bereitstellen.

Weitere Informationen zu den Vorteilen der Aktualisierung auf AEM 6.5 finden Sie im Dokument [Upgrade auf AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/upgrade.html)

## Zugriff auf [!UICONTROL Cloud Manager] {#accessing-cloud-manager}

Sie erhalten Zugriff auf [!UICONTROL Cloud Manager] und Ihre AEM Umgebungen, indem Sie sich einfach bei der [!UICONTROL Experience Cloud] Landingpage mit Ihren Adobe Identity Management-Anmeldedaten und Auswahl von AEM in der Lösungsmenü.

Nach der erstmaligen Anmeldung bei [!UICONTROL Cloud Manager] können Sie direkt über die [!UICONTROL Cloud Manager]-Benutzeroberfläche auf Ihre AEM-Umgebungen zugreifen. An dieser Stelle sind Sie bereit, alle Möglichkeiten von [!UICONTROL Cloud Manager] und bereiten Sie Ihre erste Codeverzweigung vor, die in Ihrer Staging- und Produktionsumgebung bereitgestellt werden soll.

Erste Schritte mit [!UICONTROL Cloud Manager], siehe Dokument [Erstmalige Anmeldung](/help/getting-started/first-time-login.md).

Weitere Informationen zu AEM finden Sie im Dokument . [Bereitstellung und Wartung](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html)

## Erste Schritte mit [!UICONTROL Cloud Manager] {#getting-started-with-cloud-manager}

Nachdem Sie sich bei [!UICONTROL Cloud Manager] Sie können mit Ihrem AEM-Projekt beginnen, indem Sie:

1. Einrichten der Code-Repository-Umgebung.
1. Einrichten des Teams und der Rollen
   * Rollenmitgliedschaften werden zugewiesen, indem der Benutzer zu einem [!UICONTROL Cloud Manager] Profil mit der Admin Console.
1. Einrichten der Quellcodeverzweigungen im Git-Repository.
1. Definieren Ihrer Ziele in Bezug auf Last- und Performance-KPIs.
1. Definieren von Testszenarien, um Ihren Code erfolgreich in Ihrer Staging- und Produktionsumgebung bereitzustellen, sobald alle Qualitätsprüfungen erfolgreich abgeschlossen wurden.

## End-to-End-Journey {#end-to-end-journey}

Dieses Diagramm veranschaulicht die Journey auf hoher Ebene bei der Verwendung von [!UICONTROL Cloud Manager] CI/CD-Pipeline zur Bereitstellung Ihrer Codeänderungen in Ihren Staging- und Produktionsumgebungen.

![End-to-End-Journey](/help/assets/screen_shot_2018-05-15at124004pm.png)
