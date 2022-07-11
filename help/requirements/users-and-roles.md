---
title: Hinzufügen von Anwendern und Rollen
description: Erfahren Sie, wie Sie mit der Admin Console Benutzer und Rollen hinzufügen und Profile erstellen können.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 30%

---


# Hinzufügen von Anwendern und Rollen {#add-users-and-roles}

Viele Funktionen in [!UICONTROL Cloud Manager] erfordert spezifische Berechtigungen zur Verwendung. Beispielsweise dürfen nur bestimmte Benutzer die KPIs (Key Performance Indicators) für ein Programm festlegen. Diese Berechtigungen werden logisch in Rollen gruppiert.

In [!UICONTROL Cloud Manager] sind derzeit vier Rollen für Anwender definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Business Owner
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
| Geschäftsinhaber | Dieser Benutzer ist für die Definition von KPIs, die Genehmigung von Produktionsbereitstellungen und das Überschreiben wichtiger 3-Tier-Fehler bei Bedarf zuständig. |
| Programm-Manager | Dieser Benutzer verwendet [!UICONTROL Cloud Manager] , um Teams einzurichten, den Status zu überprüfen, KPIs anzuzeigen und wichtige 3-Tier-Fehler bei Bedarf zu genehmigen. |
| Implementierungs-Manager | Dieser Benutzer verwaltet Bereitstellungsvorgänge und verwendet [!UICONTROL Cloud Manager] um Staging-/Produktionsbereitstellungen auszuführen, CI/CD-Pipelines zu bearbeiten, bei Bedarf wichtige 3-Tier-Fehler zu genehmigen und auf das Git-Repository zugreifen zu können. |
| Entwickler | Dieser Benutzer entwickelt und testet benutzerdefinierten Anwendungscode und verwendet hauptsächlich [!UICONTROL Cloud Manager] , um den Bereitstellungsstatus anzuzeigen und auf das Git-Repository für Code-Commits zugreifen zu können. |
| Customer Success Engineer | Dieser Benutzer unterstützt im Allgemeinen den Kundenerfolg für AMS-Kunden und interagiert mit [!UICONTROL Cloud Manager] zum Ausführen von Bereitstellungen, die eine CSE-Überwachung erfordern. |
| Inhaltsautor | Dieser Benutzer interagiert im Allgemeinen nicht mit [!UICONTROL Cloud Manager] , kann jedoch [!UICONTROL Cloud Manager] Programmumschalter , um auf AEM zuzugreifen. |

>[!NOTE]
>
>Die Entwicklerrolle in der Admin Console ist nicht mit der Entwicklerrolle in [!UICONTROL Cloud Manager].

## Erstellen von Profilen mit Admin Console {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager] -Rollen werden über die Admin Console verwaltet. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem der Benutzer zu einem [!UICONTROL Cloud Manager] Produktprofil.

Die Admin Console ist ein zentraler Ort für die Verwaltung Ihrer Adobe-Berechtigungen in Ihrem gesamten Unternehmen. Weitere Informationen zu Adobe Admin Console finden Sie in der Dokumentation zur [Admin Console.](https://helpx.adobe.com/de/enterprise/using/admin-console.html)

>[!NOTE]
>
>Um auf die Admin Console zuzugreifen und Ihr Team (Benutzer und Rollen) einzurichten, besuchen Sie [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com).

Um die entsprechenden rollenbasierten Berechtigungen für [!UICONTROL Cloud Manager] -Benutzern muss ein Administrator in der Kundenorganisation neue Produktprofile unter der [!UICONTROL AEM Managed Services] Produktkontext, der jedem der vier [!UICONTROL Cloud Manager] Benutzerrollen:

* Geschäftsinhaber
* Implementierungs-Manager
* Entwickler
* Programmmanager

Mit der Admin Console können Sie Benutzer/Gruppen für diese Produktprofile erstellen oder hinzufügen.

1. Melden Sie sich bei der Admin Console an und klicken Sie auf **Neues Profil** , um ein neues Profil hinzuzufügen.

   ![Neues Profil](/help/assets/admin_console_roles-1.png)

1. Geben Sie die Informationen ein, um eine neue Rolle für [!UICONTROL Cloud Manager].

   * **Profilname**
   * **Anzeigename**
   * **Berechtigungsgruppe**

1. Klicken Sie auf **Fertig**, um die Profilerstellung abzuschließen.

Wenn Sie Produktprofile erstellen, wird die **Anzeigename** muss der technische Wert sein, der durch [!UICONTROL Cloud Manager] (siehe folgende Tabelle). Die **Profilname** kann beliebig sein. Um Verwirrung zu vermeiden, wird jedoch empfohlen, die Werte in der Variablen **Empfohlener Profilname** Spalte. Deaktivieren Sie dazu beim Erstellen des Produktprofils die Option **Wie Profilname** und geben Sie den entsprechenden Wert als **Anzeigenamen** an.

| **Rolle** | **Anzeigename (erforderlich)** | **Empfohlener Profilname** |
|---|---|---|
| Business Owner | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Business Owner“ |
| Implementierungs-Manager | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Implementierungs-Manager“ |
| Entwickler | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Entwickler“ |
| Programmmanager | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Programmmanager“ |

![Neues Profil erstellen](/help/assets/screen_shot_2018-05-04at171819.png)

Nachdem Sie ein Produktprofil erstellt haben, können Sie diesen Produktprofilen Benutzer (oder Gruppen) hinzufügen.

![Benutzer bearbeiten](/help/assets/image2018-4-9_15-19-26.png)

![Benutzergruppen](/help/assets/image2018-4-9_15-16-47.png)
