---
title: Inhaltskopie für Umgebungskonsistenz
description: Mit der Inhaltskopie in Cloud Manager können Benutzer veränderliche Inhalte On-Demand aus Adobe Managed Services-gehosteten Adobe Experience Manager 6.x-Produktionsumgebungen in niedrigere Testumgebungen kopieren.
exl-id: 97915e58-a1d3-453f-b5ce-cad55ed73262
source-git-commit: e3a656605ac59ca1f95985426932fddf2b53b7c9
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 34%

---


# Inhaltskopie zur Konsistenz der Umgebung {#content-copy}

Mit der Inhaltskopie in Cloud Manager können Benutzer veränderliche Inhalte On-Demand aus Adobe Managed Services-gehosteten Adobe Experience Manager 6.x-Produktionsumgebungen in niedrigere Testumgebungen kopieren.

## Über Content Copy {#introduction}

Aktuelle, echte Daten sind für Tests, Validierung und Benutzerakzeptanz nützlich. Mit der Inhaltskopie können Sie Inhalte aus Ihrer Produktions-AMS-gehosteten AEM 6.x-Umgebung in Staging- oder Entwicklungsumgebungen kopieren. Dieser Workflow unterstützt verschiedene Testszenarien.

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

Um die Funktion &quot;Inhaltskopie&quot;verwenden zu können, muss der Benutzer der Rolle **Bereitstellungsmanager** in der Quell- und Zielumgebung zugewiesen sein.

## Inhaltssatz erstellen {#create-content-set}

Bevor Inhalt kopiert werden kann, muss ein Content-Set definiert werden. Nach der Definition können Content-Sets zum Kopieren von Inhalten wiederverwendet werden. Gehen Sie wie folgt vor, um ein Content-Set zu erstellen.

**So erstellen Sie einen Inhaltssatz:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie in der linken oberen Ecke der Seite auf ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Menü links zu öffnen.

