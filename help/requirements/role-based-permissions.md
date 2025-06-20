---
title: Rollenbasierte Berechtigungen
description: Erfahren Sie mehr über die vorkonfigurierten rollenbasierten Berechtigungen von Cloud Manager für die Verwaltung des Zugriffs auf Ihre Cloud-Ressourcen.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 99%

---


# Rollenbasierte Berechtigungen {#role-based-permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das Git-Repository zu übertragen. Eine Geschäftsinhaberin oder ein Geschäftsinhaber verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

>[!NOTE]
>
>In dieser Dokumentation werden rollenbasierte Berechtigungen für Cloud Manager für Adobe Managed Services (AMS) beschrieben.
>
>Die entsprechende Dokumentation für AEM as a Cloud Service finden Sie unter [Einführung in Cloud Manager](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction#role-based-permissions) in der Dokumentation zu AEM as a Cloud Service.

## Benutzerrollen {#user-roles}

Die Rollen für [!UICONTROL Cloud Manager] werden in [Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html) verwaltet. Jede Benutzerin und jeder Benutzer von [!UICONTROL Cloud Manager] muss Mitglied der kundenseitigen IMS-Organisation sein und über den Adobe Managed Services-Produktkontext verfügen. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem die Benutzerin bzw. der Benutzer in der Admin Console einem [!UICONTROL Cloud Manager]-Produktprofil hinzugefügt wird.

Weitere Informationen zum Einrichten von Rollen finden Sie unter [Einrichten von Benutzenden und Rollen](/help/requirements/users-and-roles.md).

In der folgenden Tabelle sind die Rollen aufgeführt, die Sie in Admin Console zuweisen können.

| [!UICONTROL Cloud Manager]-Rolle | Beschreibung |
|---|---|
| Geschäftsinhaber | Die oder der primäre Benutzende, die bzw. der die [!UICONTROL Cloud Manager]-Ersteinrichtung durchführt und für das Definieren von KPIs, Genehmigen von Produktionsbereitstellungen und ggf. Überschreiben gravierender 3-Tier-Fehler verantwortlich ist. |
| Inhaltsautorin oder -autor | Diese bzw. dieser Benutzende interagiert im Allgemeinen nicht mit Cloud Manager, kann aber den Cloud Manager-Programmumschalter verwenden (aus Experience Cloud kommend), um auf Adobe Experience Manager (AEM) zuzugreifen. |
| Customer Success Engineer | Diese bzw. dieser Benutzende unterstützt in erster Linie den AMS Customer Success und interagiert mit [!UICONTROL Cloud Manager], um Bereitstellungen auszuführen. Diese Bereitstellungen erfordern die Überwachung durch ein Mitglied des Customer Success Engineer(CSE)-Teams von Adobe. |
| Bereitstellungs-Manager | Diese Person verwaltet die Bereitstellungsvorgänge mit [!UICONTROL Cloud Manager], um Staging- und Produktionsbereitstellungen durchzuführen, kann ggf. gravierende 3-Tier-Fehler genehmigen und hat Zugriff auf das Git-Repository. |
| Entwicklerin oder Entwickler | Diese Person entwickelt und testet benutzerdefinierten Anwendungs-Code, verwendet [!UICONTROL Cloud Manager] hauptsächlich zur Anzeige des Bereitstellungsstatus und hat Commit-Zugriff auf das Git-Repository. |
| Programm-Manager | Diese bzw. dieser Benutzende verwendet [!UICONTROL Cloud Manager], um Teams einzurichten, den Status zu überprüfen, KPIs einzusehen und ggf. gravierende 3-Tier-Fehler zu genehmigen. |

## Benutzerberechtigungen {#user-permissions}

Jede der Rollen verfügt über bestimmte vorkonfigurierte Berechtigungen. In der folgenden Tabelle sind die verfügbaren Berechtigungen sowie die Rollen, die diese ausführen können, aufgeführt.

| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungs-Manager | Programm-Manager | Entwicklerin oder Entwickler | CSE |
| --- | --- | --- | --- | --- | --- | --- |
| `Read the Application` | Lesen der Programm-KPIs | x | x | x | x | x |
| `Write Application` | Programm einrichten oder bearbeiten | x | | | | |
| `Add Program` | Neues Programm hinzufügen | x |  |  |  |  |
| `Read Environment` | Siehe Umgebungsdetails | x | x | x | x | x |
| `Create Execution` | Starten der Pipeline | x | x | x | | |
| `Read Execution` | Siehe Ausführungsstatus | x | x | x | x | x |
| `Resume Execution` | Möglichkeit der Wiederaufnahme der Ausführung bei Pause | x | x | x | | x |
| `Execution Approve Deploy to Production` | Go-Live-Genehmigung erteilen | x | x | x | | |
| `Execution Schedule Deploy to Production` | Bereitstellung für die Produktion planen | x | x | x | | x |
| `Execution Deploy to Production` | Anwendung für die Produktion bereitstellen, wenn diese zwecks CSE-Aufsicht angehalten wurde |  |  |  |  | x |
| `Execution Cancel` | Abbrechen der aktuellen Ausführung |  |  | x |  |  |
| `Execution Override Quality Gate Failures` | Bedeutende Quality-Gate-Fehler genehmigen | x | x | x |  |  |
| `Pipeline Create` | Pipeline einrichten/bearbeiten |  | x |  |  |  |
| `Pipeline Read` | Siehe Pipeline-Details | x | x | x | x | x |
| `Pipeline Write` | Pipeline einrichten/bearbeiten |  | x |  |  |  |
| P`ipeline Modify Approval` | Berechtigung zum Bearbeiten der Option „Geschäftsinhaber“ |  | x |  |  |  |
| `Pipeline Modify Managed Deployment` | Berechtigung zum Bearbeiten der Option „CSE-Aufsicht“ |  | x |  |  |  |
| `Pipeline Delete` | Berechtigung zum Löschen der Pipeline |  | x |  |  |  |
| `Step Read` | Siehe Ergebnis des Schritts „Qualitätsmetriken“ | x | x | x | x | x |
| `Generate Personal Access Token` | Zugriff auf Git |  | x |  | x |  |

<!-- CQDOC-22080 | Download log files  |  |  | x |  | x |  | -->

Weitere Informationen zum Einrichten von Benutzenden finden Sie unter [Einrichten von Benutzenden und Rollen](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Es sind auch benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen verfügbar. Weitere Informationen finden Sie unter [Benutzerdefinierte Berechtigungen](/help/using/custom-permissions.md).
