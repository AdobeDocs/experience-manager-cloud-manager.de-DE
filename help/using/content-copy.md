---
title: Das Inhaltskopie-Werkzeug
description: Mit dem Inhaltskopie-Werkzeug von Cloud Manager können Benutzende veränderbare Inhalte bei Bedarf aus ihren AEM-Produktionsumgebungen zu Testzwecken in niedrigere Umgebungen kopieren.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: 7ef29a244688de82537da0b879fbf397900427c0
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 99%

---

# Das Inhaltskopie-Werkzeug {#content-copy}

Mit dem Inhaltskopie-Werkzeug von Cloud Manager können Benutzende veränderbare Inhalte bei Bedarf aus ihren AEM-Produktionsumgebungen zu Testzwecken in niedrigere Umgebungen kopieren.

## Einführung {#introduction}

Aktuelle, echte Daten sind für Tests, Validierung und Benutzerakzeptanz nützlich. Mit dem Inhaltskopie-Werkzeug von Inhalten können Sie Inhalte für solche Tests aus Ihrer AEM-Produktionsumgebung in eine Staging- oder Entwicklungsumgebung kopieren.

Der zu kopierende Inhalt wird durch ein Content-Set definiert. Ein Content-Set besteht aus einer Liste von JCR-Pfaden, die den veränderlichen Inhalt enthalten, der aus einer Quellumgebung in eine Zielumgebung innerhalb desselben Cloud Manager-Programms kopiert werden soll. Die folgenden Pfade sind in einem Content-Set zulässig.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Beim Kopieren von Inhalten ist die Quellumgebung die Datenquelle.

* Wenn der Inhalt in der Zielumgebung geändert wurde, wird er durch den Inhalt in der Quelle überschrieben, wenn die Pfade übereinstimmen.
* Wenn die Pfade unterschiedlich sind, wird der Inhalt der Quelle mit dem Inhalt des Ziels zusammengeführt.

   >[!NOTE]
   >
   >Es werden nur Topologien auf der Grundlage von Dateidatenspeichern unterstützt.

## Berechtigungen {#permissions}

Um das Werkzeug zum Kopieren von Inhalten verwenden zu können, muss den Benutzenden die Rolle **Bereitstellungs-Manager** in der Quell- und Zielumgebung zugewiesen sein.

## Erstellen eines Content-Sets {#create-content-set}

Bevor Inhalt kopiert werden kann, muss ein Content-Set definiert werden. Nach der Definition können Content-Sets zum Kopieren von Inhalten wiederverwendet werden. Gehen Sie wie folgt vor, um ein Content-Set zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie vom Bildschirm **Umgebungen** zur Seite **Content-Sets**.

1. Tippen oder klicken Sie rechts oben auf dem Bildschirm auf **Content-Set hinzufügen**.

   ![Content-Sets](/help/assets/content-sets.png)

1. Geben Sie auf der Registerkarte **Details** des Assistenten einen Namen und eine Beschreibung für das Content-Set ein und tippen oder klicken Sie auf **Weiter**.

   ![Content-Set-Details](/help/assets/add-content-set-details.png)

1. Auf der Registerkarte **Inhaltspfade** des Assistenten geben Sie die Pfade der veränderbaren Inhalte an, die in das Content-Set aufgenommen werden sollen.

   1. Geben Sie den Pfad in das Feld **Einschlusspfad hinzufügen** ein.
   1. Tippen oder klicken Sie auf die Schaltfläche **Pfad hinzufügen**, um den Pfad zum Content-Set hinzuzufügen.
   1. Tippen oder klicken Sie bei Bedarf erneut auf die Schaltfläche **Pfad hinzufügen**.

   ![Hinzufügen von Pfaden zu Content-Sets](/help/assets/add-content-set-paths.png)

1. Wenn Sie Ihr Content-Set verfeinern oder einschränken möchten, können Sie Unterpfade ausschließen.

   1. Tippen oder klicken Sie in der Liste der enthaltenen Pfade auf das Symbol **Ausschluss-Unterpfade hinzufügen** neben dem Pfad, den Sie einschränken möchten.
   1. Geben Sie den Unterpfad ein, der unterhalb des ausgewählten Pfads ausgeschlossen werden soll.
   1. Tippen oder klicken Sie auf **Pfad ausschließen**.
   1. Tippen oder klicken Sie erneut auf **Ausschluss-Unterpfade hinzufügen**, um bei Bedarf weitere Pfade zum Ausschluss hinzuzufügen.

   ![Ausschließen von Pfaden](/help/assets/add-content-set-paths-excluded.png)

1. Sie können die angegebenen Pfade bei Bedarf ändern.

   1. Tippen oder klicken Sie auf das X neben den ausgeschlossenen Unterpfaden, um sie zu löschen.
   1. Tippen oder klicken Sie auf die Ellipsen-Schaltfläche neben den Pfaden, um die Optionen **Bearbeiten** und **Löschen** anzuzeigen.

   ![Bearbeiten der Pfadliste](/help/assets/add-content-set-excluded-paths.png)

