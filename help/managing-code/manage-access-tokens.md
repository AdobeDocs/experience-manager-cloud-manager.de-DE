---
title: Verwalten von Zugriffstoken in Cloud Manager
description: Erfahren Sie, wie Sie Zugriffstoken anzeigen, bearbeiten und löschen können, die für das Übermitteln Ihres eigenen Git-Repositorys in Cloud Manager auf Adobe Managed Services verwendet werden.
badge: label="Early Adopter" type="Positive" url="/help/release-notes/current.md
source-git-commit: aa0eff7eb1f6b0cde9b99b7cbbfb3410e0db94a6
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 11%

---


# Verwalten von Zugriffstoken für externe Repositorys {#manage-access-tokens}

Cloud Manager verwendet Zugriffstoken, um auf externen Git-Plattformen gehostete Repositorys zu verwalten. Wenn ein Token abgelaufen war, musste das zugehörige Repository zuvor neu integriert werden, um funktionsfähig zu bleiben.

Mit der Funktion **Zugriffs-Token verwalten** können Sie Token jetzt effizienter verwalten. Sie können Token anzeigen, umbenennen oder entfernen, die mit unterstützten externen Git-Anbietern wie GitHub Enterprise, GitLab, Bitbucket und Azure DevOps verbunden sind.

Siehe auch [Hinzufügen externer Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

>[!NOTE]
>
>Die in diesem Artikel beschriebenen Funktionen sind nur über das Early-Adopter-Programm verfügbar. Weitere Informationen und die Möglichkeit, sich bei frühzeitigen Anwendern anzumelden, finden Sie unter [Verwalten von Zugriffstoken](/help/release-notes/current.md#access-tokens).

## Zugriffstoken anzeigen {#view-access-tokens}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in **[Konsole](/help/getting-started/navigation.md#my-programs-console)** Meine Programme“ das Programm aus, dessen eigenes Git-Zugriffstoken Sie verwalten möchten.
1. Klicken Sie im Seitenmenü unter **Programm** auf ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorys**.
1. Klicken Sie oben rechts auf der Seite auf **Zugriffstoken verwalten**.

   Die Schaltfläche **Zugriffs-Token verwalten** ist nur sichtbar, wenn Ihr Programm die Funktion „Eigenes Git einbringen“ verwendet.

   ![Dialogfeld „Zugriffs-Token verwalten“ mit einem aktiven und einem inaktiven Token](/help/managing-code/assets/access-tokens-manage.png)

1. Im Dialogfeld **Zugriffstoken verwalten**:
   * Alle Zugriffstoken werden aufgelistet.
   * Sie können **Token** bearbeiten.
   * Sie können **nur** Token (löschen *die derzeit nicht verwendet werden*. Wenn ein Token verwendet wird, ist die Schaltfläche ![Gliederungssymbol löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) deaktiviert.

## Bearbeiten eines Zugriffstokens {#edit-access-tokens}

1. Klicken Sie **Dialogfeld** Zugriffs-Token verwalten“ rechts neben einem Token-Namen auf ![Symbol „Bearbeiten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. Aktualisieren Sie **Dialogfeld „Zugriffs** Token bearbeiten“ im Textfeld **Token** den Token-Namen.

   Das Zugriffstoken-Geheimnis selbst kann nicht geändert werden.

   ![Dialogfeld „Zugriffstoken bearbeiten“](/help/managing-code/assets/access-tokens-edit.png)

1. Wenn das Token verwendet wird, werden Sie in einer Benachrichtigung darauf hingewiesen, dass alle zugehörigen Repositorys automatisch erneut überprüft werden.

1. Klicken Sie **Aktualisieren**, um die Änderungen zu speichern.

## Löschen eines Zugriffs-Tokens {#delete-access-token}

1. Klicken Sie **Dialogfeld** Zugriffs-Token verwalten“ rechts neben einem Token-Namen auf ![Löschsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   Das Symbol ist für Token![ die derzeit verwendet werden, deaktiviert (](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)Löschkontursymbol).

1. Klicken Sie im Dialogfeld **Zugriffs-Token löschen** auf **Löschen**, um das Token dauerhaft zu entfernen.