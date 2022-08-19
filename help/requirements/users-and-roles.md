---
title: Hinzufügen von Anwendern und Rollen
description: Erfahren Sie, wie Sie mit der Admin Console Anwender und Rollen hinzufügen und Profile erstellen können.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: ht
source-wordcount: '581'
ht-degree: 100%

---


# Hinzufügen von Anwendern und Rollen {#add-users-and-roles}

Für viele Funktionen in [!UICONTROL Cloud Manager] sind spezielle Berechtigungen erforderlich. Beispielsweise dürfen nur bestimmte Anwender die KPIs (Key Performance Indicators) für ein Programm festlegen. Diese Berechtigungen werden logisch in Rollen gruppiert.

In [!UICONTROL Cloud Manager] sind derzeit vier Rollen für Anwender definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Geschäftsinhaber
* Programm-Manager
* Implementierungs-Manager
* Entwickler

>[!NOTE]
>
>Um [!UICONTROL Cloud Manager] verwenden zu können, müssen Sie über eine Adobe ID und den Adobe Managed Services-Produktkontext verfügen.

## Rollendefinitionen {#role-definitions}

Diese Tabelle fasst die Rollen zusammen.

| [!UICONTROL Cloud Manager]-Rolle | Beschreibung |
|--- |--- |
| Geschäftsinhaber | Dieser Anwender ist verantwortlich für die Definition von KPIs, die Genehmigung von Produktionbereitstellungen und das Überschreiben von gravierenden 3-Tier-Fehlern, falls erforderlich. |
| Programm-Manager | Dieser Anwender nutzt [!UICONTROL Cloud Manager], um die Einrichtung von Teams vorzunehmen, den Status zu überprüfen, KPIs einzusehen und ggf. gravierende 3-Tier-Fehler zu genehmigen. |
| Implementierungs-Manager | Dieser Anwender verwaltet die Bereitstellungsvorgänge mit [!UICONTROL Cloud Manager], um Staging- und Produktionsbereitstellungen durchzuführen, CI/CD-Pipeline zu bearbeiten, kann bei Bedarf gravierende 3-Tier-Fehler genehmigen und hat Zugriff auf das Git-Repository. |
| Entwickler | Dieser Anwender entwickelt und testet benutzerdefinierten Anwendungscode, verwendet [!UICONTROL Cloud Manager] hauptsächlich zur Anzeige des Bereitstellungsstatus und für Code-Commits auf das Git-Repository zugreifen. |
| Customer Success Engineer | Dieser Anwender unterstützt im Allgemeinen den Kundenerfolg für AMS-Kunden und interagiert mit [!UICONTROL Cloud Manager], um Bereitstellungen durchzuführen, die die Aufsicht des Customer Success Engineer (CSE) erfordern. |
| Inhaltsautor | Dieser Anwender interagiert im Allgemeinen nicht mit [!UICONTROL Cloud Manager], kann aber das [!UICONTROL Cloud Manager]-Programm switcher verwenden, um auf Adobe Experience Manager (AEM) zuzugreifen. |

>[!NOTE]
>
>Die Entwicklerrolle in der Admin Console hat nichts mit der Entwicklerrolle in [!UICONTROL Cloud Manager] zu tun.

## Erstellen von Profilen mit der Admin Console {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager]-Rollen werden über die Admin Console verwaltet. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem der Anwender einem [!UICONTROL Cloud Manager]-Produktprofil hinzugefügt wird.

Die Admin Console ermöglicht eine zentrale Verwaltung Ihrer Adobe-Berechtigungen in der gesamten Organisation. Weitere Informationen zur Adobe Admin Console finden Sie in der Dokumentation zur [Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html).

>[!NOTE]
>
>Um auf die Admin Console zuzugreifen und Ihr Team (Anwender und Rollen) einzurichten, besuchen Sie [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Um die entsprechenden rollenbasierten Berechtigungen für [!UICONTROL Cloud Manager]-Anwender bereitzustellen, muss ein Administrator in der Organisation des Kunden neue Produktprofile unter dem [!UICONTROL AEM Managed Services]-Produktkontext für jede der vier [!UICONTROL Cloud Manager]-Rollen erstellen:

* Geschäftsinhaber
* Implementierungs-Manager
* Entwickler
* Programm-Manager

Mit der Admin Console können Sie Anwender/Gruppen für diese Produktprofile erstellen oder hinzufügen.

1. Melden Sie sich bei Admin Console an und klicken Sie auf **Neues Profil**, um ein neues Profil hinzuzufügen.

   ![Neues Profil](/help/assets/admin_console_roles-1.png)

1. Tragen Sie die Informationen ein, um eine neue Rolle für [!UICONTROL Cloud Manager] einzurichten.

   * **Profilname**
   * **Anzeigename**
   * **Berechtigungsgruppe**

1. Klicken Sie auf **Fertig**, um die Profilerstellung abzuschließen.

Beim Erstellen dieser Produktprofile muss der **Anzeigename** dem von [!UICONTROL Cloud Manager] definierten technischen Wert entsprechen (siehe Tabelle unten). Der **Profilname** ist beliebig. Um Verwirrungen zu vermeiden, sollten Sie jedoch die Werte in der unten stehenden Spalte **Empfohlener Profilname** verwenden. Deaktivieren Sie dazu beim Erstellen des Produktprofils die Option **Wie Profilname** und geben Sie den entsprechenden Wert als **Anzeigenamen** an.

| **Rolle** | **Anzeigename (erforderlich)** | **Empfohlener Profilname** |
|---|---|---|
| Geschäftsinhaber | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Geschäftsinhaber“ |
| Implementierungs-Manager | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Implementierungs-Manager“ |
| Entwickler | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Entwickler“ |
| Programm-Manager | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Programm-Manager“ |

![Erstellen eines neuen Profils](/help/assets/screen_shot_2018-05-04at171819.png)

Nachdem Sie das Produktprofil erstellt haben, können Sie diesen Produktprofilen Anwender (oder Gruppen) hinzufügen.

![Bearbeiten von Anwendern](/help/assets/image2018-4-9_15-19-26.png)

![Benutzergruppen](/help/assets/image2018-4-9_15-16-47.png)
