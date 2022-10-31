---
title: Hinzufügen von Anwendern und Rollen
description: Erfahren Sie, wie Sie mit der Admin Console Anwender und Rollen hinzufügen und Profile erstellen können.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: dd96d773ea3e6b9c45886fe41b28d3dd70cb8a61
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

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

Um die entsprechenden rollenbasierten Berechtigungen für [!UICONTROL Cloud Manager]-Anwender bereitzustellen, muss ein Administrator in der Organisation des Kunden neue Produktprofile unter dem [!UICONTROL AEM Managed Services]-Produktkontext für jede der vier [!UICONTROL Cloud Manager]-Rollen erstellen:

* Geschäftsinhaber
* Implementierungs-Manager
* Entwickler
* Programm-Manager

Mit der Admin Console können Sie Anwender/Gruppen für diese Produktprofile erstellen oder hinzufügen.

1. Melden Sie sich bei der Admin Console an unter [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Klicken Sie auf **Übersicht** auf das Produkt klicken, das Sie ändern möchten, auf der Registerkarte **Produkte und Dienstleistungen** Karte. Wenn es dort nicht aufgeführt ist, verwenden Sie die **Produkte** , um das Produkt zu suchen, und klicken Sie darauf.

   ![Registerkarte &quot;Admin Console - Übersicht&quot;](/help/assets/admin-console-overview.png)

1. Im **Produkte** klicken Sie auf die Umgebung, der Sie Benutzer/Gruppen zu Produktprofilen hinzufügen möchten.

   ![Registerkarte &quot;Admin Console-Produkte&quot;](/help/assets/admin-console-product.png)

1. Im **Produktprofil** Registerkarte des Produkts klicken Sie auf **Neues Profil** , um ein neues Profil hinzuzufügen.

   ![Neues Profil](/help/assets/admin-console-product-profiles.png)

1. Tragen Sie die Informationen ein, um eine neue Rolle für [!UICONTROL Cloud Manager] einzurichten.

   * **Profilname** - Der **Profilname** ist beliebig. Um Verwirrungen zu vermeiden, sollten Sie jedoch die Werte in der unten stehenden Spalte **Empfohlener Profilname** verwenden.
   * **Anzeigename** - die **Anzeigename** muss der technische Wert sein, der durch [!UICONTROL Cloud Manager] (siehe folgende Tabelle).
   * **Berechtigungsgruppe** - Sie können eine Berechtigungsgruppe für das Profil auswählen (nicht immer verfügbar).

   ![Erstellen eines neuen Profils](/help/assets/screen_shot_2018-05-04at171819.png)

   | Rolle | Anzeigename (erforderlich) | Empfohlener Profilname |
   |---|---|---|
   | Geschäftsinhaber | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Geschäftsinhaber“ |
   | Implementierungs-Manager | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Implementierungs-Manager“ |
   | Entwickler | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Entwickler“ |
   | Programm-Manager | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Programm-Manager“ |


1. Klicken **Fertig** , um das neue Profil zu speichern.

## Zuweisen von Profilen zu Benutzern oder Benutzergruppen {#assign-profiles}

Nachdem Sie Produktprofile erstellt haben, können Sie ihnen Benutzer oder Benutzergruppen zuweisen.

1. Melden Sie sich bei der Admin Console an unter [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Wählen Sie in der Admin Console die **Benutzer** Registerkarte.

   ![Registerkarte &quot;Benutzer&quot;](/help/assets/admin-console-users.png)

1. Klicken Sie auf **Benutzer** im linken Navigationsbereich und klicken Sie dann auf einen Benutzer, um ihn zu ändern.

1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten im **Produkte** und wählen Sie **Bearbeiten**.

   ![Benutzer bearbeiten](/help/assets/admin-console-edit-user.png)

1. Im **Produkte und Benutzergruppen bearbeiten** klicken Sie auf die Schaltfläche mit dem Pluszeichen und wählen Sie die Profile aus, die dem Benutzer zugewiesen werden sollen.

   * Wenn der Benutzer den Rollen bereits zugewiesen ist, ist die Schaltfläche mit dem Pluszeichen eine Bearbeitungsschaltfläche (ein Bleistift), funktioniert aber auf dieselbe Weise.

   ![Produkte und Benutzergruppen bearbeiten](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Klicken **Speichern** , um die Profile für den Benutzer zu speichern.

Wiederholen Sie die gleichen Schritte, um Profile Benutzergruppen zuzuweisen, wählen Sie jedoch **Benutzergruppen** über das linke Navigationsfenster auf **Benutzer** Registerkarte. Klicken Sie auf eine Benutzergruppe und wählen Sie die **Zugewiesene Produktprofile** Registerkarte und klicken Sie auf **Produktprofil zuweisen** , um Profile zuzuweisen.

![Zuweisen von Profilen zu Gruppen](/help/assets/admin-console-edit-user-groups.png)
