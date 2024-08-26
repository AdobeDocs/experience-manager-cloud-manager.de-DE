---
title: Das Inhaltskopie-Tool
description: Mit dem Inhaltskopie-Tool von Cloud Manager können Benutzende veränderliche Inhalte bei Bedarf aus AMS-gehosteten AEM 6.x-Produktionsumgebungen zu Testzwecken in niedrigere Umgebungen kopieren.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 90%

---


# Das Inhaltskopie-Tool {#content-copy}

Mit dem Inhaltskopie-Tool von Cloud Manager können Benutzende veränderliche Inhalte bei Bedarf aus AMS-gehosteten AEM 6.x-Produktionsumgebungen zu Testzwecken in niedrigere Umgebungen kopieren.

## Einführung {#introduction}

Aktuelle, echte Daten sind für Tests, Validierung und Benutzerakzeptanz nützlich. Mit dem Inhaltskopie-Tool können Sie Inhalte aus Ihrer AMS-gehosteten AEM 6.x-Produktionsumgebung in Staging- oder Entwicklungsumgebungen kopieren. Dieser Workflow unterstützt verschiedene Testszenarien.

Ein Content-Set definiert die zu kopierenden Inhalte. Ein Content-Set enthält eine Liste von JCR-Pfaden mit dem zu kopierenden veränderlichen Inhalten. Die Inhalte werden von einer Quellumgebung in eine Zielumgebung verschoben. Alle dies geschieht innerhalb desselben Cloud Manager-Programms.

