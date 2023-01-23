---
title: Das Werkzeug "Inhaltskopie"
description: Mit dem Content Copy-Tool für Cloud Manager können Benutzer veränderliche Inhalte bei Bedarf aus ihren AEM Produktionsumgebungen in niedrigere Umgebungen kopieren, um sie zu Testzwecken zu verwenden.
source-git-commit: 360cbf7e3a21e530a4e43f13f6d414dae4afa104
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 7%

---


# Das Werkzeug &quot;Inhaltskopie&quot; {#content-copy}

Mit dem Content Copy-Tool für Cloud Manager können Benutzer veränderliche Inhalte bei Bedarf aus ihren AEM Produktionsumgebungen in niedrigere Umgebungen kopieren, um sie zu Testzwecken zu verwenden.

## Einführung {#introduction}

Aktuelle, echte Daten sind für Tests, Validierung und Benutzerakzeptanz nützlich. Mit dem Werkzeug zum Kopieren von Inhalten können Sie Inhalte aus Ihrer Produktions-AEM in eine Staging- oder Entwicklungsumgebung für solche Tests kopieren.

Der zu kopierende Inhalt wird durch einen Inhaltssatz definiert. Ein Inhaltssatz besteht aus einer Liste von JCR-Pfaden, die den veränderlichen Inhalt enthalten, der aus einer Quellumgebung in eine Zielumgebung innerhalb desselben Cloud Manager-Programms kopiert werden soll. Die folgenden Pfade sind in einem Inhaltssatz zulässig.

```text
/content/**
/conf/**
/etc/**
/var/workflow/models/**
```

Beim Kopieren von Inhalten ist die Quellumgebung die Quelle der Wahrheit.

* Wenn Inhalt in der Zielumgebung geändert wurde, wird er durch Inhalte in der Quelle überschrieben, wenn die Pfade identisch sind.
* Unterscheiden sich die Pfade, werden Inhalte aus der Quelle mit dem Inhalt im Ziel zusammengeführt.

## Berechtigungen {#permissions}

Um das Werkzeug zum Kopieren von Inhalten verwenden zu können, muss der Benutzer dem **Bereitstellungsmanager** Rolle in der Quell- und Zielumgebung.

## Erstellen eines Inhaltssatzes {#create-content-set}

Bevor ein Inhalt kopiert werden kann, muss ein Inhaltssatz definiert werden. Nach der Definition können Inhaltssätze zum Kopieren von Inhalten wiederverwendet werden. Führen Sie die folgenden Schritte aus, um einen Inhaltssatz zu erstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie zum **Content Sets** Seite aus **Umgebungen** angezeigt.

1. Tippen oder klicken Sie auf **Inhaltsset hinzufügen** rechts oben auf dem Bildschirm.

   ![Content Sets](/help/assets/content-sets.png)

1. Im **Details** auf der Registerkarte des Assistenten einen Namen und eine Beschreibung für den Inhaltssatz angeben und auf **Weiter**.

   ![Inhaltsset-Details](/help/assets/add-content-set-details.png)

1. Im **Inhaltspfade** im Assistenten die Pfade des veränderlichen Inhalts angeben, der in den Inhaltsset aufgenommen werden soll.

   1. Geben Sie den Pfad im **Einschlusspfad hinzufügen** -Feld.
   1. Tippen oder klicken Sie auf **Pfad hinzufügen** -Schaltfläche, um den Pfad zum Inhaltsset hinzuzufügen.
   1. Tippen oder klicken Sie auf **Pfad hinzufügen** bei Bedarf erneut klicken.

   ![Hinzufügen von Pfaden zu Inhaltssätzen](/help/assets/add-content-set-paths.png)

1. Wenn Sie den Inhaltssatz verfeinern oder beschränken müssen, können Unterpfade ausgeschlossen werden.

   1. Tippen oder klicken Sie in der Liste der enthaltenen Pfade auf die **Hinzufügen von Ausschlussunterpfaden** neben dem Pfad, den Sie beschränken müssen.
   1. Geben Sie den Unterpfad ein, der unter dem ausgewählten Pfad ausgeschlossen werden soll.
   1. Tippen oder klicken Sie auf **Ausschlusspfad**.
   1. Tippen oder klicken Sie auf **Hinzufügen von Ausschlussunterpfaden** erneut hinzufügen, um bei Bedarf zusätzliche Pfade zum Ausschließen hinzuzufügen.

   ![Ausschließen von Pfaden](/help/assets/add-content-set-paths-excluded.png)

1. Sie können die angegebenen Pfade bei Bedarf ändern.

   1. Tippen oder klicken Sie auf das X neben den ausgeschlossenen Unterpfaden, um sie zu löschen.
   1. Tippen oder klicken Sie auf die Schaltfläche mit Auslassungspunkten neben Pfaden, um sie anzuzeigen **Bearbeiten** und **Löschen** Optionen.

   ![Pfadliste bearbeiten](/help/assets/add-content-set-excluded-paths.png)

1. Tippen oder klicken Sie auf **Erstellen** , um den Inhaltssatz zu erstellen.

