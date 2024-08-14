---
title: Das Inhaltskopie-Tool
description: Mit dem Cloud Manager-Werkzeug zum Kopieren von Inhalten können Benutzer bei Bedarf veränderliche Inhalte aus AMS-gehosteten AEM 6.x-Produktionsumgebungen in niedrigere Testumgebungen kopieren.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 2563c58431e58d2fc5917a2ad88835bbdd4224f2
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 48%

---


# Das Werkzeug zum Kopieren von Inhalten {#content-copy}

Mit dem Cloud Manager-Werkzeug zum Kopieren von Inhalten können Benutzer bei Bedarf veränderliche Inhalte aus AMS-gehosteten AEM 6.x-Produktionsumgebungen in niedrigere Testumgebungen kopieren.

## Einführung {#introduction}

Aktuelle, echte Daten sind für Tests, Validierung und Benutzerakzeptanz nützlich. Mit dem Werkzeug zum Kopieren von Inhalten können Sie Inhalte aus Ihrer Produktions-AMS-gehosteten AEM 6.x-Umgebung in Staging- oder Entwicklungsumgebungen kopieren. Dieser Workflow unterstützt verschiedene Testszenarien.

Ein Inhaltssatz definiert den zu kopierenden Inhalt. Ein Inhaltssatz enthält eine Liste von JCR-Pfaden mit dem zu kopierenden veränderlichen Inhalt. Der Inhalt wird von einer Quellumgebung in eine Zielumgebung verschoben. Alle Aktionen erfolgen innerhalb desselben Cloud Manager-Programms.

Die folgenden Pfade sind in einem Inhaltsset zulässig:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Beim Kopieren von Inhalten ist die Quellumgebung die Datenquelle.

* Wenn Sie Inhalte in der Zielumgebung bearbeiten, überschreibt der Quellinhalt ihn, wenn die Pfade übereinstimmen.
* Wenn die Pfade unterschiedlich sind, wird der Inhalt der Quelle mit dem Inhalt des Ziels zusammengeführt.

## Berechtigungen {#permissions}

Um das Werkzeug zum Kopieren von Inhalten zu verwenden, muss der Benutzer der Rolle **Bereitstellungsmanager** in der Quell- und Zielumgebung zugewiesen sein.

## Inhaltssatz erstellen {#create-content-set}

Bevor Inhalt kopiert werden kann, muss ein Content-Set definiert werden. Nach der Definition können Content-Sets zum Kopieren von Inhalten wiederverwendet werden. Gehen Sie wie folgt vor, um ein Content-Set zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Navigieren Sie auf dem Bildschirm **Umgebungen** zur Seite **Inhaltssets** .

1. Klicken Sie oben rechts im Bildschirm auf **Inhaltsset hinzufügen**.

   ![Content-Sets](/help/assets/content-sets.png)

1. Geben Sie auf der Registerkarte **Details** des Assistenten einen Namen und eine Beschreibung für den Inhaltssatz ein und klicken Sie auf **Weiter**.

   ![Content-Set-Details](/help/assets/add-content-set-details.png)

1. Auf der Registerkarte **Inhaltspfade** des Assistenten geben Sie die Pfade der veränderbaren Inhalte an, die in das Content-Set aufgenommen werden sollen.

   1. Geben Sie den Pfad in das Feld **Einschlusspfad hinzufügen** ein.
   1. Klicken Sie auf **Pfad hinzufügen**, um den Pfad zum Inhaltssatz hinzuzufügen.
   1. Klicken Sie bei Bedarf erneut auf **Pfad hinzufügen**.

   ![Hinzufügen von Pfaden zu Content-Sets](/help/assets/add-content-set-paths.png)

1. Wenn Sie Ihr Content-Set verfeinern oder einschränken möchten, können Sie Unterpfade ausschließen.

   1. Klicken Sie in der Liste der eingeschlossenen Pfade neben dem Pfad, den Sie beschränken müssen, auf das Symbol **Unterpfade zum Ausschließen hinzufügen** .
   1. Geben Sie den Unterpfad ein, der vom ausgewählten Pfad ausgeschlossen werden soll.
   1. Klicken Sie auf **Pfad ausschließen**.
   1. Klicken Sie erneut auf **Unterpfade zum Ausschließen hinzufügen** , um weitere Pfade hinzuzufügen, die bei Bedarf ausgeschlossen werden sollen.

   ![Ausschließen von Pfaden](/help/assets/add-content-set-paths-excluded.png)

1. Sie können die angegebenen Pfade bei Bedarf ändern.

   1. Klicken Sie auf den `X` neben den ausgeschlossenen Unterpfaden, um sie zu löschen.
   1. Klicken Sie auf die Suchschaltfläche neben den Pfaden, um die Optionen **Bearbeiten** und **Löschen** anzuzeigen.

   ![Bearbeiten der Pfadliste](/help/assets/add-content-set-excluded-paths.png)

1. Klicken Sie auf **Erstellen** , um den Inhaltssatz zu erstellen.

Das Content-Set kann jetzt zum Kopieren von Inhalten zwischen Umgebungen verwendet werden.

>[!NOTE]
>
>Sie können einem Content-Set bis zu 50 Pfade hinzufügen.
>Für ausgeschlossene Pfade gibt es keine Beschränkung.

## Bearbeiten eines Inhaltssatzes {#edit-content-set}

Hierbei führen Sie ähnliche Schritte wie beim Erstellen eines Content-Sets aus. Wählen Sie statt auf **Inhaltsset hinzufügen** einen vorhandenen Satz aus der Konsole aus und wählen Sie im Suchmenü die Option **Bearbeiten** aus.

![Bearbeiten des Content-Sets](/help/assets/edit-content-set.png)

