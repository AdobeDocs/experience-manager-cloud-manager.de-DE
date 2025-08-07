---
title: Verwalten von Zugriffstoken in Cloud Manager
description: Erfahren Sie, wie Sie Zugriffstoken anzeigen, bearbeiten und löschen können, die für das Übermitteln Ihres eigenen Git-Repositorys in Cloud Manager auf Adobe Managed Services verwendet werden.
exl-id: 873aad0b-d7c6-4bc3-a70d-bbfdc1e02193
source-git-commit: d6f058c3f6dc010f08a5cb75a0fb152b56111e79
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 79%

---

# Verwalten von Zugriffs-Token für externe Repositorys {#manage-access-tokens}

Cloud Manager verwendet Zugriffs-Token, um auf externen Git-Plattformen gehostete Repositorys zu verwalten. Wenn ein Token abgelaufen war, musste das zugehörige Repository zuvor neu integriert werden, um funktionsfähig zu bleiben.

Mit **Zugriffs-Token verwalten** können Sie Token jetzt effizienter verwalten. Sie können Token anzeigen, umbenennen oder entfernen, die mit unterstützten externen Git-Anbietern wie GitHub Enterprise, GitLab, Bitbucket und Azure DevOps verbunden sind.

Siehe auch [Hinzufügen von externen Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

>[!NOTE]
>
>Die in diesem Artikel beschriebenen Funktionen sind nur über das Private Beta-Programm verfügbar. Weitere Informationen und zum Anmelden bei der privaten Beta-Version finden Sie unter [Verwalten von Zugriffstoken](/help/release-notes/current.md#access-tokens).

## Anzeigen von Zugriffs-Token {#view-access-tokens}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/getting-started/navigation.md#my-programs-console)** das Programm aus, dessen Zugriffs-Token für „Bring Your Own Git“ Sie verwalten möchten.
1. Klicken Sie im Seitenmenü unter **Programm** auf ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorys**.
1. Klicken Sie oben rechts auf der Seite auf **Zugriffs-Token verwalten**.

   Die Schaltfläche **Zugriffs-Token verwalten** ist nur sichtbar, wenn Ihr Programm die Funktion „Bring Your Own Git“ verwendet.

   ![Dialogfeld „Zugriffs-Token verwalten“ mit einem aktiven und einem inaktiven Token](/help/managing-code/assets/access-tokens-manage.png)

1. Im Dialogfeld **Zugriffs-Token verwalten**:
   * Alle Zugriffs-Token werden aufgelistet.
   * Sie können **Token** bearbeiten.
   * Sie können **nur** Token (löschen *die derzeit nicht verwendet werden*. Wenn ein Token verwendet wird, ist die Schaltfläche ![Gliederungssymbol löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) deaktiviert.

## Bearbeiten eines Zugriffs-Tokens {#edit-access-tokens}

1. Klicken Sie im Dialogfeld **Zugriffs-Token verwalten** rechts neben einem Token-Namen auf ![Bearbeiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. Aktualisieren Sie im Dialogfeld **Zugriffs-Token bearbeiten** den Wert **Token-Name** oder **Zugriffs-Token** oder beide.

   ![Dialogfeld „Zugriffstoken bearbeiten“](/help/managing-code/assets/access-tokens-edit.png)

1. Wenn das **Zugriffs-Token** derzeit verwendet wird, werden Sie in einer Benachrichtigung darauf hingewiesen, dass alle zugehörigen Repositorys nach der Aktualisierung automatisch erneut validiert werden.

1. Klicken Sie auf **Aktualisieren**, um die Änderungen zu speichern.

## Löschen eines Zugriffs-Tokens {#delete-access-token}

1. Klicken Sie im Dialogfeld **Zugriffs-Token verwalten** rechts neben einem Token-Namen auf ![Löschsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   Das Symbol ist für Token, die derzeit verwendet werden, deaktiviert (![Konturlöschsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)).

1. Klicken **unter „Zugriffs-Token löschen** auf **Löschen**, um das Token dauerhaft zu entfernen.