Der Inhaltssatz kann jetzt zum Kopieren von Inhalten zwischen Umgebungen verwendet werden.

## Bearbeiten eines Inhaltssets {#edit-content-set}

Führen Sie ähnliche Schritte wie beim Erstellen eines Inhaltsschritts aus. Anstatt auf **Inhaltsset hinzufügen**, wählen Sie einen vorhandenen Satz aus der Konsole aus und wählen Sie **Bearbeiten** aus dem Menü mit den Auslassungspunkten.

![Inhaltsset bearbeiten](/help/assets/edit-content-set.png)

Beim Bearbeiten des Inhaltssatzes müssen Sie möglicherweise die konfigurierten Pfade erweitern, um die ausgeschlossenen Unterpfade anzuzeigen.

## Kopieren von Inhalten {#copy-content}

Nachdem ein Inhaltssatz erstellt wurde, können Sie ihn zum Kopieren von Inhalten verwenden. Führen Sie die folgenden Schritte aus, um Inhalte zu kopieren.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie zum **Content Sets** Seite aus **Umgebungen** angezeigt.

1. Wählen Sie einen Inhaltssatz aus der Konsole aus und wählen Sie **Inhalt kopieren** aus dem Menü mit den Auslassungspunkten.

   ![Inhaltskopie](/help/assets/copy-content.png)

   >[!NOTE]
   >
   >Eine Umgebung kann nicht auswählbar sein, wenn:
   >
   >* Der Benutzer verfügt nicht über die entsprechenden Berechtigungen.
   >* Die Umgebung verfügt über eine laufende Pipeline oder einen Vorgang zum Kopieren von Inhalten.


1. Im **Inhalt kopieren** Geben Sie die Quelle und das Ziel für die Aktion zum Kopieren des Inhalts an.

   ![Kopieren von Inhalten](/help/assets/copying-content.png)

1. Tippen oder klicken Sie auf **Kopieren**.

Der Kopiervorgang wird gestartet. Der Status des Kopiervorgangs wird in der Konsole für den ausgewählten Inhaltssatz angezeigt.

## Content Copy-Aktivität {#copy-activity}

Sie können den Status Ihrer Kopierprozesse im **Aktivität &quot;Inhalt kopieren&quot;** Seite.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zum Bildschirm **Umgebungen**.

1. Navigieren Sie zum **Aktivität &quot;Inhalt kopieren&quot;** Seite aus **Umgebungen** angezeigt.

![Content Copy-Aktivität](/help/assets/copy-content-activity.png)

### Inhaltskopie-Status {#statuses}

Sobald Sie mit dem Kopieren von Inhalten beginnen, kann der Prozess einen der folgenden Status haben.

| Status | Beschreibung |
|---|---|
| In Bearbeitung | Vorgang &quot;Content Copy&quot;läuft |
| Fehlgeschlagen | Vorgang &quot;Content Copy&quot;fehlgeschlagen |
| Abgeschlossen | Vorgang &quot;Content Copy&quot;erfolgreich abgeschlossen |

## Beschränkungen {#limitations}

Für das Werkzeug zum Kopieren von Inhalten gelten die folgenden Einschränkungen.

* Eine Inhaltskopie kann nicht von einer niedrigeren Umgebung in eine höhere Umgebung durchgeführt werden.
* Das Kopieren von Inhalten kann nur innerhalb derselben Ebene durchgeführt werden (d. h. author-author oder publish-publish).
* Eine programmübergreifende Inhaltskopie ist nicht möglich.
* Die Ausführung gleichzeitiger Vorgänge zum Kopieren von Inhalten in derselben Umgebung ist nicht möglich.
* Eine Inhaltskopie kann nicht durchgeführt werden, wenn ein aktiver Vorgang auf der Ziel- oder Quellumgebung ausgeführt wird, z. B. einer CI/CD-Pipeline.
* Pro Inhaltsset können bis zu zehn Pfade angegeben werden. Ausgeschlossene Pfade sind nicht beschränkt.
* Das Werkzeug zum Kopieren von Inhalten sollte nicht als Klonen- oder Spiegelwerkzeug verwendet werden, da es keine verschobenen oder gelöschten Inhalte auf der Quelle verfolgen kann.
* Das Werkzeug zum Kopieren von Inhalten verfügt über keine Versionierungsfunktion und kann geänderten oder neu erstellten Inhalt in der Quellumgebung in einem Inhaltsset seit dem letzten Vorgang zum Kopieren von Inhalten nicht automatisch erkennen.
   * Wenn Sie Ihre Zielumgebung nur mit Inhaltsänderungen aktualisieren möchten, die seit dem letzten Vorgang der Inhaltskopie vorgenommen wurden, müssen Sie einen Inhaltssatz erstellen. Geben Sie in diesem Satz die Pfade in der Quellinstanz an, an denen Änderungen seit dem letzten Vorgang der Inhaltskopie vorgenommen wurden.
* Versionsinformationen sind nicht in einer Inhaltskopie enthalten.