1. Tippen oder klicken Sie auf **Erstellen**, um das Content-Set zu erstellen.

Das Content-Set kann jetzt zum Kopieren von Inhalten zwischen Umgebungen verwendet werden.

>[!NOTE]
>
>Sie können bis zu 50 Pfade in einem Inhaltsset hinzufügen.
>Für ausgeschlossene Pfade gibt es keine Beschränkung.

## Bearbeiten eines Content-Sets {#edit-content-set}

Hierbei führen Sie ähnliche Schritte wie beim Erstellen eines Content-Sets aus. Anstatt auf **Content-Set hinzufügen** zu tippen oder zu klicken, wählen Sie ein vorhandenes Set aus der Konsole aus und wählen Sie im Menü mit den Auslassungspunkten die Option **Bearbeiten**.

![Bearbeiten des Content-Sets](/help/assets/edit-content-set.png)

Beim Bearbeiten des Content-Sets müssen Sie möglicherweise die konfigurierten Pfade erweitern, um die ausgeschlossenen Unterpfade anzuzeigen.

## Kopieren von Inhalten {#copy-content}

Nachdem ein Content-Set erstellt wurde, können Sie es zum Kopieren von Inhalten verwenden. Führen Sie die folgenden Schritte aus, um Inhalte zu kopieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie vom Bildschirm **Umgebungen** zur Seite **Content-Sets**.

1. Wählen Sie ein Content-Set aus der Konsole aus, und wählen Sie im Menü mit den Auslassungspunkten **Inhalt kopieren**.

   ![Inhaltskopie](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Eine Umgebung ist unter Umständen nicht auswählbar, wenn:
   >
   >* die Benutzenden nicht über die entsprechenden Berechtigungen verfügen.
   >* in der Umgebung eine laufende Pipeline oder ein Vorgang zum Kopieren von Inhalten in Bearbeitung ist.


1. Geben Se im Dialog **Inhalt kopieren** die Quelle und das Ziel für die Inhaltskopie-Aktion an.

1. Sie können die Ausschlusspfade in der Zielumgebung löschen oder beibehalten. Aktivieren Sie das Kontrollkästchen `Do not delete exclude paths from destination`, wenn Sie die im Content-Set angegebenen Ausschlusspfade beibehalten möchten. Wenn das Kontrollkästchen deaktiviert bleibt, werden Ausschlusspfade in der Zielumgebung gelöscht.

   ![Kopieren von Inhalten](/help/assets/copying-content.png)

1. Tippen oder klicken Sie auf **Kopieren**.

Der Kopiervorgang wird gestartet. Der Status des Kopiervorgangs wird für das ausgewählte Content-Set in der Konsole angezeigt.

## Aktivität „Inhalt kopieren“ {#copy-activity}

Sie können den Status der Kopierprozesse auf der Seite **Aktivität „Inhalt kopieren“** überwachen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie im Bildschirm **Umgebungen** zur Seite **Aktivität „Inhalt kopieren“**.

![Aktivität „Inhalt kopieren“](/help/assets/copy-content-activity.png)

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
* Das Kopieren von Inhalten kann nur innerhalb derselben Ebene durchgeführt werden (d. h. Autor-Autor oder Veröffentlichung-Veröffentlichung).
* Eine programmübergreifende Inhaltskopie ist nicht möglich.
* Die Ausführung gleichzeitiger Inhaltskopievorgänge in derselben Umgebung ist nicht möglich.
* Eine Inhaltskopie kann nicht durchgeführt werden, wenn ein aktiver Vorgang in der Ziel- oder Quellumgebung ausgeführt wird, z. B. eine CI/CD-Pipeline.
* Pro Content-Set können bis zu fünfzig Pfade angegeben werden. Ausgeschlossene Pfade sind nicht beschränkt.
* Das Werkzeug zum Kopieren von Inhalten sollte nicht als Klon- oder Spiegelwerkzeug verwendet werden, da es keine verschobenen oder gelöschten Inhalte auf der Quelle verfolgen kann.
* Das Werkzeug zum Kopieren von Inhalten verfügt über keine Versionierungsfunktion und kann geänderten oder neu erstellten Inhalt in der Quellumgebung in einem Content-Set seit dem letzten Inhaltskopievorgang nicht automatisch erkennen.
   * Um die Zielumgebung nur mit Inhaltsänderungen zu aktualisieren, die seit dem letzten Inhaltskopievorgang vorgenommen wurden, müssen Sie ein Content-Set erstellen. Geben Sie in diesem Set sind die Pfade in der Quellinstanz an, an denen seit dem letzten Inhaltskopievorgang Änderungen vorgenommen wurden.
* Versionsinformationen sind in einer Inhaltskopie nicht enthalten.
