---
title: Hinzufügen von Anwendern und Rollen
description: Erfahren Sie, wie Sie mit der Admin Console Benutzende und Rollen hinzufügen und Profile erstellen können.
exl-id: 40086cf0-a1c4-4dde-9dbf-84ea5fa53b84
source-git-commit: 9ad9af206fafea45f8bbf61b02950de0776b5a9f
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 86%

---


# Hinzufügen von Benutzenden und Rollen {#add-users-and-roles}

Für viele Funktionen in [!UICONTROL Cloud Manager] sind spezielle Berechtigungen erforderlich. Beispielsweise dürfen nur bestimmte Anwender die KPIs (Key Performance Indicators) für ein Programm festlegen. Diese Berechtigungen werden logisch in Rollen gruppiert.

In [!UICONTROL Cloud Manager] sind derzeit vier Rollen für Benutzende definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwicklerin oder Entwickler

>[!NOTE]
>
>Um [!UICONTROL Cloud Manager] verwenden zu können, müssen Sie über eine Adobe ID und den Adobe Managed Services-Produktkontext verfügen.

## Rollendefinitionen {#role-definitions}

In der folgenden Tabelle sind die Rollen in Cloud Manager zusammengefasst. 

| [!UICONTROL Cloud Manager]-Rolle | Beschreibung |
| --- | --- |
| Geschäftsinhaber | Verantwortlich für die Definition von KPIs, die Genehmigung von Produktionsbereitstellungen und das Überschreiben von gravierenden dreistufigen Fehlern, falls erforderlich. |
| Programm-Manager | Diese Person nutzt [!UICONTROL Cloud Manager], um die Einrichtung von Teams vorzunehmen, den Status zu überprüfen, KPIs einzusehen und ggf. gravierende dreistufige Fehler zu genehmigen. |
| Bereitstellungs-Manager | Verwaltet die Bereitstellungsvorgänge mit [!UICONTROL Cloud Manager], um Staging- und Produktionsbereitstellungen durchzuführen, CI/CD-Pipelines zu bearbeiten und bei Bedarf gravierende dreistufige Fehler zu genehmigen. Diese Personen haben außerdem Zugriff auf das Git-Repository. |
| Entwicklerin oder Entwickler | Entwickelt und testet benutzerdefinierten Anwendungs-Code, verwendet [!UICONTROL Cloud Manager] hauptsächlich zur Anzeige des Bereitstellungsstatus und kann für Code-Commits auf das Git-Repository zugreifen. |
| Customer Success Engineer | Diese Person unterstützt im Allgemeinen den Erfolg von AMS-Kunden. Sie interagiert mit [!UICONTROL Cloud Manager], um Bereitstellungen auszuführen, die von einer bzw. einem CSE überwacht werden müssen. |
| Inhaltsautorin oder -autor | Interagiert im Allgemeinen nicht mit [!UICONTROL Cloud Manager], kann aber den[!UICONTROL Cloud Manager]-Programmumschalter verwenden, um auf AEM zuzugreifen. |

>[!NOTE]
>
>Die Entwicklerrolle in der Admin Console hat nichts mit der Entwicklerrolle in [!UICONTROL Cloud Manager] zu tun.

## Erstellen eines Produktprofils mit der Admin Console {#using-admin-console-to-create-a-profile}

[!UICONTROL Cloud Manager]-Rollen werden über die Admin Console verwaltet. Bestimmte Rollenmitgliedschaften werden bereitgestellt, indem der Anwender einem [!UICONTROL Cloud Manager]-Produktprofil hinzugefügt wird.

