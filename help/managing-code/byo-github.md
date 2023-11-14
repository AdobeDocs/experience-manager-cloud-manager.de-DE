---
title: Arbeiten mit Ihren eigenen GitHub-Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Cloud Manager für die Arbeit mit Ihren eigenen GitHub-Repositorys einrichten.
feature: Release Information
source-git-commit: 76a3dc6df41032488a3cfe11d0c72769562b96df
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 1%

---


# Arbeiten mit Ihren eigenen GitHub-Repositorys in Cloud Manager {#byo-github}

Durch die Konfiguration von Cloud Manager für die Verwendung mit Ihren eigenen GitHub-Repositorys können Sie Ihren Code direkt in Ihrem GitHub-Repository über Cloud Manager validieren, sodass Sie Ihren Code nicht konsistent mit dem Adobe-Repository synchronisieren müssen.

>[!NOTE]
>
>Diese Funktion steht nur für [das Programm für den frühen Anwender.](/help/release-notes/current.md#early-adoption)

## Konfiguration {#configuration}

Die Konfiguration besteht aus zwei Hauptschritten:

1. [Repository hinzufügen](#add-repo)
1. [Private Repository-Eigentümervalidierung](#validate-ownership)

### Repository hinzufügen {#add-repo}

1. In Cloud Manager über die **Programmübersicht** Seite, tippen oder klicken Sie auf **Repositorys** Registerkarte, um zu der **Repositorys** Seite und klicken Sie auf **Repository hinzufügen**.

1. Im **Repository hinzufügen** Dialogfeld auswählen **Privates Repository** als Repository-Typ.

1. Details zu Ihrem Repository angeben

   * **Repository-Name** - Ein ausdrucksstarker Name
   * **Repository-URL** - Die URL des Repositorys, die enden muss in `.git`
   * **Beschreibung** (optional) - Eine längere Beschreibung des Repositorys nach Bedarf

   ![Eigenes Repository hinzufügen](/help/assets/repositories/add-own-github.png)

1. Tippen oder klicken Sie auf **Speichern**.

>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie im Dokument [Cloud Manager-Repositorys.](/help/managing-code/repositories.md)

### Validierung des Eigentums an privaten Repositorys {#validate-ownership}

Cloud Manager weiß jetzt von Ihrem GitHub-Repository, muss aber trotzdem darauf zugreifen. Um Zugriff zu gewähren, müssen Sie die Adobe GitHub-App installieren und sicherstellen, dass Sie Eigentümer des angegebenen Repositorys sind.

1. Nachdem Sie Ihr eigenes Repository hinzugefügt haben, wird die **Validierung des Eigentums an privaten Repositorys** wird geöffnet.

   ![Validierung des Eigentums an privaten Repositorys](/help/assets/repositories/private-repo-validate.png)

1. Cloud Manager verwendet eine GitHub-App, um sicher mit Ihrem Repository zu interagieren.
   * Ein Eigentümer Ihrer GitHub-Organisation muss die App installieren, die sich unter `https://github.com/apps/cloud-manager-for-aem-stage` und gewähren Zugriff auf das Repository.
   * Weitere Informationen dazu finden Sie in der GitHub-Dokumentation .

1. Um die Sicherheit zu erhöhen, müssen Sie eine geheime Datei in der Standardverzweigung Ihres Repositorys erstellen. Tippen oder klicken **Erzeugen**.

1. Bestätigen Sie die Erstellung der geheimen Datei, indem Sie auf **Bestätigen**.

   ![Geheimgenerierung bestätigen](/help/assets/repositories/confirm-generation.png)

1. Zurück im **Validierung des Eigentums an privaten Repositorys** -Fenster hat Cloud Manager den Inhalt der privaten Datei im **Geheimer Dateiinhalt** -Feld. Kopieren Sie den Inhalt aus diesem Feld.

   * Der Inhalt der geheimen Datei wird nur einmal angezeigt. Wenn Sie den Inhalt nicht kopieren, bevor Sie dieses Fenster schließen, müssen Sie das Geheimnis neu generieren.

   ![Inhalt der geheimen Datei kopieren](/help/assets/repositories/new-secret.png)

1. Erstellen Sie im Standardzweig Ihres GitHub-Repositorys eine neue Datei mit dem Namen `.well-known/adobe/cloud-manager-challenge` und fügen Sie den geheimen Dateiinhalt in diese Datei ein und speichern Sie.

1. Sobald die App installiert ist und die geheime Datei im Repository vorhanden ist, können Sie auf tippen oder klicken **Bestätigen** im **Validierung des Eigentums an privaten Repositorys** angezeigt.

Die App kann installiert und geheime Dateien können in beliebiger Reihenfolge erstellt werden. Beide Schritte müssen jedoch vor der Validierung ausgeführt werden.

Bis zur Validierung wird das Repository mit einem roten Symbol aufgeführt, das angibt, dass es noch nicht validiert wurde und noch nicht verwendet werden kann.

![Nicht validierte Repo](/help/assets/repositories/unvalidated-repo.png)

Beachten Sie Folgendes: **Typ** -Spalte identifiziert einfach von Adobe bereitgestellte Repositorys (**Adobe**) und Ihre eigenen GitHub-Repositorys (**GitHub**).

Wenn Sie zu einem späteren Zeitpunkt zum Repository zurückkehren müssen, um die Validierung abzuschließen, muss die **Repositorys** auf die Suchschaltfläche in der Zeile, die das soeben hinzugefügte GitHub-Repository darstellt, tippen oder klicken Sie darauf und wählen Sie **Validierung des Eigentums** aus dem Dropdown-Menü.

## Verwenden eigener GitHub-Repositorys mit Cloud Manager {#using}

Nachdem das GitHub-Repository in Cloud Manager validiert wurde, ist die Integration abgeschlossen und Sie können das Repository mit Cloud Manager verwenden.

1. Wenn Sie eine Pull-Anforderung erstellen, beginnt automatisch eine GitHub-Prüfung.

   ![GitHub-Prüfungen](/help/assets/repositories/github-checks.png)

1. Für jede Pull-Anforderung wird eine [Vollständige Stack-Code-Qualitäts-Pipeline](/help/using/managing-pipelines.md) automatisch erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anforderung gestartet.

1. Die GitHub-Prüfung verbleibt im Status &quot;Wird ausgeführt&quot;, bis die Code-Qualitätsprüfungen abgeschlossen sind. Die Ergebnisse der Code-Qualität werden dann an die GitHub-Prüfung übertragen.

   ![GitHub-Code-Qualitätsprüfungen](/help/assets/repositories/github-code-quality.png)

Wenn die Pull-Anforderung geschlossen oder zusammengeführt wird, wird die erstellte vollständige Stack-Code-Qualitäts-Pipeline automatisch gelöscht.

## Einschränkungen {#limitations}

Beachten Sie bei der Verwendung Ihrer eigenen GitHub-Repositorys mit Cloud Manager die folgenden Einschränkungen.

* Sie können die GitHub-Repositorys nicht als direkte Repository-Quelle für die von Ihnen verwalteten Pipelines verwenden.
   * Diese Funktion ist geplant.
* Sie können die Überprüfung der Pull-Anforderung nicht mithilfe der GitHub-Prüfung vom Cloud Manager anhalten.
   * Wenn das GitHub-Repository in Cloud Manager validiert wird, versucht Cloud Manager immer, die für dieses Repository erstellten Pull-Anforderungen zu validieren.
Wenn die Adobe GitHub-App aus Ihrer GitHub-Organisation entfernt wird, wird dadurch die Überprüfungsfunktion für Pull-Anforderungen für alle Repositorys entfernt.