1. Klicken Sie im Menü auf der linken Seite unter der Seite **Dienste** auf das Symbol ![Kontrollkästchen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Inhaltssets**.

1. Klicken Sie in der rechten oberen Ecke der Seite auf **Inhaltsset hinzufügen**.

   ![Content-Sets](/help/assets/content-sets.png)

1. Geben Sie im Dialogfeld **`Add Content Set`** auf der Registerkarte **Details** in den Feldern **Name** und **Beschreibung** einen Namen und eine optionale Beschreibung für den Inhaltssatz ein und klicken Sie dann auf **Weiter**.

   ![Content-Set-Details](/help/assets/add-content-set-details.png)

1. Geben Sie auf der Registerkarte **Inhaltspfade** im Textfeld **Pfad** einen Pfad zum Inhalt an, der geändert werden kann und in den Inhaltssatz aufgenommen werden soll.

   Nur Pfade, die mit `/content`, `/conf`, `/etc`, `/var/workflow/models` oder `/var/commerce` beginnen, können einbezogen werden.

1. Klicken Sie auf das Symbol &quot;**![Ordner hinzufügen&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderAdd_18_N.svg) Pfad hinzufügen**&quot;, um den Pfad zum Inhaltsset hinzuzufügen (oder darin einzuschließen).

1. (Optional) Fügen Sie bei Bedarf weitere Pfade (bis zu 50) hinzu, indem Sie die vorherigen beiden Schritte wiederholen. Fahren Sie andernfalls mit dem nächsten Schritt fort.

   ![Hinzufügen von Pfaden zu Content-Sets](/help/assets/add-content-set-paths.png)

1. (Optional) Um Ihren Inhaltssatz einzugrenzen, können Sie optional Unterpfade in einem eingeschlossenen Inhaltspfad angeben, die ausgeschlossen werden sollen.

   1. Klicken Sie rechts neben einem eingeschlossenen Inhaltspfad, den Sie beschränken möchten, auf das Symbol ![Ordnerlöschung](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg).
   1. Geben Sie im Textfeld einen relativen Pfad zum im Dialogfeld angezeigten Stammverzeichnis ein.
   1. Klicken Sie auf das Symbol ![Ordnerlöschung](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderDelete_18_N.svg) **Pfad ausschließen**.
   1. Wiederholen Sie gegebenenfalls die Schritte i bis iii. weiter oben, um weitere Ausschlusspfade hinzuzufügen. Es gibt keine Einschränkung. Fahren Sie andernfalls mit dem nächsten Schritt fort.

   ![Ausschließen von Pfaden](/help/assets/add-content-set-paths-excluded.png)

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   1. Klicken Sie rechts neben einem ausgeschlossenen Unterpfad auf das Symbol &quot;![Größe 500 überschreiten&quot;](https://spectrum.adobe.com/static/icons/ui_18/CrossSize500.svg) , um ihn zu löschen.
   1. Klicken Sie auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/ui_18/More.svg)&quot;rechts neben einem eingeschlossenen Inhaltspfad und klicken Sie dann auf &quot;**Bearbeiten**&quot;oder &quot;**Löschen**&quot;.

   ![Bearbeiten der Pfadliste](/help/assets/add-content-set-excluded-paths.png)

1. Klicken Sie auf **Erstellen**. Sie können jetzt den Inhaltssatz verwenden, um Inhalte zwischen Umgebungen zu kopieren.

## Inhaltsset bearbeiten oder löschen {#edit-content-set}

Wenn Sie einen Inhaltssatz bearbeiten, müssen Sie möglicherweise die konfigurierten Pfade erweitern, um die ausgeschlossenen Unterpfade anzuzeigen.

**So bearbeiten oder löschen Sie einen Inhaltsset:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie in der linken oberen Ecke der Seite auf ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Menü links zu öffnen.

1. Klicken Sie im Menü auf der linken Seite unter **Dienste** auf das Symbol ![Kontrollkästchen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Inhaltssets**.

1. Klicken Sie in der Tabelle auf der Seite **Inhaltssets** rechts neben einem eingeschlossenen Inhaltspfad auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/ui_18/More.svg) und klicken Sie dann auf **Bearbeiten** oder **Löschen**.

![Bearbeiten des Content-Sets](/help/assets/edit-content-set.png)

## Inhalt kopieren {#copy-content}

Nachdem ein Inhaltssatz erstellt wurde, können Sie ihn zum Kopieren von Inhalten verwenden.

Eine Umgebung kann nicht ausgewählt werden, wenn eine der folgenden Bedingungen zutrifft:

* Dem Benutzer fehlen die erforderlichen Berechtigungen.
* Ein Pipeline- oder Inhaltskopiervorgang wird derzeit in der Umgebung ausgeführt.

**So kopieren Sie Inhalt:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie in der linken oberen Ecke der Seite auf ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Menü links zu öffnen.

1. Klicken Sie im Menü auf der linken Seite unter **Dienste** auf das Symbol ![Kontrollkästchen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg) **Inhaltssets**.

1. Klicken Sie in der Tabelle auf der Seite **Inhaltssets** rechts neben einem eingeschlossenen Inhaltspfad, den Sie kopieren möchten, auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/ui_18/More.svg) und klicken Sie dann auf &quot;**Inhalt kopieren**&quot;.

   ![Inhaltskopie](/help/assets/copy-content.png)

1. Wählen Sie im Dialogfeld &quot;**Inhalt kopieren**&quot;die Umgebung &quot;**Source**&quot;und die Umgebung &quot;**Ziel**&quot;für die Aktion zum Kopieren von Inhalten aus.

   * Regionen in einer Zielumgebung müssen eine Teilmenge von Regionen in einer Quellumgebung sein.
   * Kompatibilitätsprobleme werden geprüft, bevor eine Aktion zum Kopieren von Inhalten ausgeführt wird. Wenn Sie die Umgebung **Ziel** auswählen, validiert das System automatisch die Quell- und Zielumgebungen. Wenn die Validierung fehlschlägt, wird der Prozess angehalten und im Dialogfeld wird eine Fehlermeldung angezeigt, in der der Grund für den Fehler erläutert wird.

     ![Kopieren von Inhalten](/help/assets/copying-content.png)

