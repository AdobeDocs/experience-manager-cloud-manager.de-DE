---
title: Hinzufügen privater Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen privaten GitHub-Repositorys einrichten.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 40%

---


# Hinzufügen privater Repositorys in Cloud Manager {#private-repositories}

Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen privaten GitHub-Repositorys einrichten.

## Übersicht {#overview}

Durch die Konfiguration von Cloud Manager mit Ihren privaten GitHub-Repositorys können Sie Code direkt in GitHub validieren, sodass eine regelmäßige Synchronisierung mit dem Adobe-Repository nicht mehr erforderlich ist.

>[!NOTE]
>
>Diese Funktion ist nur für öffentliche GitHub-Repositorys verfügbar. Unterstützung für selbstgehostetes GitHub-Repositorys ist nicht verfügbar.

## Konfiguration {#configuration}

Die Konfiguration erfolgt in zwei Hauptschritten:

1. [Repository hinzufügen](#add-repo)
1. [Validierung der Eigentümerschaft eines privaten Repositorys](#validate-ownership)

### Repository hinzufügen {#add-repo}

1. Klicken Sie in Cloud Manager auf der Seite **Programmübersicht** auf die Registerkarte **Repositorys** , um zur Seite **Repositorys** zu wechseln, und klicken Sie auf **Repository hinzufügen**.

1. Wählen Sie im Dialogfeld **Repository hinzufügen** die Option **Privates Repository** als Repository-Typ aus.

1. Angabe von Details zu Ihrem Repository

   * **Repository-Name** – Ein aussagekräftiger Name
   * **Repository-URL** – Die URL des Repositorys, die mit `.git` enden muss
   * **Beschreibung** (optional) – Eine längere Beschreibung des Repositorys nach Bedarf

   ![Eigenes Repository hinzufügen](/help/assets/repositories/add-own-github.png)

1. Klicken Sie auf **Speichern**.

>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/managing-code/managing-repositories.md).

### Validierung der Eigentümerschaft eines privaten Repositorys {#validate-ownership}

Cloud Manager kennt jetzt Ihr GitHub-Repository, benötigt aber noch den Zugriff darauf. Um Zugriff zu gewähren, müssen Sie die Adobe GitHub-App installieren und sicherstellen, dass Sie Eigentümerin bzw. Eigentümer des angegebenen Repositorys sind.

1. Nachdem Sie Ihr eigenes Repository hinzugefügt haben, wird das Dialogfeld **Validierung der Eigentümerschaft des privaten Repositorys** angezeigt.

   ![Validierung der Eigentümerschaft eines privaten Repositorys](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager verwendet eine GitHub-App, um sicher mit Ihrem Repository zu interagieren.

   Ein Eigentümer Ihrer GitHub-Organisation muss die App unter `https://github.com/apps/cloud-manager-for-aem` installieren und Zugriff auf das Repository gewähren. Weitere Informationen finden Sie in der GitHub-Dokumentation .

1. Um die Sicherheit zu erhöhen, erstellen Sie eine geheime Datei in der Standardverzweigung Ihres Repositorys. Klicken Sie auf **Erzeugen**.

1. Bestätigen Sie die Erstellung der geheimen Datei, indem Sie auf **Bestätigen** klicken.

   ![Geheimnisgenerierung bestätigen](/help/assets/repositories/confirm-generation.png)

1. Zurück im Dialogfeld **Validierung der Eigentümerschaft des privaten Repositorys** hat Cloud Manager den Inhalt im Feld **Geheimer Dateiinhalt** generiert. Kopieren Sie den Inhalt aus diesem Feld.

   Der Inhalt der geheimen Datei wird nur einmal angezeigt. Wenn Sie den Inhalt nicht kopieren, bevor Sie dieses Fenster schließen, müssen Sie das Geheimnis neu generieren.

   ![Inhalt der geheimen Datei kopieren](/help/assets/repositories/new-secret.png)

1. Erstellen Sie in der Standardverzweigung Ihres GitHub-Repositorys eine neue Datei mit dem Namen `.well-known/adobe/cloud-manager-challenge`, fügen Sie den geheimen Dateiinhalt in diese Datei ein und speichern Sie sie.

1. Nachdem die App installiert wurde und die geheime Datei im Repository vorhanden ist, können Sie im Dialogfeld **Validierung der privaten Repository-Eigentümerschaft** auf **Validieren** klicken.

Die App kann installiert werden und Sie können eine geheime Datei in beliebiger Reihenfolge generieren. Beide Schritte müssen jedoch vor der Validierung ausgeführt werden.

Bis zur Validierung wird das Repository mit einem roten Symbol aufgeführt, das angibt, dass es noch nicht validiert wurde und noch nicht verwendet werden kann.

![Nicht validiertes Repo](/help/assets/repositories/unvalidated-repo.png)

Beachten Sie, dass in der Spalte **Typ** die von Adobe bereitgestellten Repositorys (**Adobe**) und Ihre eigenen GitHub-Repositorys (**GitHub**) leicht erkennbar aufgeführt sind.

Um später zum Repository zurückzukehren und die Validierung abzuschließen, wechseln Sie zur Seite **Repositorys** . Klicken Sie auf die Suchschaltfläche neben dem von Ihnen hinzugefügten GitHub-Repository und wählen Sie **Eigentumsprüfung** aus dem Dropdownmenü aus.

## Verwenden privater Repositorys mit Cloud Manager {#using}

Nachdem das GitHub-Repository in Cloud Manager validiert wurde, ist die Integration abgeschlossen und Sie können das Repository mit Cloud Manager verwenden.

1. Wenn Sie eine Pull-Anforderung erstellen, wird automatisch eine GitHub-Prüfung gestartet.

   ![GitHub-Prüfungen](/help/assets/repositories/github-checks.png)

1. Für jede Pull-Anforderung wird automatisch eine [vollständige Stack-Code-Qualitäts-Pipeline](/help/using/managing-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

1. Die GitHub-Prüfung verbleibt im Status &quot;Wird ausgeführt&quot;, bis die Code-Qualitätsprüfungen abgeschlossen sind. Die Ergebnisse der Code-Qualität werden dann an die GitHub-Prüfung übertragen.

   ![GitHub-Code-Qualitätsprüfungen](/help/assets/repositories/github-code-quality.png)

Wenn die Pull-Anfrage geschlossen oder zusammengeführt wird, wird die erstellte vollständige Stack-Code-Qualitäts-Pipeline automatisch gelöscht.

>[!TIP]
>
>Im Dokument [Anmerkungen zur GitHub-Prüfung](github-annotations.md) finden Sie Details zu den Informationen, die bei der Ausführung von Pull-Anfrageprüfungen über GitHub bereitgestellt werden.

>[!TIP]
>
>Sie können die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren. Weitere Informationen finden Sie unter [GitHub-Prüfkonfiguration für private Repositorys](github-check-config.md) .

## Zuordnen privater Repositorys zu Pipelines {#pipelines}

Validierte private Repositorys können [Vollstapelpipelines](/help/overview/ci-cd-pipelines.md) zugeordnet werden.

## Einschränkungen {#limitations}

Bei der Verwendung privater Repositorys mit Cloud Manager gelten bestimmte Einschränkungen.

* Sie können die Überprüfung der Pull-Anforderung nicht mithilfe der GitHub-Prüfung von Cloud Manager anhalten. Wenn das GitHub-Repository in Cloud Manager validiert wird, versucht Cloud Manager, die für dieses Repository erstellten Pull-Anforderungen zu überprüfen.
* Wenn die Adobe GitHub-App aus Ihrer GitHub-Organisation entfernt wird, entfernt diese Aktion die Überprüfungsfunktion für Pull-Anforderungen für alle Repositorys.
* Bei Verwendung privater Repositorys in Produktions-Vollstapelpipelines wird kein Git-Tag erstellt und gesendet.
* Pipelines, die private Repositorys und den On-Commit-Build-Trigger verwenden, werden nicht automatisch gestartet, wenn ein neues Commit in die ausgewählte Verzweigung verschoben wird.
* Die [Funktion zur Wiederverwendung von Artefakten](/help/getting-started/project-setup.md#build-artifact-reuse) gilt nicht für private Repositorys.
