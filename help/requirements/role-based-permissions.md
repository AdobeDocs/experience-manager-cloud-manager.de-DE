---
title: Rollenbasierte Berechtigungen
description: Erfahren Sie mehr über die vorkonfigurierten rollenbasierten Berechtigungen von Cloud Manager für die Verwaltung des Zugriffs auf Ihre Cloud-Ressourcen.
exl-id: b66533fb-db93-40e8-919d-581261fdbf24
source-git-commit: 1c0c3a751ba2023fc2c2dd5d0d54f914373ad95b
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 97%

---


# Rollenbasierte Berechtigungen {#role-based-permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das Git-Repository zu übertragen. Ein Geschäftsinhaber verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

>[!NOTE]
>
>In dieser Dokumentation werden rollenbasierte Berechtigungen für Cloud Manager für Adobe Managed Services (AMS) beschrieben.
>
>Die entsprechende Dokumentation für AEM as a Cloud Service finden Sie unter [Einführung in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/concepts/cloud-manager-introduction.html#role-based-permissions?lang=de) in der Dokumentation zu AEM as a Cloud Service.

## Anwenderrollen {#user-roles}

Die Rollenverwaltung für [!UICONTROL Cloud Manager] erfolgt in der [Admin Console.](https://helpx.adobe.com/de/enterprise/using/admin-console.html) Jede Anwenderin und jeder Anwender von [!UICONTROL Cloud Manager] muss Mitglied der IMS-Organisation des Kunden sein und über den Adobe Managed Services-Produktkontext verfügen. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem die Anwendering bzw. der Anwender in der Admin Console einem [!UICONTROL Cloud Manager]-Produktprofil hinzugefügt wird.

Weitere Informationen zum Einrichten von Rollen finden Sie im Dokument [Einrichten von Anwendern und Rollen](/help/requirements/users-and-roles.md).

In dieser Tabelle sind die Rollen aufgeführt, die Sie in der Admin Console zuweisen können.

| [!UICONTROL Cloud Manager]-Rolle | Beschreibung |
|---|---|
| Geschäftsinhaber | Dies ist der primäre Anwender, der die anfängliche Einrichtung von [!UICONTROL Cloud Manager] durchführt und für die Definition von KPIs, die Genehmigung von Produktionsbereitstellungen und das Überschreiben gravierender 3-Tier-Fehler verantwortlich ist, falls erforderlich. |
| Programm-Manager | Dieser Anwender nutzt [!UICONTROL Cloud Manager], um die Einrichtung von Teams vorzunehmen, den Status zu überprüfen, KPIs einzusehen und ggf. gravierende 3-Tier-Fehler zu genehmigen. |
| Bereitstellungs-Manager | Dieser Anwender verwaltet die Bereitstellungsvorgänge mit [!UICONTROL Cloud Manager], um Staging- und Produktionsbereitstellungen durchzuführen, kann bei Bedarf gravierende 3-Tier-Fehler genehmigen und hat Zugriff auf das Git-Repository. |
| Entwickler | Dieser Anwender entwickelt und testet benutzerdefinierten Anwendungs-Code, verwendet [!UICONTROL Cloud Manager] hauptsächlich zur Anzeige des Bereitstellungsstatus und hat Commit-Zugriff auf das Git-Repository. |
| Customer Success Engineer | Dieser Anwender unterstützt im Allgemeinen den Kundenerfolg für AMS-Kunden und interagiert mit [!UICONTROL Cloud Manager], um Bereitstellungen durchzuführen, die die Aufsicht des Customer Success Engineer (CSE) erfordern. |
| Inhaltsautor | Dieser Anwender interagiert im Allgemeinen nicht mit [!UICONTROL Cloud Manager], kann aber das [!UICONTROL Cloud Manager]-Programm switcher verwenden (von [!UICONTROL Experience Cloud] kommend), um auf Adobe Experience Manager (AEM) zuzugreifen. |

## Benutzerberechtigungen {#user-permissions}

Jede der Rollen verfügt über bestimmte vorkonfigurierte Berechtigungen. In der folgenden Tabelle sind die verfügbaren Berechtigungen aufgelistet, sowie die Rollen, die sie ausführen können.


| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungs-Manager | Programm-Manager | Entwickler | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Anwendung lesen | Lesen der Programm-KPIs | x | x | x | x | x |
| Anwendung schreiben | Programmeinrichtung oder -bearbeitung | x |  |  |  |  |
| Programm hinzufügen | Neues Programm hinzufügen | x |  |  |  |  |
| Umgebung lesen | Siehe Umgebungsdetails | x | x | x | x | x |
| Ausführung erstellen | Starten der Pipeline | x | x | x |  |  |
| Ausführung lesen | Siehe Ausführungsstatus | x | x | x | x | x |
| Ausführung fortsetzen | Kann die Ausführung fortsetzen, wenn sie angehalten wurde | x | x | x |  | x |
| Ausführung, Bereitstellung für die Produktion genehmigen | Go-Live-Genehmigung erteilen | x | x | x |  |  |
| Ausführung, Bereitstellung für die Produktion planen | Bereitstellung für die Produktion planen | x | x | x |  | x |
| Ausführung für die Produktion bereitstellen | Anwendung für die Produktion bereitstellen, wenn diese zwecks CSE-Aufsicht angehalten wurde |  |  |  |  | x |
| Ausführung abbrechen | Abbrechen der aktuellen Ausführung |  |  | x |  |  |
| Ausführung, Quality-Gate-Fehler außer Kraft setzen | Bedeutende Quality-Gate-Fehler genehmigen | x | x | x |  |  |
| Pipeline erstellen | Pipeline einrichten/bearbeiten |  | x |  |  |  |
| Pipeline lesen | Siehe Pipeline-Details | x | x | x | x | x |
| Pipeline schreiben | Pipeline einrichten/bearbeiten |  | x |  |  |  |
| Pipeline ändern, Genehmigung | Berechtigung zum Bearbeiten der Option „Geschäftsinhaber“ |  | x |  |  |  |
| Pipeline ändern, verwaltete Bereitstellung | Berechtigung zum Bearbeiten der Option „CSE-Aufsicht“ |  | x |  |  |  |
| Pipeline löschen | Berechtigung zum Löschen der Pipeline |  | x |  |  |  |
| Schritt lesen | Siehe Ergebnis des Schritts „Qualitätsmetriken“ | x | x | x | x | x |
| Persönliches Zugriffs-Token erstellen | Zugriff auf Git |  | x |  | x |  |

Weitere Informationen zum Einrichten von Anwendern finden Sie im Dokument [Einrichten von Anwendern und Rollen](/help/requirements/users-and-roles.md).

>[!TIP]
>
>Auch benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen sind verfügbar. Lesen Sie das Dokument . [Benutzerdefinierte Berechtigungen](/help/using/custom-permissions.md) für weitere Details.