1. (Optional) Führen Sie einen der folgenden Schritte aus:

   1. Um die ausgeschlossenen Pfade in der Zielumgebung beizubehalten, aktivieren Sie **`Do not delete exclude paths from destination`**. ** Mit dieser Einstellung bleiben die im Inhaltssatz angegebenen ausgeschlossenen Pfade intakt.
   1. Um *die ausgeschlossenen Pfade in der Zielumgebung zu entfernen, deaktivieren Sie **`Do not delete exclude paths from destination`**.* Mit dieser Einstellung werden die im Inhaltssatz angegebenen ausgeschlossenen Pfade gelöscht.
   1. Um den Versionsverlauf der Pfade von der Quellumgebung in die Zielumgebung zu kopieren, aktivieren Sie die Option **Versionen kopieren** . Der Content Copy-Prozess ist erheblich schneller, wenn der Versionsverlauf *nicht* kopiert wird.

1. Klicken Sie auf **Kopieren**. Der Status des Kopiervorgangs wird für das ausgewählte Content-Set in der Konsole angezeigt.

## Prüfen des Status einer Inhaltskopie {#copy-activity}

Sie können den Status der Kopierprozesse auf der Seite **Aktivität zum Kopieren von Inhalten** überwachen.

**Überprüfen des Status einer Inhaltskopie:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie in der linken oberen Ecke der Seite auf ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Menü links zu öffnen.

1. Klicken Sie im Menü auf der linken Seite unter **Dienste** auf das Symbol ![Verlauf ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_History_18_N.svg) **Aktivität &quot;Inhalt kopieren&quot;**.

   ![Aktivität zum Kopieren von Inhalten](/help/assets/copy-content-activity.png)

   Ein Inhaltskopierprozess kann einen der folgenden Status aufweisen:

   | Status | Beschreibung |
   | --- | --- |
   | In Bearbeitung | Der Vorgang zum Kopieren von Inhalten ist noch nicht abgeschlossen. |
   | Abgeschlossen | Der Inhaltskopiervorgang wurde erfolgreich abgeschlossen. |
   | Fehlgeschlagen | Vorgang zum Kopieren von Inhalten fehlgeschlagen. |

## Einschränkungen der Inhaltskopie {#limitations}

* Eine Inhaltskopie kann nicht von einer niedrigeren Umgebung in eine höhere Umgebung durchgeführt werden.
* Das Kopieren von Inhalten kann nur innerhalb derselben Ebene durchgeführt werden. (d. h. Autor-Autor oder Veröffentlichung-Veröffentlichung).
* Eine programm- und regionenübergreifende Inhaltskopie ist nicht möglich.
* Eine Inhaltskopie für eine auf Cloud-Datenspeicher basierende Topologie kann nur durchgeführt werden, wenn sich die Quell- und Zielumgebung bei demselben Cloud-Anbieter und in derselben Region befinden.
* Die Ausführung gleichzeitiger Inhaltskopievorgänge in derselben Umgebung ist nicht möglich.
* Eine Inhaltskopie kann nicht durchgeführt werden, wenn ein aktiver Vorgang in der Ziel- oder Quellumgebung ausgeführt wird, z. B. eine CI/CD-Pipeline.
* Die Inhaltskopie sollte nicht als Klonen- oder Spiegelwerkzeug verwendet werden, da sie keine verschobenen oder gelöschten Inhalte auf der Quelle verfolgen kann.
* Eine Inhaltskopie kann nicht pausiert oder abgebrochen werden, nachdem sie initiiert wurde.
* Beim Kopieren von Inhalten werden Assets und Dynamic Media-Metadaten aus der höheren Umgebung in die ausgewählte niedrigere Umgebung dupliziert. Kopierte Assets müssen dann mithilfe des [Workflows zur DAM-Verarbeitung von Assets](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/using/assets-workflow) in der niedrigeren Umgebung neu verarbeitet werden, um die entsprechende Dynamic Media-Konfiguration zu verwenden.
* [Dynamic Media-Konfigurationen mit aktivierten Asset-Größen von mehr als 2 GB](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/assets/dynamic/config-dms7#optional-config-dms7-assets-larger-than-2gb) werden nicht unterstützt.
* Die Regionen der Zielumgebung müssen mit den Regionen der Quellumgebung oder einer Teilmenge davon übereinstimmen.

## Bekannte Probleme bei der Inhaltskopie {#known-issues}

{{content-copy-known-issues}}
