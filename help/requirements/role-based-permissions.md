---
title: Rollenbasierte Berechtigungen
description: Erfahren Sie mehr über die vorkonfigurierten rollenbasierten Berechtigungen von Cloud Manager für die Verwaltung des Zugriffs auf Ihre Cloud-Ressourcen.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 60%

---


# Rollenbasierte Berechtigungen {#role-based-permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das Git-Repository zu übertragen. Ein Geschäftsinhaber verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

>[!NOTE]
>
>In dieser Dokumentation werden rollenbasierte Berechtigungen für Cloud Manager für Adobe Managed Services (AMS) beschrieben.
>
>Die entsprechende Dokumentation für AEM as a Cloud Service finden Sie unter [Einführung in Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) in der Dokumentation zu AEM as a Cloud Service.

## Benutzerrollen {#user-roles}

Die Rollen für [!UICONTROL Cloud Manager] werden in [Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) verwaltet. Jede Benutzerin und jeder Benutzer von [!UICONTROL Cloud Manager] muss Mitglied der kundenseitigen IMS-Organisation sein und über den Adobe Managed Services-Produktkontext verfügen. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem die Benutzerin bzw. der Benutzer in der Admin Console einem [!UICONTROL Cloud Manager]-Produktprofil hinzugefügt wird.

Weitere Informationen zum Einrichten von Rollen finden Sie unter [Einrichten von Anwendern und Rollen](/help/requirements/users-and-roles.md).

In der folgenden Tabelle sind die Rollen aufgeführt, die Sie in der Admin Console zuweisen können.

| [!UICONTROL Cloud Manager]-Rolle | Beschreibung |
|---|---|
| Geschäftsinhaber | Der primäre Benutzer, der die anfängliche Einrichtung von [!UICONTROL Cloud Manager] abgeschlossen hat und für die Definition von KPIs, die Genehmigung von Produktionsbereitstellungen und das Überschreiben wichtiger 3-Tier-Fehler bei Bedarf zuständig ist. |
| Inhaltsautorin oder -autor | Der Benutzer interagiert im Allgemeinen nicht mit Cloud Manager, kann jedoch den Cloud Manager-Programmumschalter (nach Navigation von Experience Cloud) verwenden, um auf Adobe Experience Manager (AEM) zuzugreifen. |
| Customer Success Engineer | Der Benutzer unterstützt in erster Linie den Erfolg von AMS-Kunden und interagiert mit [!UICONTROL Cloud Manager], um Bereitstellungen auszuführen. Diese Implementierungen erfordern die Überwachung durch einen Adobe Customer Success Engineer (CSE). |
| Bereitstellungs-Manager | Der Benutzer verwaltet die Bereitstellungsvorgänge mit [!UICONTROL Cloud Manager], um Staging- und Produktionsbereitstellungen auszuführen. Er kann bei Bedarf wichtige 3-Tier-Fehler genehmigen und Zugriff auf das Git-Repository haben. |
| Entwicklerin oder Entwickler | Der Benutzer entwickelt und testet benutzerdefinierten Anwendungscode, verwendet hauptsächlich [!UICONTROL Cloud Manager], um den Bereitstellungsstatus anzuzeigen, und hat Commitzugriff auf das Git-Repository. |
| Programm-Manager | Der Benutzer verwendet [!UICONTROL Cloud Manager], um Teams einzurichten, den Status zu überprüfen, KPIs anzuzeigen und ggf. wichtige 3-Tier-Fehler zu genehmigen. |

## Benutzerberechtigungen {#user-permissions}

Jede der Rollen verfügt über spezifische, vorkonfigurierte Berechtigungen. In der folgenden Tabelle sind die verfügbaren Berechtigungen und die Rollen aufgeführt, die sie ausführen können.

| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungs-Manager | Programm-Manager | Entwickler | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| Anwendung lesen | Lesen der Programm-KPIs | x | x | x | x | x |
| Anwendung schreiben | Einrichten oder Bearbeiten von Programmen | x | | | | |
| Programm hinzufügen | Neues Programm hinzufügen | x | | | | |
| Umgebung lesen | Siehe Umgebungsdetails | x | x | x | x | x |
| Ausführung erstellen | Starten der Pipeline | x | x | x | | |
| Ausführung lesen | Siehe Ausführungsstatus | x | x | x | x | x |
| Ausführung fortsetzen | Möglichkeit der Wiederaufnahme der Ausführung bei angehaltener Ausführung | x | x | x | | x |
| Ausführung, Bereitstellung für die Produktion genehmigen | Go-Live-Genehmigung erteilen | x | x | x | | |
| Ausführung, Bereitstellung für die Produktion planen | Bereitstellung für die Produktion planen | x | x | x | | x |
| Ausführung für die Produktion bereitstellen | Anwendung für die Produktion bereitstellen, wenn diese zwecks CSE-Aufsicht angehalten wurde | | | | | x |
| Ausführung abbrechen | Abbrechen der aktuellen Ausführung | | | x | | |
| Ausführung, Quality-Gate-Fehler außer Kraft setzen | Bedeutende Quality-Gate-Fehler genehmigen | x | x | x | | |
| Pipeline erstellen | Pipeline einrichten/bearbeiten | | x | | | |
| Pipeline lesen | Siehe Pipeline-Details | x | x | x | x | x |
| Pipeline schreiben | Pipeline einrichten/bearbeiten | | x | | | |
| Pipeline ändern, Genehmigung | Berechtigung zum Bearbeiten der Option „Geschäftsinhaber“ | | x | | | |
| Pipeline ändern, verwaltete Bereitstellung | Berechtigung zum Bearbeiten der Option „CSE-Aufsicht“ | | x | | | |
| Pipeline löschen | Berechtigung zum Löschen der Pipeline | | x | | | |
| Schritt lesen | Siehe Ergebnis des Schritts „Qualitätsmetriken“ | x | x | x | x | x |
| Persönliches Zugriffs-Token erstellen | Zugriff auf Git | | x | | x | |

Weitere Informationen zum Einrichten von Benutzern finden Sie unter [Einrichten von Anwendern und Rollen](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Es sind auch benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen verfügbar. Weitere Informationen finden Sie unter [Benutzerdefinierte Berechtigungen](/help/using/custom-permissions.md).
