---
title: Inhaltskopie für Umgebungskonsistenz
description: Mit der Inhaltskopie in Cloud Manager können Benutzende veränderliche Inhalte bei Bedarf aus Produktionsumgebungen von Adobe Experience Manager 6.x, die von Adobe Managed Services gehostet werden, zu Testzwecken in niedrigere Umgebungen kopieren.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: e3a656605ac59ca1f95985426932fddf2b53b7c9
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 100%

---


# Inhaltskopie für Umgebungskonsistenz {#content-copy}

Mit der Inhaltskopie in Cloud Manager können Benutzende veränderliche Inhalte bei Bedarf aus Produktionsumgebungen von Adobe Experience Manager 6.x, die von Adobe Managed Services gehostet werden, zu Testzwecken in niedrigere Umgebungen kopieren.

## Über die Inhaltskopie {#introduction}

Aktuelle, echte Daten sind für Tests, Validierung und Benutzerakzeptanz nützlich. Mit der Inhaltskopie können Sie Inhalte aus Ihrer AMS-gehosteten AEM 6.x-Produktionsumgebung in Staging- oder Entwicklungsumgebungen kopieren. Dieser Workflow unterstützt verschiedene Testszenarien.

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

Wenn Sie Inhalte in der Zielumgebung bearbeiten, werden diese vom Quellinhalt überschrieben, sofern die Pfade übereinstimmen.

Wenn die Pfade unterschiedlich sind, wird der Inhalt der Quelle mit dem Inhalt des Ziels zusammengeführt.

### Berechtigungen {#permissions}

Um die Funktion der Inhaltskopie verwenden zu können, muss den Benutzenden in der Quell- und Zielumgebung die Rolle **Bereitstellungs-Manager** zugewiesen sein.

## Erstellen eines Content-Sets {#create-content-set}

Bevor Inhalt kopiert werden kann, muss ein Content-Set definiert werden. Nach der Definition können Content-Sets zum Kopieren von Inhalten wiederverwendet werden. Gehen Sie wie folgt vor, um ein Content-Set zu erstellen.