Beim Bearbeiten des Content-Sets müssen Sie möglicherweise die konfigurierten Pfade erweitern, um die ausgeschlossenen Unterpfade anzuzeigen.

## Kopieren von Inhalten {#copy-content}

Nachdem ein Content-Set erstellt wurde, können Sie es zum Kopieren von Inhalten verwenden. Führen Sie die folgenden Schritte aus, um Inhalte zu kopieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Navigieren Sie auf dem Bildschirm **Umgebungen** zur Seite **Inhaltssets** .

1. Wählen Sie ein Content-Set aus der Konsole aus, und wählen Sie im Menü mit den Auslassungspunkten **Inhalt kopieren**.

   ![Inhaltskopie](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Eine Umgebung ist unter Umständen nicht auswählbar, wenn:
   >
   >* die Benutzenden nicht über die entsprechenden Berechtigungen verfügen.
   >* in der Umgebung eine laufende Pipeline oder ein Vorgang zum Kopieren von Inhalten in Bearbeitung ist.

1. Geben Sie im Dialogfeld **Inhalt kopieren** die Quell- und Zielumgebungen für die Aktion zum Kopieren von Inhalten an.
   * Die Regionen der Zielumgebung müssen mit den Regionen der Quellumgebung oder einer Untergruppe davon übereinstimmen.

1. Sie können die Ausschlusspfade in der Zielumgebung löschen oder beibehalten. Aktivieren Sie das Kontrollkästchen `Do not delete exclude paths from destination` , um den im Inhaltsset angegebenen Wert `exclude paths` beizubehalten. Wenn das Kontrollkästchen deaktiviert ist, werden Ausschlusspfade in der Zielumgebung gelöscht.

1. Sie können den Versionsverlauf der Pfade kopieren, die von der Quell- in die Zielumgebung kopiert werden. Aktivieren Sie das Kontrollkästchen `Copy Versions` , wenn Sie alle Versionsverläufe kopieren möchten.

   ![Kopieren von Inhalten](/help/assets/copying-content.png)

1. Klicken Sie auf **Kopieren**.

Der Kopiervorgang wird gestartet. Der Status des Kopiervorgangs wird für das ausgewählte Content-Set in der Konsole angezeigt.

## Aktivität &quot;Inhaltskopie&quot; {#copy-activity}

Sie können den Status der Kopierprozesse auf der Seite **Aktivität „Inhalt kopieren“** überwachen.

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie dann das entsprechende Unternehmen und Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Navigieren Sie auf dem Bildschirm **Umgebungen** zur Seite **Aktivität &quot;Inhalt kopieren&quot;** .

![Aktivität „Inhalt kopieren“](/help/assets/copy-content-activity.png)

### Status der Inhaltskopie {#statuses}

Sobald das Kopieren von Inhalten beginnt, kann der Prozess einen der folgenden Status haben.

| Status | Beschreibung |
|---|---|
| In Bearbeitung | Die Inhaltskopie wird gerade durchgeführt |
| Fehlgeschlagen | Die Inhaltskopie ist fehlgeschlagen |
| Abgeschlossen | Die Inhaltskopie wurde erfolgreich abgeschlossen |

## Einschränkungen {#limitations}

Für das Werkzeug zum Kopieren von Inhalten gelten die folgenden Einschränkungen.

* Eine Inhaltskopie kann nicht von einer niedrigeren Umgebung in eine höhere Umgebung durchgeführt werden.
* Die Inhaltskopie kann nur innerhalb derselben Ebene durchgeführt werden. Das heißt, author-author oder publish-publish.
* Eine programm- und regionenübergreifende Inhaltskopie ist nicht möglich.
* Die auf dem Cloud-Datenspeicher basierende Topologie kann nur dann kopiert werden, wenn sich die Quell- und Zielumgebung auf demselben Cloud-Anbieter und in derselben Region befinden.
* Die Ausführung gleichzeitiger Vorgänge zum Kopieren von Inhalten in derselben Umgebung ist nicht möglich.
* Eine Inhaltskopie kann nicht ausgeführt werden, wenn ein aktiver Vorgang in der Ziel- oder Quellumgebung ausgeführt wird, z. B. einer CI/CD-Pipeline.
* Pro Content-Set können bis zu fünfzig Pfade angegeben werden. Ausgeschlossene Pfade sind nicht beschränkt.
* Das Werkzeug zum Kopieren von Inhalten sollte nicht als Klon- oder Spiegelwerkzeug verwendet werden, da es keine verschobenen oder gelöschten Inhalte auf der Quelle verfolgen kann.
* Eine Inhaltskopie kann nicht pausiert oder abgebrochen werden, nachdem sie initiiert wurde.
* Das Inhaltskopie-Werkzeug kopiert Assets zusammen mit Metadaten von Dynamic Media aus der höheren Umgebung in die ausgewählte untere Umgebung.
   * Kopierte Assets müssen dann mithilfe des [Workflows für DAM-Prozess-Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html?lang=de) in der unteren Umgebung neu verarbeitet werden, um die entsprechende Konfiguration für Dynamic Media zu verwenden.
* Der Vorgang zum Kopieren von Inhalten wird erheblich schneller ausgeführt, wenn der Versionsverlauf nicht kopiert wird.
* [Dynamic Media-Konfigurationen mit Asset-Größen größer als 2 GB aktiviert](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) werden nicht unterstützt.
* Wenn der Versionsverlauf nicht kopiert wird, ist der Inhaltskopierprozess wesentlich schneller.
* Die Regionen der Zielumgebung müssen mit den Regionen der Quellumgebung oder einer Untergruppe davon übereinstimmen.

## Bekannte Probleme {#known-issues}

{{content-copy-known-issues}}
