---
title: Nicht-Produktions-Pipelines konfigurieren
description: Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: ba08da1b25a1f9ba8bc954b2fbd27b60d4ddf1a0
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 55%

---

# Nicht-Produktions-Pipelines konfigurieren {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen. Wenn Sie zunächst einen konzeptionellen Überblick darüber erhalten möchten, wie Pipelines in Cloud Manager funktionieren, finden Sie weitere Informationen unter [CI/CD-Pipelines](/help/overview/ci-cd-pipelines.md).

## Übersicht {#overview}

Über die Kachel **Pipelines** in [!UICONTROL Cloud Manager] kann der **Bereitstellungs-Manager** zwei verschiedene Arten von Pipelines erstellen.

* **Produktions-Pipelines**: Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte umfasst, um Quell-Code vollständig in die Produktion zu übernehmen.
* **Produktionsfremde Pipelines**: Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf produktionsfremde Pipelines. Weitere Informationen zum Konfigurieren von Produktions-Pipelines finden Sie im Dokument [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) .

Es gibt zwei Arten von produktionsfremden Pipelines:

* **Codequalitätspipelines** - Diese führen Code-Qualitätsprüfungen für den Code in einer Git-Verzweigung durch und führen die Schritte zum Erstellen und zur Codequalität aus.
* **Implementierungs-Pipelines** - Diese Pipelines führen zusammen mit den Build- und Codequalitätsschritten wie den Code-Qualitäts-Pipelines auch den Code in einer Nicht-Produktionsumgebung aus.

>[!NOTE]
>
>Eine Pipeline kann erst eingerichtet werden, wenn ihr verknüpftes Git-Repository mindestens eine Verzweigung aufweist und die [Programmeinrichtung](/help/getting-started/program-setup.md) abgeschlossen ist. Informationen zum Hinzufügen und Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/managing-code/managing-repositories.md) .

## Hinzufügen einer Nicht-Produktions-Pipeline {#add-non-production-pipeline}

Sobald Sie mit der Benutzeroberfläche von Cloud Manager Ihr Programm eingerichtet und mindestens eine Umgebung haben, können Sie eine produktionsfremde Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte „Pipelines“ über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **Hinzufügen** und wählen Sie dann **Nicht-Produktions-Pipeline hinzufügen** aus.

   ![Produktionsfremde Pipeline hinzufügen](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Wählen Sie auf der Registerkarte **Konfiguration** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** den zu erstellenden Pipeline-Typ aus: entweder **Codequalitäts-Pipeline** oder **Bereitstellungspipeline**.

   ![Pipeline-Typ wählen](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Geben Sie im Feld **Name der produktionsfremden Pipeline** eine Beschreibung für die Pipeline an.

1. Wenn Sie eine **Bereitstellungs-Pipeline** erstellen möchten, wählen Sie im Dropdown-Menü **Berechtigte Bereitstellungsumgebungen** die Ziel-Bereitstellungsumgebung aus.

1. Geben Sie das Repository an, aus dem die Pipeline den Code abrufen soll.

   * **Repository** - Definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.
   * **Git-Verzweigung** - Definiert aus welcher Verzweigung in Git, dass die ausgewählte Pipeline den Code abrufen soll.

1. Definieren Sie die Bereitstellungsoptionen.

   1. Definieren Sie unter **Bereitstellungsauslöser**, durch welches Ereignis die Pipeline aktiviert werden soll.

      * **Manuell** - Hiermit können Sie die Pipeline manuell starten.
      * **Bei Git-Änderungen** - Startet die Pipeline, wenn der konfigurierten Git-Verzweigung Commits hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf weiterhin manuell starten.

   1. Für Bereitstellungs-Pipelines definieren Sie unter **Verhalten bei wichtigen Metrikfehlern** das Verhalten der Pipeline, wenn ein wichtiger Fehler in einem der Quality Gates auftritt.

      * **Jedes Mal fragen** - Die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
      * **Sofort fehlschlagen** - Die Pipeline wird abgebrochen, sobald ein wichtiger Fehler auftritt. Damit werden im Grunde Benutzende simuliert, die manuell jeden Fehler ablehnen.
      * **Sofort fortfahren** - Die Pipeline wird automatisch fortgesetzt, wenn ein wichtiger Fehler auftritt. Damit werden im Grunde Benutzende simuliert, die manuell jeden Fehler genehmigen.

   1. **Dispatcher-Konfiguration** - Die Rolle **Bereitstellungsmanager** kann eine Reihe von Inhaltspfaden konfigurieren, die entweder ungültig gemacht oder aus dem AEM Dispatcher-Cache entfernt werden, wenn eine Pipeline ausgeführt wird. Diese Cache-Aktionen werden im Rahmen des Implementierungs-Pipeline-Schritts ausgeführt, unmittelbar nachdem alle Inhaltspakete bereitgestellt wurden. Diese Einstellungen verwenden das Standardverhalten von AEM Dispatcher. Konfigurieren:

      1. Geben Sie unter **PATH** einen Pfad für den Inhalt an.
      1. Wählen Sie unter **TYPE** die Aktion aus, die mit dem Pfad durchgeführt werden soll.

         * **Leeren**: Löschen des Cache-Inhalts.
         * **Invalidieren**: Eine Cache-Invalidierung durchführen, ähnlich wie bei der Aktivierung von Inhalten von einer Autoreninstanz auf einer Veröffentlichungsinstanz.

      1. Klicken Sie auf **Pfad hinzufügen**, um den angegebenen Pfad hinzuzufügen. Sie können bis zu 100 Pfade pro Umgebung hinzufügen.

1. Klicken Sie auf **Speichern**.

## Die nächsten Schritte {#the-next-steps}

Nachdem Sie die Pipeline konfiguriert haben, können Sie Ihren Code bereitstellen. Weitere Informationen finden Sie unter [Codebereitstellung](/help/using/code-deployment.md) .

## Video-Tutorial {#video-tutorial}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess, der in diesem Dokument beschrieben wird.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
