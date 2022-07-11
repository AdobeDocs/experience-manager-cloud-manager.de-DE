---
title: Rollenbasierte Berechtigungen
description: Erfahren Sie mehr über die vorkonfigurierten rollenbasierten Berechtigungen von Cloud Manager für die Verwaltung des Zugriffs auf Ihre Cloud-Ressourcen.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 522e5fbc650a8159602eb1aeaf42d64f4e23e8b4
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 30%

---


# Rollenbasierte Berechtigungen {#role-based-permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise entwickelt ein Entwickler Code und ist berechtigt, den Code an das Git-Repository zu pushen. Ein Business Owner verfügt über unterschiedliche Berechtigungen, mit denen er die wichtigsten Leistungsindikatoren (KPIs) definieren und Bereitstellungen genehmigen kann.

## Anwenderrollen {#user-roles}

Rollenverwaltung [!UICONTROL Cloud Manager] wird mithilfe von [Admin Console.](https://helpx.adobe.com/de/enterprise/using/admin-console.html) Jeder Benutzer von [!UICONTROL Cloud Manager] muss Mitglied der IMS-Organisation des Kunden sein und über den Adobe Managed Services-Produktkontext verfügen. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem der Benutzer zu einem [!UICONTROL Cloud Manager] Produktprofil in der Admin Console.

Weitere Informationen zum Einrichten von Rollen finden Sie im Dokument [Einrichten von Anwendern und Rollen.](/help/requirements/users-and-roles.md)

In dieser Tabelle sind die Rollen aufgeführt, die Sie in der Admin Console zuweisen können.

| [!UICONTROL Cloud Manager]-Rolle | Beschreibung |
|---|---|
| Geschäftsinhaber | Dies ist der primäre Benutzer, der den ersten [!UICONTROL Cloud Manager] und ist für die Definition von KPIs, die Genehmigung von Produktionsbereitstellungen und das Überschreiben wichtiger 3-Tier-Fehler bei Bedarf zuständig. |
| Programm-Manager | Dieser Benutzer verwendet [!UICONTROL Cloud Manager] , um Teams einzurichten, den Status zu überprüfen, KPIs anzuzeigen und wichtige 3-Tier-Fehler bei Bedarf zu genehmigen. |
| Implementierungs-Manager | Dieser Benutzer verwaltet die Bereitstellungsvorgänge mit [!UICONTROL Cloud Manager] um Staging- und Produktionsbereitstellungen auszuführen, kann bei Bedarf wichtige 3-Tier-Fehler genehmigen und Zugriff auf das Git-Repository haben. |
| Entwickler | Dieser Benutzer entwickelt und testet benutzerdefinierten Anwendungs-Code, der hauptsächlich verwendet [!UICONTROL Cloud Manager] , um den Bereitstellungsstatus anzuzeigen und Zugriff auf das Git-Repository zu erhalten. |
| Customer Success Engineer | Dieser Benutzer unterstützt im Allgemeinen den Kundenerfolg für AMS-Kunden und interagiert mit [!UICONTROL Cloud Manager] zum Zwecke der Ausführung von Bereitstellungen, die von einem Customer Success Engineer (CSE) überwacht werden müssen. |
| Inhaltsautor | Dieser Benutzer interagiert im Allgemeinen nicht mit [!UICONTROL Cloud Manager], kann jedoch die [!UICONTROL Cloud Manager] Programm-Wwitcher (nach Navigation von [!UICONTROL Experience Cloud]), um auf Adobe Experience Manager (AEM) zuzugreifen. |

## Benutzerberechtigungen {#user-permissions}

Jede der Rollen verfügt über bestimmte vorkonfigurierte Berechtigungen. In dieser Tabelle sind die verfügbaren Berechtigungen und die Rollen aufgeführt, die sie ausführen können.


| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungs-Manager | Programm-Manager | Entwickler | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Anwendung lesen | Programm-KPIs lesen | x | x | x | x | x |
| Anwendung schreiben | Programmeinrichtung oder -bearbeitung | x |  |  |  |  |
| Programm hinzufügen | Neues Programm hinzufügen | x |  |  |  |  |
| Umgebung lesen | Siehe Umgebungsdetails | x | x | x | x | x |
| Ausführung erstellen | Pipeline starten | x | x | x |  |  |
| Ausführung lesen | Siehe Ausführungsstatus | x | x | x | x | x |
| Ausführung fortsetzen | Kann die Ausführung fortsetzen, wenn sie angehalten wurde | x | x | x |  | x |
| Ausführung, Bereitstellung für die Produktion genehmigen | Go-Live-Genehmigung bereitstellen | x | x | x |  |  |
| Ausführung, Bereitstellung für die Produktion planen | Produktionsbereitstellung planen | x | x | x |  | x |
| Ausführung für die Produktion bereitstellen | Bereitstellen der Anwendung für die Produktion, wenn sie zur CSE-Überwachung angehalten wird |  |  |  |  | x |
| Ausführung abbrechen | Abbrechen der aktuellen Ausführung |  |  | x |  |  |
| Ausführung, Quality-Gate-Fehler außer Kraft setzen | Genehmigen wichtiger Qualitätssicherungsfehler | x | x | x |  |  |
| Pipeline erstellen | Einrichten/Bearbeiten der Pipeline |  | x |  |  |  |
| Pipeline lesen | Siehe Pipeline-Details | x | x | x | x | x |
| Pipeline schreiben | Einrichten/Bearbeiten der Pipeline. |  | x |  |  |  |
| Pipeline ändern, Genehmigung | Ermöglicht die Bearbeitung der Option &quot;Business Owner&quot; |  | x |  |  |  |
| Pipeline ändern, Managed Deployment | Ermöglicht die Bearbeitung der CSE-Überwachungsoption |  | x |  |  |  |
| Pipeline löschen | Ermöglicht das Löschen der Pipeline |  | x |  |  |  |
| Schritt lesen | Ergebnisse der Schrittqualitätsmetriken anzeigen | x | x | x | x | x |
| Persönliches Zugriffs-Token erstellen | Git-Zugriff |  | x |  | x |  |

Weitere Informationen zum Einrichten von Benutzern finden Sie im Dokument . [Einrichten von Anwendern und Rollen.](/help/requirements/users-and-roles.md)