Die folgenden Pfade sind in einem Content-Set zulässig:

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
/var/commerce/**
```

Beim Kopieren von Inhalten ist die Quellumgebung die Datenquelle.

* Wenn Sie Inhalte in der Zielumgebung bearbeiten, werden diese vom Quellinhalt überschrieben, sofern die Pfade übereinstimmen.
* Wenn die Pfade unterschiedlich sind, wird der Inhalt der Quelle mit dem Inhalt des Ziels zusammengeführt.

## Berechtigungen {#permissions}

Um das Inhaltskopie-Tool verwenden zu können, muss den Benutzenden in der Quell- und Zielumgebung die Rolle **Bereitstellungs-Manager** zugewiesen sein.

## Erstellen eines Content-Sets {#create-content-set}

Bevor Inhalt kopiert werden kann, muss ein Content-Set definiert werden. Nach der Definition können Content-Sets zum Kopieren von Inhalten wiederverwendet werden. Gehen Sie wie folgt vor, um ein Content-Set zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Navigieren Sie auf dem Bildschirm **Umgebungen** zur Seite **Content-Sets**.

1. Klicken Sie oben rechts im Bildschirm auf **Content-Set hinzufügen**.

   ![Content-Sets](/help/assets/content-sets.png)

1. Geben Sie auf der Registerkarte **Details** des Assistenten einen Namen und eine Beschreibung für das Content-Set ein und klicken Sie auf **Weiter**.

   ![Content-Set-Details](/help/assets/add-content-set-details.png)

1. Auf der Registerkarte **Inhaltspfade** des Assistenten geben Sie die Pfade der veränderbaren Inhalte an, die in das Content-Set aufgenommen werden sollen.

   1. Geben Sie den Pfad in das Feld **Einschlusspfad hinzufügen** ein.
   1. Klicken Sie auf **Pfad hinzufügen**, um den Pfad zum Inhaltssatz hinzuzufügen.
   1. Klicken Sie bei Bedarf erneut auf **Pfad hinzufügen**.

   ![Hinzufügen von Pfaden zu Content-Sets](/help/assets/add-content-set-paths.png)

1. Wenn Sie Ihr Content-Set verfeinern oder einschränken möchten, können Sie Unterpfade ausschließen.

   1. Klicken Sie in der Liste der eingeschlossenen Pfade auf das Symbol **Ausschluss-Unterpfade hinzufügen** neben dem Pfad, der eingeschränkt werden soll.
   1. Geben Sie den Unterpfad ein, der von dem ausgewählten Pfad ausgeschlossen werden soll.
   1. Klicken Sie auf **Pfad ausschließen**.
   1. Klicken Sie erneut auf **Ausschluss-Unterpfade hinzufügen**, um bei Bedarf weitere auszuschließende Pfade hinzuzufügen.

   ![Ausschließen von Pfaden](/help/assets/add-content-set-paths-excluded.png)

1. Sie können die angegebenen Pfade bei Bedarf ändern.

   1. Klicken Sie auf das `X` neben den ausgeschlossenen Unterpfaden, um diese zu löschen.
   1. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben den Pfaden, um die Optionen **Bearbeiten** und **Löschen** anzuzeigen.

   ![Bearbeiten der Pfadliste](/help/assets/add-content-set-excluded-paths.png)

1. Klicken Sie auf **Erstellen**, um das Content-Set zu erstellen.

Das Content-Set kann jetzt zum Kopieren von Inhalten zwischen Umgebungen verwendet werden.

>[!NOTE]
>
>Sie können einem Content-Set bis zu 50 Pfade hinzufügen.
>Für ausgeschlossene Pfade gibt es keine Beschränkung.

## Bearbeiten eines Content-Sets {#edit-content-set}

Hierbei führen Sie ähnliche Schritte wie beim Erstellen eines Content-Sets aus. Anstatt auf **Content-Set hinzufügen** zu klicken, wählen Sie ein vorhandenes Set in der Konsole und dann die Option **Bearbeiten** aus dem Menü mit den Auslassungspunkten aus.

![Bearbeiten des Content-Sets](/help/assets/edit-content-set.png)

Beim Bearbeiten des Content-Sets müssen Sie möglicherweise die konfigurierten Pfade erweitern, um die ausgeschlossenen Unterpfade anzuzeigen.

## Inhalt kopieren {#copy-content}

Nachdem ein Content-Set erstellt wurde, können Sie es zum Kopieren von Inhalten verwenden. Führen Sie die folgenden Schritte aus, um Inhalte zu kopieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Navigieren Sie auf dem Bildschirm **Umgebungen** zur Seite **Content-Sets**.

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

1. Sie können die Ausschlusspfade in der Zielumgebung löschen oder beibehalten. Aktivieren Sie das Kontrollkästchen `Do not delete exclude paths from destination`, um die im Content-Set angegebenen `exclude paths` beizubehalten. Wenn das Kontrollkästchen deaktiviert bleibt, werden die Ausschlusspfade in der Zielumgebung gelöscht.

1. Sie können den Kopieversionsverlauf der Pfade aus der Quell- in die Zielumgebung kopieren. Aktivieren Sie das Kontrollkästchen `Copy Versions`, wenn alle Versionsverläufe kopiert werden sollen.

   ![Kopieren von Inhalten](/help/assets/copying-content.png)

1. Klicken Sie auf **Kopieren**.

Der Kopiervorgang wird gestartet. Der Status des Kopiervorgangs wird für das ausgewählte Content-Set in der Konsole angezeigt.

## Inhaltskopie-Aktivität {#copy-activity}

Sie können den Status der Kopierprozesse auf der Seite **Aktivität zum Kopieren von Inhalten** überwachen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie auf der Seite **Übersicht** zum Bildschirm **Umgebungen**.

1. Navigieren Sie auf dem Bildschirm **Umgebungen** zur Seite **Aktivität zum Kopieren von Inhalten**.

![Aktivität zum Kopieren von Inhalten](/help/assets/copy-content-activity.png)

### Inhaltskopie-Status {#statuses}

Sobald das Kopieren von Inhalten beginnt, kann der Prozess einen der folgenden Status haben.

| Status | Beschreibung |
|---|---|
| In Bearbeitung | Die Inhaltskopie wird gerade durchgeführt |
| Fehlgeschlagen | Die Inhaltskopie ist fehlgeschlagen |
| Abgeschlossen | Die Inhaltskopie wurde erfolgreich abgeschlossen |

## Einschränkungen {#limitations}

Für das Werkzeug zum Kopieren von Inhalten gelten die folgenden Einschränkungen.

* Eine Inhaltskopie kann nicht von einer niedrigeren Umgebung in eine höhere Umgebung durchgeführt werden.
* Das Kopieren von Inhalten kann nur innerhalb derselben Ebene durchgeführt werden. (d. h. Autor-Autor oder Veröffentlichung-Veröffentlichung).
* Eine programm- und regionenübergreifende Inhaltskopie ist nicht möglich.
* Eine Inhaltskopie für eine auf Cloud-Datenspeicher basierende Topologie kann nur durchgeführt werden, wenn sich die Quell- und Zielumgebung bei demselben Cloud-Anbieter und in derselben Region befinden.
* Die Ausführung gleichzeitiger Inhaltskopievorgänge in derselben Umgebung ist nicht möglich.
* Eine Inhaltskopie kann nicht durchgeführt werden, wenn ein aktiver Vorgang in der Ziel- oder Quellumgebung ausgeführt wird, z. B. eine CI/CD-Pipeline.
* Pro Content-Set können bis zu fünfzig Pfade angegeben werden. Für ausgeschlossene Pfade gibt es keine Beschränkung.
* Das Inhaltskopie-Tool sollte nicht als Klon- oder Spiegelwerkzeug verwendet werden, da es keine verschobenen oder gelöschten Inhalte auf der Quelle verfolgen kann.
* Eine Inhaltskopie kann nicht angehalten oder abgebrochen werden, nachdem sie initiiert wurde.
* Das Werkzeug zum Kopieren von Inhalten kopiert Assets und Dynamic Media-Metadaten aus der höheren Umgebung in die ausgewählte untere Umgebung. Kopierte Assets müssen dann mithilfe des [Workflows zur DAM-Verarbeitung von Assets](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/using/assets-workflow) in der niedrigeren Umgebung neu verarbeitet werden, um die entsprechende Dynamic Media-Konfiguration zu verwenden.
* Der Content Copy-Prozess ist erheblich schneller, wenn der Versionsverlauf nicht kopiert wird.
* [Dynamic Media-Konfigurationen mit Asset-Größen größer als 2 GB aktiviert](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) werden nicht unterstützt.
* Wenn der Versionsverlauf nicht kopiert wird, ist der Prozess zur Erstellung einer Inhaltskopie wesentlich schneller.
* Die Regionen der Zielumgebung müssen mit den Regionen der Quellumgebung oder einer Untergruppe davon übereinstimmen.

## Bekannte Probleme {#known-issues}

{{content-copy-known-issues}}
