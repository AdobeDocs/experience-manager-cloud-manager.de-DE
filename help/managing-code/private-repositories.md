---
title: Hinzufügen von privaten Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen privaten GitHub-Repositorys einrichten.
feature: Release Information
exl-id: e0d103c9-c147-4040-bf53-835e93d78a0b
source-git-commit: 15e733117b4458cc53dec309dad5bde8cb17029f
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 100%

---


# Hinzufügen von privaten Repositorys in Cloud Manager {#private-repositories}

Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen privaten GitHub-Repositorys einrichten.

## Übersicht {#overview}

Indem Sie Cloud Manager für die Verwendung mit Ihren eigenen privaten GitHub-Repositorys konfigurieren, können Sie Ihren Code über Cloud Manager direkt in Ihrem GitHub-Repository validieren, sodass Sie ihn nicht ständig mit dem Adobe-Repository synchronisieren müssen.

>[!NOTE]
>
>Diese Funktion ist nur für öffentliche GitHub-Repositorys verfügbar. Unterstützung für selbstgehostetes GitHub-Repositorys ist nicht verfügbar.

## Konfiguration {#configuration}

Die Konfiguration erfolgt in zwei Hauptschritten:

1. [Repository hinzufügen](#add-repo)
1. [Validierung der Eigentümerschaft eines privaten Repositorys](#validate-ownership)

### Repository hinzufügen {#add-repo}

1. Tippen oder klicken Sie in Cloud Manager auf der Seite **Programmübersicht** auf die Registerkarte **Repositorys**, um zur Seite **Repositorys** zu wechseln, und dann auf **Repository hinzufügen**.

1. Wählen Sie im Dialogfeld **Repository hinzufügen** als Repository-Typ **Privates Repository**.

1. Angabe von Details zu Ihrem Repository

   * **Repository-Name** – Ein aussagekräftiger Name
   * **Repository-URL** – Die URL des Repositorys, die mit `.git` enden muss
   * **Beschreibung** (optional) – Eine längere Beschreibung des Repositorys nach Bedarf

   ![Eigenes Repository hinzufügen](/help/assets/repositories/add-own-github.png)

1. Tippen oder klicken Sie auf **Speichern**.

>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie im Dokument [Cloud Manager-Repositorys](/help/managing-code/managing-repositories.md).

### Validierung der Eigentümerschaft eines privaten Repositorys {#validate-ownership}

Cloud Manager kennt jetzt Ihr GitHub-Repository, benötigt aber noch den Zugriff darauf. Um Zugriff zu gewähren, müssen Sie die Adobe GitHub-App installieren und sicherstellen, dass Sie Eigentümerin bzw. Eigentümer des angegebenen Repositorys sind.

1. Nachdem Sie Ihr eigenes Repository hinzugefügt haben, wird der Dialog **Validierung der Eigentümerschaft eines privaten Repositorys** geöffnet.

   ![Validierung der Eigentümerschaft eines privaten Repositorys](/help/assets/repositories/private-repo-validate.png)

1. Zur sicheren Interaktion mit Ihrem Repository verwendet Cloud Manager eine GitHub-App.
   * Eine Eigentümerin bzw. ein Eigentümer Ihrer GitHub-Organisation muss die App unter `https://github.com/apps/cloud-manager-for-aem` installieren und Zugriff auf das Repository gewähren.
   * Weitere Informationen dazu finden Sie in der GitHub-Dokumentation.

1. Um die Sicherheit zu erhöhen, müssen Sie eine geheime Datei in der Standardverzweigung Ihres Repositorys erstellen. Tippen oder klicken Sie auf **Generieren**.

1. Bestätigen Sie die Generierung der geheimen Datei, indem Sie auf **Bestätigen** klicken.

   ![Geheimnisgenerierung bestätigen](/help/assets/repositories/confirm-generation.png)

1. Im Fenster **Validierung der Eigentümerschaft eines privaten Repositorys** hat Cloud Manager den Inhalt der privaten Datei im Feld **Geheimer Dateiinhalt** generiert. Kopieren Sie den Inhalt aus diesem Feld.

   * Der Inhalt der geheimen Datei wird nur einmal angezeigt. Wenn Sie den Inhalt nicht kopieren, bevor Sie dieses Fenster schließen, müssen Sie die geheime Datei neu generieren.

   ![Inhalt der geheimen Datei kopieren](/help/assets/repositories/new-secret.png)

1. Erstellen Sie in der Standardverzweigung Ihres GitHub-Repositorys eine neue Datei mit dem Namen `.well-known/adobe/cloud-manager-challenge`, fügen Sie den geheimen Dateiinhalt in diese Datei ein und speichern Sie sie.

1. Sobald die App installiert ist und sich die geheime Datei im Repository befindet, können Sie im Dialogfeld **Validierung der Eigentümerschaft eines privaten Repositorys** auf **Bestätigen** tippen oder klicken.

Die Installation der App und die Erstellung der geheimen Datei kann in jeder beliebigen Reihenfolge erfolgen. Beide Schritte müssen jedoch vor der Validierung ausgeführt werden.

Bis zur Validierung ist das Repository mit einem roten Symbol gekennzeichnet, das angibt, dass es noch nicht validiert wurde und noch nicht verwendet werden kann.

![Nicht validiertes Repo](/help/assets/repositories/unvalidated-repo.png)

Beachten Sie, dass in der Spalte **Typ** die von Adobe bereitgestellten Repositorys (**Adobe**) und Ihre eigenen GitHub-Repositorys (**GitHub**) leicht erkennbar aufgeführt sind.

Wenn Sie zu einem späteren Zeitpunkt zum Repository zurückkehren müssen, um die Validierung abzuschließen, klicken oder tippen Sie auf der Seite **Repositorys** auf die Schaltfläche mit den Auslassungspunkten in der Zeile mit dem soeben von Ihnen hinzugefügten GitHub-Repository und wählen Sie **Eigentümervalidierung** aus dem Dropdown-Menü.

## Verwenden privater Repositorys mit Cloud Manager {#using}

Nachdem das GitHub-Repository in Cloud Manager validiert wurde, ist die Integration abgeschlossen und Sie können das Repository mit Cloud Manager verwenden.

1. Beim Erstellen einer Pull-Anfrage wird automatisch eine GitHub-Prüfung ausgeführt.

   ![GitHub-Prüfungen](/help/assets/repositories/github-checks.png)

1. Für jede Pull-Anfrage wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/using/managing-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

1. Die GitHub-Prüfung verbleibt im Status „Wird ausgeführt“, bis die Code-Qualitätsprüfungen abgeschlossen sind. Die Ergebnisse der Code-Qualität werden dann an die GitHub-Prüfung übertragen.

   ![GitHub-Code-Qualitätsprüfungen](/help/assets/repositories/github-code-quality.png)

Wenn die Pull-Anfrage geschlossen oder zusammengeführt wird, wird die erstellte vollständige Stack-Code-Qualitäts-Pipeline automatisch gelöscht.

>[!TIP]
>
>Im Dokument [Anmerkungen zur GitHub-Prüfung](github-annotations.md) finden Sie Details zu den Informationen, die bei der Ausführung von Pull-Anfrageprüfungen über GitHub bereitgestellt werden.

>[!TIP]
>
>Sie können die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren. Weitere Informationen finden Sie im Dokument [Konfiguration der GitHub-Prüfung für private Repositorys](github-check-config.md).

## Zuordnen von privaten Repositorys zu Pipelines {#pipelines}

Validierte private Repositorys können [Full-Stack-Pipelines](/help/overview/ci-cd-pipelines.md) zugeordnet werden.

## Einschränkungen {#limitations}

Bei der Verwendung privater Repositorys mit Cloud Manager gelten bestimmte Einschränkungen.

* Sie können die Überprüfung der Pull-Anfrage nicht mithilfe der GitHub-Prüfung über Cloud Manager anhalten.
   * Während der Validierung des GitHub-Repositorys versucht Cloud Manager immer, die für dieses Repository erstellten Pull-Anfragen zu validieren.
* Wenn die Adobe GitHub-App aus Ihrer GitHub-Organisation entfernt wird, wird dadurch auch die Überprüfungsfunktion für Pull-Anfragen für alle Repositorys entfernt.
* Bei Verwendung privater Repositorys in Full-Stack-Produktions-Pipelines wird kein Git-Tag erstellt und gesendet.
* Pipelines, die private Repositorys und den On-Commit-Build-Trigger verwenden, werden nicht automatisch gestartet, wenn ein neues Commit in die ausgewählte Verzweigung verschoben wird.
* Die [Funktion zur Wiederverwendung von Artefakten](/help/getting-started/project-setup.md#build-artifact-reuse) gilt nicht für private Repositorys.
