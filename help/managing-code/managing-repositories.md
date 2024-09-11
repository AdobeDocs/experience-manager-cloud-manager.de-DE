---
title: Verwalten von Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie in Cloud Manager Ihre Git-Repositorys erstellen, anzeigen und bearbeiten.
exl-id: 384b197d-f7a7-4022-9b16-9d83ab788966
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '641'
ht-degree: 100%

---


# Cloud Manager-Repositorys {#cloud-manager-repos}

Erfahren Sie, wie Sie in Cloud Manager Ihre Git-Repositorys erstellen, anzeigen und bearbeiten.

## Überblick {#overview}

Repositorys werden zum Speichern und Verwalten des Projekt-Codes mithilfe von Git verwendet. Für jedes Programm, das Sie in Cloud Manager erstellen, wird ein von Adobe verwaltetes Repository erstellt.

Sie können zusätzliche, von Adobe verwaltete Repositorys erstellen und auch eigene private Repositorys hinzufügen. Alle mit Ihrem Programm verknüpften Repositorys können im Fenster **Repositorys** eingesehen werden.

In Cloud Manager erstellte Repositorys stehen Ihnen auch beim Hinzufügen oder Bearbeiten von Pipelines zur Verfügung. Weitere Informationen finden Sie unter [CI/CD-Pipelines](/help/overview/ci-cd-pipelines.md).

Für jede Pipeline gibt es ein einzelnes primäres Repository oder eine Verzweigung. Mit der [Unterstützung von Git-Untermodulen](git-submodules.md) können jedoch viele sekundäre Verzweigungen zum Zeitpunkt der Erstellung einbezogen werden.

## Fenster „Repositorys“ {#repositories-window}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Wählen Sie auf der Seite **Programmübersicht** die Registerkarte **Repositorys** und wechseln Sie zu der Seite **Repositorys**.

1. Im Fenster **Repositorys** werden alle Repositorys angezeigt, die mit Ihrem Programm verknüpft sind.

   ![Fenster „Repositorys“](assets/repositories.png)

Das Fenster **Repositorys** zeigt Details zu den Repositorys:

* Der Repository-Typ
   * **Adobe** zeigt von Adobe verwaltete Repositorys an
   * **GitHub** zeigt private, von Ihnen verwaltete GitHub-Repositorys an
* Zeitpunkt der Erstellung
* Pipelines, die mit dem Repository verknüpft sind

Sie können das Repository im Fenster auswählen und auf die Schaltfläche mit den Auslassungspunkten klicken, um das ausgewählte Repository zu bearbeiten.

* **[Verzweigungen prüfen/Projekt erstellen](#check-branches)** (nur für Adobe-Repositorys verfügbar)
* **[Repository-URL kopieren](#copy-url)**
* **[Anzeigen und aktualisieren](#view-update)**
* **[Löschen](#delete)**

![Repository-Aktionen](assets/repository-actions.png)

## Hinzufügen von Repositorys {#adding-repositories}

Klicken Sie im Fenster **Repositorys** auf die Schaltfläche **Repository hinzufügen**, um den Assistenten **Repository hinzufügen** zu starten.

![Assistent „Repository hinzufügen“](assets/add-repository-wizard.png)

Cloud Manager unterstützt sowohl Repositorys, die von Adobe verwaltet werden (**Adobe-Repository**), als auch Ihre eigenen, selbst verwalteten Repositorys (**Privates Repository**). Die erforderlichen Felder unterscheiden sich je nach dem Repository-Typ, den Sie hinzufügen möchten.

Siehe [Hinzufügen von Adobe-Repositorys in Cloud Manager](adobe-repositories.md).
Siehe [Hinzufügen von privaten Repositorys in Cloud Manager](private-repositories.md).

>[!NOTE]
>
>Eine Person muss über die Rolle **Bereitstellungs-Manager** oder **Geschäftsinhaber** verfügen, um ein Repository hinzufügen zu können.
>
>Für jedes Unternehmen oder IMS-Organisation gibt es eine Grenze von 300 Repositorys über alle Programme hinweg.

## Zugreifen auf Repository-Informationen {#repo-info}

Wenn Sie sich Ihre Repositorys im Fenster **Repositorys** ansehen, können Sie die Details zum programmgesteuerten Zugriff auf die von Adobe verwalteten Repositorys anzeigen, indem Sie in der Symbolleiste auf die Schaltfläche **Auf Repository-Informationen zugreifen** klicken.

![Repository-Informationen](assets/access-repo-info.png)

Das Fenster **Repository-Informationen** mit den Details wird geöffnet. Weitere Informationen zum Zugreifen auf Repository-Informationen finden Sie unter [Zugriff auf Repository-Informationen](accessing-repositories.md).

## Überprüfen von Verzweigungen {#check-branches}

Mit der Aktion **Verzweigungen überprüfen/Projekt erstellen** werden je nach dem Status des Repositorys zwei Funktionen ausgeführt.

Wenn das Repository neu erstellt wurde, erstellt die Aktion ein Beispielprojekt basierend auf dem [AEM-Projektarchetyp](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/overview).

Wenn im Repository bereits ein Beispielprojekt erstellt wurde, prüft es den Status des Repositorys und seiner Verzweigungen und gibt zurück, dass bereits ein Beispielprojekt vorhanden ist.

![Aktion „Verzweigungen überprüfen“](assets/check-branches.png)

## Repository-URL kopieren {#copy-url}

Die Aktion **Repository-URL kopieren** kopiert die URL des im Fenster **Repositorys** ausgewählten Repositorys in die Zwischenablage, damit sie an anderer Stelle verwendet werden kann.

## Anzeigen und Aktualisieren {#view-update}

Die Aktion **Anzeigen/Aktualisieren** öffnet das Dialogfeld **Repository aktualisieren**. Dort können Sie den **Namen** und die **Repository-URL-Vorschau** anzeigen und die **Beschreibung** des Repositorys aktualisieren.

![Anzeigen und Aktualisieren von Repository-Informationen](assets/update-repository.png)

## Löschen {#delete}

Die Aktion **Löschen** entfernt das Repository aus Ihrem Projekt. Ein Repository kann nicht gelöscht werden, wenn es mit einer Pipeline verknüpft ist.

![Löschen](assets/delete.png)

Wenn ein Repository in Cloud Manager gelöscht wird, wird es als gelöscht markiert und steht Benutzenden nicht mehr zur Verfügung. Es wird jedoch zu Wiederherstellungszwecken im System beibehalten.

Wenn Sie versuchen, ein neues Repository zu erstellen, nachdem Sie ein Repository mit demselben Namen gelöscht haben, erhalten Sie die Fehlermeldung `An error has occurred while trying to create repository. Contact your CSE or Adobe Support.`

Wenn Sie diese Fehlermeldung erhalten, wenden Sie sich an den Adobe-Support, damit dieser Ihnen beim Umbenennen des gelöschten Repositorys helfen kann, oder wählen Sie einen anderen Namen für Ihr neues Repository.
