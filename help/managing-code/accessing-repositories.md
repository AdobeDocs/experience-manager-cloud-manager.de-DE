---
title: Repository-Zugriffsinformationen
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihre von Adobe verwalteten Git-Repositorys zugreifen und diese verwalten können.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '361'
ht-degree: 100%

---

# Repository-Zugriffsinformationen {#accessing-repos}

Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung in Cloud Manager auf Ihre von Adobe verwalteten Git-Repositorys zugreifen und diese verwalten können.

## Zugriff auf Repository-Informationen von der Übersichtsseite aus {#overview-page}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Gehen Sie von Ihrer Seite **Programmübersicht** aus zur Karte **Pipelines**.

   ![Schaltfläche „Auf Repository-Informationen zugreifen“ auf der Karte „Umgebungen“](assets/pipelines-card.png)

1. Klicken Sie auf **Auf Repository-Informationen zugreifen**. Im Dialogfeld **Repository-Informationen für …** können Sie Folgendes anzeigen:

   * Den Git-Benutzernamen.
   * Das Git-Kennwort.
   * Die URL zum Git-Repository von Cloud Manager.
   * Vordefinierte Git-Befehle zum schnellen Hinzufügen einer Remote-Verbindung zu Ihrem Git-Repository und Push-Code.

   ![Fenster „Repository-Informationen“](assets/access-repo-info.png)

1. Um auf das Kennwort zugreifen zu können, muss ein neues Kennwort generiert werden. Klicken Sie auf **`Generate password`**.

1. Bestätigen Sie die Generierung des Kennworts im Dialogfeld **Sind Sie sicher, …?** durch Klicken auf **Kennwort generieren**.

   ![Kennwortgenerierung bestätigen](assets/confirm-password-generation.png)

1. Das Kennwort wird im Feld **Kennwort** generiert. Klicken Sie auf das Symbol „Kopieren“, um es in die Zwischenablage zu kopieren.

   * Durch das Generieren eines Kennworts wird das vorherige Kennwort ungültig.
   * Cloud Manager speichert Ihr Zugangskennwort nicht. Achten Sie darauf, dass Sie dieses Kennwort sicher speichern.
   * Wenn Sie das Kennwort verlieren, müssen Sie ein neues generieren.

   ![Beispiel eines generierten Kennworts](assets/generated-password.png)

Mithilfe dieser Anmeldeinformationen können Sie eine lokale Kopie des Repositorys klonen, Änderungen an diesem lokalen Repository vornehmen und etwaige Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.

>[!NOTE]
>
>* Die Option **Auf Repository-Informationen zugreifen** ist für Benutzende mit der Rolle **Entwickler** oder **Bereitstellungs-Manager** sichtbar.
>* Durch die Schaltfläche **Auf Repository-Informationen zugreifen** werden nur die Repository-Zugriffsinformationen für von Adobe verwaltete Repositorys angezeigt. Zugriffsinformationen über [private Repositorys](private-repositories.md) sind in Cloud Manager nicht verfügbar.

## Zugreifen auf Repository-Informationen über das Fenster „Repositorys“ {#repositories-window}

Eine Schaltfläche **Auf Repository-Informationen zugreifen** ist auch in der Symbolleiste des Fensters [**Repositorys** verfügbar](managing-repositories.md). Es werden dieselben Informationen zum Zugriff auf von Adobe verwaltete Repositorys angezeigt.

## Widerrufen eines Zugangskennworts {#revoke-password}

Sie können jederzeit ein Zugangskennwort sperren lassen. [Erstellen Sie ein Support-Ticket für eine solche Anfrage](https://experienceleague.adobe.com/?lang=de?support-solution=Experience+Manager&amp;support-tab=home#support).

Das Ticket wird mit hoher Priorität behandelt und die Sperrung wird typischerweise innerhalb eines Tages erfolgen.
