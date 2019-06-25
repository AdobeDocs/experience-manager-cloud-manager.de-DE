---
title: Sicherheit und Datenschutz
seo-title: Sicherheit und Datenschutz für AEM Cloud Manager
description: Auf dieser Seite erfahren Sie mehr zum Thema Sicherheit und Datenschutz von Assets (Code/Artefakten).
seo-description: Auf dieser Seite erfahren Sie mehr zum Thema Sicherheit und Datenschutz von Assets (Code/Artefakten) bei Verwendung von AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: Einführung
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: ht
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Sicherheit und Datenschutz {#security-and-privacy}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das **Git-Repository** zu übertragen. Ein Business Owner verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

## Rollenbasierte Berechtigungen {#role-based-permissions}

### Anwenderrollen {#user-roles}

Die Rollenverwaltung für [!UICONTROL Cloud Manager] erfolgt in [Adobe Admin Console](https://helpx.adobe.com/enterprise/using/admin-console.html). Jeder Anwender von [!UICONTROL Cloud Manager] muss Mitglied der IMS-Organisation des Kunden sein und über den Adobe Managed Services-Produktkontext verfügen. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem der Anwender in Admin Console einem [!UICONTROL Cloud Manager]-Produktprofil hinzugefügt wird.

Weitere Informationen zum Einrichten von Rollen finden Sie unter [Einrichten von Anwendern und Rollen](setting-up-users-and-roles.md).

In der folgenden Tabelle sind die Rollen definiert, die Sie in Admin Console zuweisen können.

| **[!UICONTROL Cloud Manager]-Rolle** | **Beschreibung** |
|---|---|
| Business Owner | Hauptanwender, der die [!UICONTROL Cloud Manager]-Ersteinrichtung abschließt. Verantwortlich für die Definition von KPIs, Genehmigung von Produktionsbereitstellungen und Außerkraftsetzung bedeutender 3-Tier-Fehler. |
| Programmmanager | Verwendet [!UICONTROL Cloud Manager], um Teams einzurichten, den Status zu überprüfen und KPIs anzuzeigen. Kann bedeutende 3-Tier-Fehler genehmigen. |
| Bereitstellungsmanager | Verwaltet Bereitstellungsvorgänge. Kann mit [!UICONTROL Cloud Manager] Staging- und Produktionsbereitstellungen ausführen. Kann bedeutende 3-Tier-Fehler genehmigen. Hat Zugriff auf das Git-Repository. |
| Entwickler | Entwickelt und testet anwenderspezifischen Anwendungscode. Nutzt [!UICONTROL Cloud Manager] hauptsächlich, um den Status anzuzeigen. Hat Commitzugriff auf das Git-Repository. |
| Customer Success Engineer | Unterstützt im Allgemeinen den Erfolg von AMS-Kunden. Interagiert mit [!UICONTROL Cloud Manager], um Bereitstellungen auszuführen, die von einem CSE (Customer Success Engineer) überwacht werden müssen. |
| Inhaltsautor | Interagiert im Allgemeinen nicht mit [!UICONTROL Cloud Manager]. Dieser Anwender kann über den [!UICONTROL Cloud Manager]-Programmumschalter (nach Navigation über [!UICONTROL Experience Cloud]) auf Adobe Experience Manager (AEM) zugreifen. |

### Anwenderberechtigungen {#user-permissions}

Jede Rolle verfügt über bestimmte Berechtigungen, vorkonfigurierte Aufgaben oder Berechtigungen, die jeder Rolle zugeordnet sind. In der folgenden Tabelle sind die verfügbaren Funktionen und Rollen aufgelistet, die die Funktion ausführen können.

Weitere Informationen zum Einrichten von Anwendern finden Sie unter [Einrichten von Anwendern und Rollen](setting-up-users-and-roles.md).

| Berechtigung | Beschreibung | Business Owner | Bereitstellungsmanager | Programmmanager | Entwickler | CSE |
|--- |--- |--- |--- |--- |--- |--- |
| Anwendung lesen | Siehe Details des Programms. | x | x | x | x | x |
| Anwendung schreiben | Konfigurieren des Programms (einschließlich KPIs). | x |  |  |  |  |
| Umgebung lesen | Siehe Umgebungsdetails. | x | x | x | x | x |
| Ausführung erstellen | Starten der Pipeline. | x | x | x |  |  |
| Ausführung lesen | Siehe Ausführungsstatus. | x | x | x | x | x |
| Ausführung fortsetzen | Kann die Ausführung fortsetzen, wenn sie angehalten wurde. | x | x | x |  | x |
| Ausführung, Bereitstellung für die Produktion genehmigen | Bereitstellen der GoLive-Genehmigung. | x | x | x |  |  |
| Ausführung, Bereitstellung für die Produktion planen | Planen der Bereitstellung für die Produktion. | x | x | x |  | x |
| Ausführung für die Produktion bereitstellen | Bereitstellen der Anwendung für die Produktion, wenn diese zwecks CSE-Überwachung angehalten wurde. |  |  |  |  | x |
| Ausführung abbrechen | Abbrechen der aktuellen Ausführung. | x | x | x |  |  |
| Ausführung, Quality-Gate-Fehler außer Kraft setzen | Genehmigen bedeutender Quality-Gate-Fehler. | x | x | x |  |  |
| Pipeline erstellen | Einrichten/Bearbeiten der Pipeline. |  | x |  |  |  |
| Pipeline lesen | Siehe Pipelinedetails. | x | x | x | x | x |
| Pipeline schreiben | Einrichten/Bearbeiten der Pipeline. |  | x |  |  |  |
| Pipeline ändern, Genehmigung | Berechtigung zum Bearbeiten der Option „Business Owner“. |  | x |  |  |  |
| Pipeline ändern, Managed Deployment | Berechtigung zum Bearbeiten der Option „CSE-Überwachung“. |  | x |  |  |  |
| Lösung lesen | Lesen der Programm-KPIs. | x | x | x | x | x |
| Lösung schreiben | Konfigurieren des Programms (einschließlich KPIs), Einrichten/Bearbeiten der Pipeline. | x |  |  |  |  |
| Schritt lesen | Siehe Ergebnis des Schritts „Qualitätsmetriken“. | x | x | x | x | x |

## Ressourcenisolation {#resource-isolation}

Kunden, die [!UICONTROL Cloud Manager] verwenden, benötigen ihre IMS-Anmeldeinformationen, um sich zu authentifizieren, da alle mit [!UICONTROL Cloud Manager] verbundenen Berechtigungen konfiguriert und an die IMS-Organisation gebunden werden. Während des Onboardingprozesses stellt das Bereitstellungsteam sicher, dass die Ressourcenisolation in [!UICONTROL Cloud Manager] durchgesetzt wird.

## Datensicherheit {#data-security}

Code in [!UICONTROL Cloud Manager] wird während der Übertragung verschlüsselt. Von Cloud Manager erstellte Binärdateien werden ebenfalls während der Übertragung und beim Speichern verschlüsselt.

Alle Kunden erhalten ein eigenes **Git-Repository**. Ihr Code ist sicher und wird nicht an andere **Organisationen** weitergegeben.

## Datenschutz {#data-privacy}

[!UICONTROL Cloud Manager] erfüllt die von Adobe definierten Datenschutzgrundsätze. Entwickler können Code dank HTTPS sicher per Push an das **Git-Repository** übertragen.

Die [!DNL Benutzeroberfläche (User Interface, UI) für [!UICONTROL Cloud Manager]] basiert auf Diensten, die einem gemeinsamen, von Adobe definierten Steuerungsframework entsprechen. Die [!DNL Benutzeroberfläche (User Interface, UI) für [!UICONTROL Cloud Manager]] nutzt sichere Dienste verschiedener Cloudanbieter.