Die Admin Console ermöglicht eine zentrale Verwaltung Ihrer Adobe-Berechtigungen in der gesamten Organisation. Weitere Informationen zur Adobe Admin Console finden Sie unter [Admin Console](https://helpx.adobe.com/de/enterprise/using/admin-console.html).

Admins müssen unter dem Produktkontext [!UICONTROL AEM Managed Services] neue Produktprofile erstellen, um rollenbasierte Berechtigungen für Benutzende von [!UICONTROL Cloud Manager] zuzuweisen, die jeder der vier [!UICONTROL Cloud Manager]-Rollen entsprechen.

* Geschäftsinhaber
* Bereitstellungs-Manager
* Entwicklerin oder Entwickler
* Programm-Manager

Erstellen oder fügen Sie diesen Produktprofilen mit der Admin Console Benutzer oder Gruppen hinzu.

<!-- CQDOC-22790
>[!IMPORTANT]
>
>Due to a current limitation in the Admin Console and Cloud Manager, profiles cannot be saved with **No permissions** selected. Attempting to do so results in a backend error. This behavior affects the creation of Deployment Manager profiles. As a workaround, select at least one permission when creating a new profile. -->

**So erstellen Sie ein Produktprofil mit der Admin Console:**

1. Melden Sie sich bei der Admin Console unter [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) an.

1. Klicken Sie auf der Registerkarte **Überblick** auf das Produkt, das auf der Karte **Produkte und Services** bearbeitet werden soll. Wenn es dort nicht aufgeführt ist, verwenden Sie die Registerkarte **Produkte**, um das Produkt zu suchen, und klicken Sie darauf.

   ![Registerkarte Übersicht Admin Console](/help/assets/admin-console-overview.png)

1. Auf der Registerkarte **Produkte** klicken Sie auf die Umgebung, der Sie Benutzer/Gruppen zu Produktprofilen hinzufügen möchten.

   ![Registerkarte Admin Console Produkte](/help/assets/admin-console-product.png)

1. Klicken Sie auf der Registerkarte **Produktprofil** des Produkts auf **Neues Profil**, um ein neues Profil hinzuzufügen.

   ![Neues Profil](/help/assets/admin-console-product-profiles.png)

1. Tragen Sie die Informationen ein, um eine neue Rolle für [!UICONTROL Cloud Manager] einzurichten.

   * **Profilname** – Der **Profilname** ist beliebig. Um Missverständnisse zu vermeiden, sollten Sie jedoch die Werte in der Spalte **Empfohlener Profilname** verwenden.
   * **Anzeigename** – Der **Anzeigename** muss dem vom [!UICONTROL Cloud Manager] definierten technischen Wert entsprechen (siehe nachfolgende Tabelle).
   * **Berechtigungsgruppe** – Sie können eine Berechtigungsgruppe für das Profil auswählen (nicht immer verfügbar).

<!-- CQDOC-22790
      >[!IMPORTANT]
      >
      >Due to a current limitation in the Admin Console and Cloud Manager, profiles cannot be saved with **No permissions** selected. Attempting to do so results in a backend error. This behavior affects the creation of Deployment Manager profiles. As a workaround, select at least one permission when creating a new profile. -->

![Erstellen eines neuen Profils](/help/assets/screen_shot_2018-05-04at171819.png)

| Rolle | Anzeigename (erforderlich) | Empfohlener Profilname |
|---|---|---|
| Geschäftsinhaber | `CM_BUSINESS_OWNER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Geschäftsinhaber“ |
| Bereitstellungs-Manager | `CM_DEPLOYMENT_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Bereitstellungs-Manager“ |
| Entwicklerin oder Entwickler | `CM_DEVELOPER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Entwickler“ |
| Programm-Manager | `CM_PROGRAM_MANAGER_ROLE_PROFILE` | [!UICONTROL Cloud Manager] – Rolle „Programm-Manager“ |


1. Klicken Sie auf **Fertig**, um das neue Profil zu speichern.

## Zuweisen von Profilen zu Benutzenden oder Benutzergruppen {#assign-profiles}

Nachdem Sie Produktprofile erstellt haben, können Sie ihnen Benutzerinnen, Benutzer oder Benutzergruppen zuweisen.

1. Melden Sie sich bei Admin Console unter [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) an.

1. Wählen Sie in der Admin Console die Registerkarte **Benutzer**.

   ![Registerkarte „Benutzer“](/help/assets/admin-console-users.png)

1. Klicken Sie im linken Navigationsbereich auf **Benutzer** und dann auf eine Benutzerin oder einen Benutzer, um diese bzw. diesen zu ändern.

1. Klicken Sie auf ![Mehr-Symbol, ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)) im Abschnitt **Produkte** und klicken Sie auf **Bearbeiten**.

   ![Benutzer bearbeiten](/help/assets/admin-console-edit-user.png)

1. Klicken Sie **Dialogfeld „Produkte und Benutzergruppen bearbeiten** auf ![Hinzufügen-Symbol, Pluszeichen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) und wählen Sie die Profile aus, die dem Benutzer zugewiesen werden sollen.

   * Wenn der Benutzer den Rollen bereits zugewiesen ist, ist die Schaltfläche ![Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) eine Bearbeitungsschaltfläche (ein Bleistift), funktioniert jedoch auf dieselbe Weise.

   ![Produkte und Benutzergruppen bearbeiten](/help/assets/admin-console-edit-products-and-user-groups.png)

1. Klicken Sie auf **Speichern**, um die Profile der Benutzer zu speichern.

Wiederholen Sie die gleichen Schritte, um Benutzergruppen Profile zuzuweisen, wählen Sie jedoch **Benutzergruppen** über das linke Navigationsfenster auf der Registerkarte **Benutzer**. Klicken Sie auf eine Benutzergruppe und wählen Sie **Zugewiesene Produktprofile** klicken Sie auf **Produktprofil zuweisen**, um Profile zuzuweisen.

![Profile einer Gruppe zuweisen](/help/assets/admin-console-edit-user-groups.png)
