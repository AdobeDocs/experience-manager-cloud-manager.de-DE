---
title: Repository-Zugriffsinformationen
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung von Cloud Manager auf Ihre von Adobe verwalteten Git-Repositorys zugreifen und diese verwalten können.
exl-id: 1cc88c82-67c7-4553-a1b8-d2ab22be466c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 31%

---

# Zugriffsinformationen für Repositorys {#accessing-repos}

Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung in Cloud Manager auf Ihre Adobe-verwalteten Git-Repositorys zugreifen und diese verwalten können.

## Zugriff auf Repository-Informationen über die Seite &quot;Übersicht&quot; {#overview-page}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf Ihrer Seite **Programmübersicht** zur Karte **Pipelines** .

   ![Schaltfläche „Auf Repository-Informationen zugreifen“ auf der Karte „Umgebungen“](assets/pipelines-card.png)

1. Klicken Sie auf **Zugriff auf Repo Info**. Im Dialogfeld **Repository Info for..** können Sie Folgendes anzeigen:

   * Der Git-Benutzername.
   * Das Git-Kennwort.
   * Die URL zum Cloud Manager Git-Repository.
   * Vordefinierte Git-Befehle zum schnellen Hinzufügen einer Remote-Verbindung zu Ihrem Git-Repo- und Push-Code.

   ![Fenster „Repository-Informationen“](assets/access-repo-info.png)

1. Um auf das Kennwort zugreifen zu können, muss ein neues Kennwort generiert werden. Klicken Sie auf **`Generate password`**.

1. Bestätigen Sie im Dialogfeld **Sind Sie sicher ...** die Kennworterstellung durch Klicken auf **Kennwort generieren**.

   ![Kennwortgenerierung bestätigen](assets/confirm-password-generation.png)

1. Im Feld **Kennwort** wird das Kennwort generiert. Klicken Sie auf das Kopiersymbol, um es in die Zwischenablage zu kopieren.

   * Beim Generieren eines Kennworts wird das vorherige Kennwort ungültig.
   * Cloud Manager speichert Ihr Kennwort nicht. Vergewissern Sie sich, dass Sie dieses Kennwort sicher speichern.
   * Wenn Sie das Kennwort verlieren, müssen Sie ein neues generieren.

   ![Beispiel eines generierten Kennworts](assets/generated-password.png)

Mithilfe dieser Anmeldeinformationen können Sie eine lokale Kopie des Repositorys klonen, Änderungen an diesem lokalen Repository vornehmen und etwaige Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.

>[!NOTE]
>
>* Die Option **Zugriff auf Repo Info** ist für Benutzer mit der Rolle **Entwickler** oder mit der Rolle **Bereitstellungsmanager** oder beidem sichtbar.
>* Durch die Schaltfläche **Auf Repository-Informationen zugreifen** werden nur die Repository-Zugriffsinformationen für von Adobe verwaltete Repositorys angezeigt. Zugriffsinformationen über [private Repositorys](private-repositories.md) sind in Cloud Manager nicht verfügbar.

## Zugriff auf Repository-Informationen über das Fenster &quot;Repositorys&quot; {#repositories-window}

Die Schaltfläche **Zugriff auf Repo Info** ist auch in der Symbolleiste des Fensters [**Repositorys**](managing-repositories.md) verfügbar. Es werden dieselben Informationen zum Zugriff auf von Adobe verwaltete Repositorys angezeigt.

## Zugriffskennwort sperren {#revoke-password}

Sie können jederzeit ein Zugangskennwort sperren lassen. [Erstellen Sie ein Support-Ticket für eine solche Anfrage](https://experienceleague.adobe.com/?lang=de?support-solution=Experience+Manager&amp;support-tab=home#support).

Das Ticket wird mit hoher Priorität behandelt und normalerweise innerhalb eines Tages widerrufen.