**So erstellen Sie ein Content-Set:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie oben links auf der Seite auf das Symbol ![Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü zu öffnen.

1. Klicken Sie im linken Seitenmenü unter **Services** auf das Symbol ![Kontrollkästchen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Content-Sets**.

1. Klicken Sie oben rechts auf der Seite auf **Content-Set hinzufügen**.

   ![Content-Sets](/help/assets/content-sets.png)

1. Geben Sie im Dialogfeld **`Add Content Set`** auf der Registerkarte **Details** in den Feldern **Name** und **Beschreibung** einen Namen und eine optionale Beschreibung für das Content-Set ein und klicken Sie dann auf **Weiter**.

   ![Details des Content-Sets](/help/assets/add-content-set-details.png)

1. Geben Sie auf der Registerkarte **Inhaltspfade** im Textfeld **Pfad** einen Pfad zum Inhalt an, der geändert werden kann und in das Content-Set einbezogen werden soll.

   Nur Pfade, die mit `/content`, `/conf`, `/etc`, `/var/workflow/models` oder `/var/commerce` beginnen, können aufgenommen werden.

1. Klicken Sie auf das Symbol **![Ordner hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) Pfad hinzufügen**, um den Pfad zum Content-Set hinzuzufügen (oder darin einzubeziehen).

1. (Optional) Bei Bedarf können Sie weitere Pfade (bis zu 50) hinzufügen, indem Sie die vorherigen beiden Schritte wiederholen. Fahren Sie ansonsten mit dem nächsten Schritt fort.

   ![Hinzufügen von Pfaden zu einem Content-Set](/help/assets/add-content-set-paths.png)

1. (Optional) Um Ihr Content-Set einzugrenzen, können Sie optional Unterpfade in einem einbezogenen Inhaltspfad angeben, die ausgeschlossen werden sollen.

   1. Klicken Sie rechts neben einem einbezogenen Inhaltspfad, den Sie ausschließen möchten, auf das Symbol ![Ordner löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. Geben Sie im Textfeld einen relativen Pfad zum im Dialogfeld angezeigten Stammpfad ein.
   1. Klicken Sie auf das Symbol ![Ordner löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Pfad ausschließen**.
   1. Wiederholen Sie gegebenenfalls die Schritte i. bis iii. oben, um weitere Pfade auszuschließen. Es gibt keine Beschränkung. Fahren Sie ansonsten mit dem nächsten Schritt fort.

   ![Ausschließen von Pfaden](/help/assets/add-content-set-paths-excluded.png)

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   1. Klicken Sie rechts neben einem ausgeschlossenen Unterpfad auf ![Kreuz-Symbol](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg), um ihn zu löschen.
   1. Klicken Sie auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/ui_18/More.svg) rechts neben einem einbezogenen Inhaltspfad und dann auf **Bearbeiten** bzw. **Löschen**.

   ![Bearbeiten der Pfadliste](/help/assets/add-content-set-excluded-paths.png)

1. Klicken Sie auf **Erstellen**. Jetzt können Sie das Content-Set zum Kopieren von Inhalten zwischen Umgebungen verwenden.

## Bearbeiten oder Löschen von Content-Sets {#edit-content-set}

Beim Bearbeiten eines Content-Sets müssen Sie möglicherweise die konfigurierten Pfade erweitern, um die ausgeschlossenen Unterpfade anzuzeigen.

**So bearbeiten oder löschen Sie ein Content-Set:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie oben links auf der Seite auf das Symbol ![Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü zu öffnen.

1. Klicken Sie im linken Seitenmenü unter **Services** auf das Symbol ![Kontrollkästchen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Content-Sets**.

1. Klicken Sie in der Tabelle auf der Seite **Content-Sets** rechts neben einem einbezogenen Inhaltspfad auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/ui_18/More.svg) und klicken Sie dann auf **Bearbeiten** oder **Löschen**.

![Bearbeiten des Content-Sets](/help/assets/edit-content-set.png)

## Kopieren von Inhalten {#copy-content}

Nachdem ein Content-Set erstellt wurde, können Sie es zum Kopieren von Inhalten verwenden. 

Eine Umgebung kann nicht ausgewählt werden, wenn eine der folgenden Bedingungen zutrifft:

* Die Benutzenden haben nicht die erforderlichen Berechtigungen.
* In der Umgebung wird gerade ein Pipeline- oder Inhaltskopiervorgang ausgeführt.

**So kopieren Sie Inhalte:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie oben links auf der Seite auf das Symbol ![Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü zu öffnen.

1. Klicken Sie im linken Seitenmenü unter **Services** auf das Symbol ![Kontrollkästchen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Content-Sets**.

1. Klicken Sie in der Tabelle auf der Seite **Content-Sets** rechts neben einem einbezogenen Inhaltspfad, den Sie kopieren möchten, auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/ui_18/More.svg) und dann auf **Inhalt kopieren**.

   ![Inhaltskopie](/help/assets/copy-content.png)

1. Geben Sie im Dialogfeld **Inhalt kopieren** die **Quelle** und das **Ziel** der jeweiligen Umgebungen für die Inhaltskopie-Aktion an.

   * Regionen in einer Zielumgebung müssen eine Untergruppe von Regionen in der Quellumgebung sein.
   * Bevor eine Aktion zum Kopieren von Inhalten ausgeführt wird, werden diese auf Kompatibilitätsprobleme geprüft. Wenn Sie eine Umgebung als **Ziel** auswählen, validiert das System automatisch die Quell- und Zielumgebung. Wenn die Validierung fehlschlägt, wird der Prozess angehalten und im Dialogfeld eine Fehlermeldung angezeigt, in der der Grund für den Fehler erläutert wird.

     ![Kopieren von Inhalten](/help/assets/copying-content.png)

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   1. Um die ausgeschlossenen Pfade in der Zielumgebung *beizubehalten*, aktivieren Sie **`Do not delete exclude paths from destination`**. Mit dieser Einstellung werden die im Content-Set angegebenen ausgeschlossenen Pfade beibehalten.
   1. Um die ausgeschlossenen Pfade in der Zielumgebung *zu entfernen*, deaktivieren Sie **`Do not delete exclude paths from destination`**. Mit dieser Einstellung werden die im Content-Set angegebenen ausgeschlossenen Pfade gelöscht.
   1. Um den Versionsverlauf der Pfade von der Quellumgebung in die Zielumgebung zu kopieren, aktivieren Sie die Option **Versionen kopieren**. Der Vorgang des Kopierens von Inhalten geht erheblich schneller, wenn der Versionsverlauf *nicht* kopiert wird.

1. Klicken Sie auf **Kopieren**. Der Status des Kopiervorgangs wird für das ausgewählte Content-Set in der Konsole angezeigt.

## Abrufen des Status einer Inhaltskopie {#copy-activity}

Sie können den Status der Kopierprozesse auf der Seite **Aktivität zum Kopieren von Inhalten** überwachen.

**So überprüfen Sie den Status einer Inhaltskopie:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie oben links auf der Seite auf das Symbol ![Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü zu öffnen.

1. Klicken Sie im linken Seitenmenü unter **Services** auf das Symbol ![Verlauf](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Aktivität zum Kopieren von Inhalten**.

   ![Aktivität zum Kopieren von Inhalten](/help/assets/copy-content-activity.png)

   Ein Inhaltskopiervorgang kann einen der folgenden Statuswerte haben:

   | Status | Beschreibung |
   | --- | --- |
   | In Bearbeitung | Der Inhaltskopiervorgang wird gerade durchgeführt. |
   | Abgeschlossen | Der Inhaltskopiervorgang wurde erfolgreich abgeschlossen. |
   | Fehlgeschlagen | Der Inhaltskopiervorgang ist fehlgeschlagen. |

## Einschränkungen der Inhaltskopie {#limitations}

* Eine Inhaltskopie kann nicht von einer niedrigeren Umgebung in eine höhere Umgebung durchgeführt werden.
* Das Kopieren von Inhalten kann nur innerhalb derselben Ebene durchgeführt werden. (d. h. Autor-Autor oder Veröffentlichung-Veröffentlichung).
* Eine programm- und regionenübergreifende Inhaltskopie ist nicht möglich.
* Eine Inhaltskopie für eine auf Cloud-Datenspeicher basierende Topologie kann nur durchgeführt werden, wenn sich die Quell- und Zielumgebung bei demselben Cloud-Anbieter und in derselben Region befinden.
* Die Ausführung gleichzeitiger Inhaltskopievorgänge in derselben Umgebung ist nicht möglich.
* Eine Inhaltskopie kann nicht durchgeführt werden, wenn ein aktiver Vorgang in der Ziel- oder Quellumgebung ausgeführt wird, z. B. eine CI/CD-Pipeline.
* Die Inhaltskopie sollte nicht als Klon- oder Spiegelwerkzeug verwendet werden, da damit keine verschobenen oder gelöschten Inhalte auf der Quelle verfolgt werden können.
* Eine Inhaltskopie kann nicht pausiert oder abgebrochen werden, wenn sie einmal initiiert wurde.
* Die Inhaltskopie dupliziert Assets und Dynamic Media-Metadaten aus der höheren Umgebung in die ausgewählte niedrigere Umgebung. Kopierte Assets müssen dann mithilfe des [Workflows zur DAM-Verarbeitung von Assets](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/using/assets-workflow) in der niedrigeren Umgebung neu verarbeitet werden, um die entsprechende Dynamic Media-Konfiguration zu verwenden.
* [Dynamic Media-Konfigurationen, für die Asset-Größen von mehr als 2 GB aktiviert sind](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb), werden nicht unterstützt.
* Die Regionen der Zielumgebung müssen mit den Regionen der Quellumgebung oder einer Teilmenge davon übereinstimmen.

## Bekannte Probleme der Inhaltskopie {#known-issues}

{{content-copy-known-issues}}
