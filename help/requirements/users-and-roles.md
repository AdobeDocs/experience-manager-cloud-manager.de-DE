---
title: Hinzufügen von Anwendern und Rollen
description: Erfahren Sie, wie Sie mit der Admin Console Benutzer und Rollen hinzufügen und Profile erstellen können.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '758'
ht-degree: 47%

---


# Hinzufügen von Benutzern und Rollen {#add-users-and-roles}

Für viele Funktionen in [!UICONTROL Cloud Manager] sind spezielle Berechtigungen erforderlich. Beispielsweise dürfen nur bestimmte Anwender die KPIs (Key Performance Indicators) für ein Programm festlegen. Diese Berechtigungen werden logisch in Rollen gruppiert.

[!UICONTROL Cloud Manager] definiert derzeit vier Benutzerrollen, die für die Verfügbarkeit bestimmter Funktionen gelten:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

>[!NOTE]
>
>Um [!UICONTROL Cloud Manager] verwenden zu können, müssen Sie über eine Adobe ID und den Adobe Managed Services-Produktkontext verfügen.

## Rollendefinitionen {#role-definitions}

Die folgende Tabelle fasst die Rollen in Cloud Manager zusammen.

| [!UICONTROL Cloud Manager]-Rolle | Beschreibung |
| --- | --- |
| Geschäftsinhaber | Verantwortlich für die Definition von KPIs, die Genehmigung von Produktionsbereitstellungen und das Überschreiben wichtiger 3-Tier-Fehler bei Bedarf. |
| Programm-Manager | Sie verwenden [!UICONTROL Cloud Manager], um Teams einzurichten, den Status zu überprüfen, KPIs anzuzeigen und wichtige 3-Tier-Fehler bei Bedarf zu genehmigen. |
| Bereitstellungs-Manager | Verwaltet Bereitstellungsvorgänge und verwendet [!UICONTROL Cloud Manager], um Staging- und Produktionsbereitstellungen auszuführen, CI/CD-Pipelines zu bearbeiten und bei Bedarf kritische 3-Tier-Fehler zu genehmigen. Sie haben auch Zugriff auf das Git-Repository. |
| Entwicklerin oder Entwickler | Entwickelt und testet benutzerdefinierten Anwendungscode und verwendet hauptsächlich [!UICONTROL Cloud Manager], um den Bereitstellungsstatus anzuzeigen, und kann auf das Git-Repository für Codecommits zugreifen. |
| Customer Success Engineer | Der CSE unterstützt im Allgemeinen den Kundenerfolg für AMS-Kunden. Sie interagieren mit [!UICONTROL Cloud Manager] , um Bereitstellungen auszuführen, die von einem CSE überwacht werden müssen. |
| Inhaltsautorin oder -autor | Sie interagieren im Allgemeinen nicht mit [!UICONTROL Cloud Manager], können jedoch den Programmschalter [!UICONTROL Cloud Manager] verwenden, um auf AEM zuzugreifen. |

>[!NOTE]
>
>Die Entwicklerrolle in der Admin Console hat nichts mit der Entwicklerrolle in [!UICONTROL Cloud Manager] zu tun.

## Erstellen eines Profils mithilfe der Admin Console {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager]-Rollen werden über die Admin Console verwaltet. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem der Anwender einem [!UICONTROL Cloud Manager]-Produktprofil hinzugefügt wird.

Die Admin Console ermöglicht eine zentrale Verwaltung Ihrer Adobe-Berechtigungen in der gesamten Organisation. Weitere Informationen zur Adobe Admin Console finden Sie unter [Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html).

Ein Administrator muss unter dem Produktkontext [!UICONTROL AEM Managed Services] neue Produktprofile erstellen, um rollenbasierte Berechtigungen für Benutzer von [!UICONTROL Cloud Manager] zuzuweisen, die jeder der vier Rollen [!UICONTROL Cloud Manager] entsprechen.

* Geschäftsinhaber
* Bereitstellungs-Manager
* Entwickler
* Programm-Manager

Mit der Admin Console können Sie Benutzer oder Gruppen für diese Produktprofile erstellen oder hinzufügen.

