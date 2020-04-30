---
title: Rollenbasierte Berechtigungen
description: Auf dieser Seite finden Sie Informationen zu rollenbasierten Berechtigungen.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 9cbe8f58cf04001ba9851ba321f03c7687e58014

---


# Rollenbasierte Berechtigungen {#role-based-permissions}

[!UICONTROL Cloud Manager] hat vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das **Git-Repository** zu übertragen. Ein Business Owner verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

## Anwenderrollen {#user-roles}

Die Rollenverwaltung für [!UICONTROL Cloud Manager] erfolgt in [Adobe Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html). Jeder Anwender von [!UICONTROL Cloud Manager] muss Mitglied der IMS-Organisation des Kunden sein und über den Adobe Managed Services-Produktkontext verfügen. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem der Anwender in Admin Console einem [!UICONTROL Cloud Manager]-Produktprofil hinzugefügt wird.

Weitere Informationen zum Einrichten von Rollen finden Sie unter [Einrichten von Anwendern und Rollen](setting-up-users-and-roles.md).

In der folgenden Tabelle sind die Rollen definiert, die Sie in Admin Console zuweisen können.

| **[!UICONTROL Cloud Manager]Rolle ** | **Beschreibung** |
|---|---|
| Business Owner | Primary user who completes the initial [!UICONTROL Cloud Manager] setup. Verantwortlich für die Definition von KPIs, Genehmigung von Produktionsbereitstellungen und Außerkraftsetzung bedeutender 3-Tier-Fehler. |
| Programmmanager | Verwendet [!UICONTROL Cloud Manager], um Teams einzurichten, den Status zu überprüfen und KPIs anzuzeigen. Kann bedeutende 3-Tier-Fehler genehmigen. |
| Bereitstellungsmanager | Verwaltet Bereitstellungsvorgänge. Uses [!UICONTROL Cloud Manager] to execute stage and production deployments. Kann bedeutende 3-Tier-Fehler genehmigen. Hat Zugriff auf das Git-Repository. |
| Entwickler | Entwickelt und testet anwenderspezifischen Anwendungscode. Primarily uses [!UICONTROL Cloud Manager] to view status. Hat Commitzugriff auf das Git-Repository. |
| Customer Success Engineer | Unterstützt im Allgemeinen den Erfolg von AMS-Kunden. Interagiert mit [!UICONTROL Cloud Manager], um Bereitstellungen auszuführen, die von einem CSE (Customer Success Engineer) überwacht werden müssen. |
| Inhaltsautor | Generally does not interact with [!UICONTROL Cloud Manager]. This user may use the [!UICONTROL Cloud Manager] Program Switcher (having navigated from [!UICONTROL Experience Cloud]) to access Adobe Experience Manager (AEM). |

## Anwenderberechtigungen {#user-permissions}

Jede Rolle verfügt über bestimmte Berechtigungen, vorkonfigurierte Aufgaben oder Berechtigungen, die jeder Rolle zugeordnet sind. In der folgenden Tabelle sind die verfügbaren Funktionen und Rollen aufgelistet, die die Funktion ausführen können.

Weitere Informationen zum Einrichten von Anwendern finden Sie unter [Einrichten von Anwendern und Rollen](setting-up-users-and-roles.md).

| Berechtigung | Beschreibung | Business Owner | Bereitstellungsmanager | Programmmanager | Entwickler | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Anwendung lesen | Lesen der Programm-KPIs. | x | x | x | x | x |
| Anwendung schreiben | Programmeinrichtung oder -bearbeitung. | x |  |  |  |  |
| Programm hinzufügen | Neues Programm hinzufügen. | x |  |  |  |  |
| Umgebung lesen | Siehe Umgebungsdetails. | x | x | x | x | x |
| Ausführung erstellen | Starten der Pipeline. | x | x | x |  |  |
| Ausführung lesen | Siehe Ausführungsstatus. | x | x | x | x | x |
| Ausführung fortsetzen | Kann die Ausführung fortsetzen, wenn sie angehalten wurde. | x | x | x |  | x |
| Ausführung, Bereitstellung für die Produktion genehmigen | Bereitstellen der GoLive-Genehmigung. | x | x | x |  |  |
| Ausführung, Bereitstellung für die Produktion planen | Planen der Bereitstellung für die Produktion. | x | x | x |  | x |
| Ausführung für die Produktion bereitstellen | Bereitstellen der Anwendung für die Produktion, wenn diese zwecks CSE-Überwachung angehalten wurde. |  |  |  |  | x |
| Ausführung abbrechen | Abbrechen der aktuellen Ausführung. |  |  | x |  |  |
| Ausführung, Quality-Gate-Fehler außer Kraft setzen | Genehmigen bedeutender Quality-Gate-Fehler. | x | x | x |  |  |
| Pipeline erstellen | Einrichten/Bearbeiten der Pipeline. |  | x |  |  |  |
| Pipeline lesen | Siehe Pipelinedetails. | x | x | x | x | x |
| Pipeline schreiben | Einrichten/Bearbeiten der Pipeline. |  | x |  |  |  |
| Pipeline ändern, Genehmigung | Berechtigung zum Bearbeiten der Option „Business Owner“. |  | x |  |  |  |
| Pipeline ändern, Managed Deployment | Berechtigung zum Bearbeiten der Option „CSE-Überwachung“. |  | x |  |  |  |
| Pipeline löschen | Ermöglicht das Löschen einer Pipeline. |  | x |  |  |  |
| Schritt lesen | Siehe Ergebnis des Schritts „Qualitätsmetriken“. | x | x | x | x | x |
| Persönliches Zugriffs-Token erstellen | Zugriff auf Git. |  | x |  | x |  |

