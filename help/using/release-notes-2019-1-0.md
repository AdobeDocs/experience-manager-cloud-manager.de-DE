---
title: Versionshinweise für 2019.1.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.1.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.1.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.1.0.
uuid: 3af5808f-828f-4846-bee4-1e62194b48ad
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: Versionshinweise
discoiquuid: 85a1dcf3-2eef-4ba8-b4d1-09e4a88c7bd0
translation-type: ht
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Versionshinweise für 2019.1.0 {#release-notes-for}

Die [!UICONTROL Cloud Manager]-Version 2018.9.0 unterstützt nun das Testen von AEM Assets-Programmen und zusätzlichen Pipelinetypen, über die die Build- und Codequalitätsschritte ausgeführt werden. Optional ist die Bereitstellung in einer Nicht-Produktionsumgebung möglich.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.1.0 wurde am 17. Januar 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* AEM Assets-Leistungstests werden nun unterstützt. Weitere Informationen finden Sie unter [Konfigurieren der CI/CD-Pipeline](configuring-pipeline.md).
* Pipelines, die ausschließlich Build- und Codequalitätsschritte ausführen, und Pipelines zum Bereitstellen in Nicht-Produktionsumgebungen werden nun unterstützt. Weitere Informationen finden Sie unter [Konfigurieren der CI/CD-Pipeline](configuring-pipeline.md) im Abschnitt **Reine Nicht-Produktions- und Codequalitätspipelines**.
* Benutzerdefinierte Umgebungsvariablen in der Buildumgebung werden nun unterstützt. Weitere Informationen finden Sie unter [Erstellen von AEM-Anwendungsprojekten](create-an-application-project.md).
* Kunden mit mehreren Staging- oder Produktionsumgebungen können auf der Seite [CI/CD-Pipeline konfigurieren](configuring-pipeline.md) festlegen, welche Umgebung als Teil der Produktionspipeline bereitgestellt wird.
* httxt2dbm wurde dem Buildcontainer hinzugefügt.
* Sie können über alle Elemente des Hilfemenüs eine neue Registerkarte öffnen.

## Fehlerbehebungen {#bug-fixes}

* Beim Bearbeiten eines Programms konnten alle Seitensätze abgewählt werden.
* Der Genehmigungsschritt hatte einen falschen Titel.
* In einigen Fällen wurde das Programmlogo falsch maskiert.
* Wenn nur ein Dispatcherkonfigurationspaket erstellt wurde, schlug der Bereitstellungsschritt fehl.
* Umgebungen mit Cold-Standby-Instanzen wurden nicht richtig verarbeitet.
* Einige beendete Programme wurden im Programmumschalter angezeigt.
* Wenn dem Git-Repository während der Pipelinebearbeitung eine neue Verzweigung hinzugefügt wurde, stand diese möglicherweise nicht sofort zur Auswahl zur Verfügung.
* Auf einigen Bildschirmen wurde das Developer Connection-Symbol nicht im Menü „Hilfe“ angezeigt.
* Das Tabulatorzeichen wurde im Konfigurationsdialogfeld zum Dispatcherflushing nicht ordnungsgemäß verarbeitet.

## Bekannte Probleme {#known-issues}

* Beim Öffnen eines Programms, das Sites enthält, aber keine Assets oder KPIs, sehen alle Anwender eine Aktionskarte mit der Schaltfläche **Programm einrichten**. Allerdings können nur Anwender mit der Rolle „Business Owner“ auf die Schaltfläche **Programm einrichten** klicken.