1. Melden Sie sich bei der Admin Console um [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) an.

1. Klicken Sie auf die Registerkarte **Übersicht** und dann auf der Karte **Produkte und Dienste** auf das Produkt, das Sie bearbeiten möchten. Wenn es dort nicht aufgeführt ist, verwenden Sie die Registerkarte **Produkte**, um das Produkt zu suchen, und klicken Sie darauf.

   ![Registerkarte Übersicht Admin Console](/help/assets/admin-console-overview.png)

1. Auf der Registerkarte **Produkte** klicken Sie auf die Umgebung, der Sie Benutzer/Gruppen zu Produktprofilen hinzufügen möchten.

   ![Registerkarte Admin Console Produkte](/help/assets/admin-console-product.png)

1. Klicken Sie auf der Registerkarte **Produktprofil** des Produkts auf **Neues Profil**, um ein neues Profil hinzuzufügen.

   ![Neues Profil](/help/assets/admin-console-product-profiles.png)

1. Tragen Sie die Informationen ein, um eine neue Rolle für [!UICONTROL Cloud Manager] einzurichten.

   * **Profilname** - Der **Profilname** kann beliebig sein. Um Verwirrungen zu vermeiden, wird jedoch empfohlen, die Werte in der Spalte **Empfohlener Profilname** zu verwenden.
   * **Anzeigename** – Der **Anzeigename** muss dem vom [!UICONTROL Cloud Manager] definierten technischen Wert entsprechen (siehe nachfolgende Tabelle).
   * **Berechtigungsgruppe** – Sie können eine Berechtigungsgruppe für das Profil auswählen (nicht immer verfügbar).

   ![Erstellen eines neuen Profils](/help/assets/screen_shot_2018-05-04at171819.png)

   | Rolle | Anzeigename (erforderlich) | Empfohlener Profilname |
   |---|---|---|
   | Geschäftsinhaber | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Geschäftsinhaber“ |
   | Bereitstellungs-Manager | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Bereitstellungs-Manager“ |
   | Entwickler | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Entwickler“ |
   | Programm-Manager | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Programm-Manager“ |


1. Klicken Sie auf **Fertig**, um das neue Profil zu speichern.

## Zuweisen von Profilen zu Benutzern oder Benutzergruppen {#assign-profiles}

Nachdem Sie Produktprofile erstellt haben, können Sie ihnen Benutzer oder Benutzergruppen zuweisen.

1. Melden Sie sich bei der Admin Console um [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) an.

1. Wählen Sie in der Admin Console die Registerkarte **Benutzer**.

   ![Registerkarte „Benutzer“](/help/assets/admin-console-users.png)

1. Klicken Sie im linken Navigationsbereich auf **Benutzer** und klicken Sie dann auf einen Benutzer, um ihn zu ändern.

1. Klicken Sie auf die Suchschaltfläche im Abschnitt **Produkte** und wählen Sie **Bearbeiten** aus.

   ![Benutzer bearbeiten](/help/assets/admin-console-edit-user.png)

1. Klicken Sie im Dialogfeld **Produkte und Benutzergruppen bearbeiten** auf die Plusschaltfläche und wählen Sie die Profile aus, die dem Benutzer zugewiesen werden sollen.

   * Wenn der Benutzer den Rollen bereits zugewiesen ist, ist die Schaltfläche mit dem Pluszeichen eine Bearbeitungsschaltfläche (ein Bleistift), funktioniert aber auf dieselbe Weise.

   ![Produkte und Benutzergruppen bearbeiten](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Klicken Sie auf **Speichern**, um die Profile der Benutzer zu speichern.

Wiederholen Sie die gleichen Schritte, um Benutzergruppen Profile zuzuweisen, wählen Sie jedoch **Benutzergruppen** über das linke Navigationsfenster auf der Registerkarte **Benutzer**. Klicken Sie auf eine Benutzergruppe, wählen Sie die Registerkarte **Zugewiesene Produktprofile** aus und klicken Sie auf **Produktprofil zuweisen** , um Profile zuzuweisen.

![Profile einer Gruppe zuweisen](/help/assets/admin-console-edit-user-groups.png)
