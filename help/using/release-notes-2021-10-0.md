---
title: Versionshinweise für 2021.10.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.10.0
feature: Release Information
source-git-commit: 09dd8fe608d95cd9dbc95129cf86b9693c2839b5
workflow-type: ht
source-wordcount: '362'
ht-degree: 100%

---

# Versionshinweise für 2021.10.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] Version 2021.10.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.10.0 wurde am 14. Oktober 2021 veröffentlicht.

## Neue Funktionen {#whats-new}

* Produktions-Pipelines können jetzt im „Notfall“-Modus ausgeführt werden, wobei bei Notfall-Bereitstellungen die Sicherheits- und Leistungstestschritte umgangen werden.

* Um die Konsistenz mit Cloud Service sicherzustellen, werden bestehende Bereitstellungspipelines nun in der Benutzeroberfläche als „Full Stack“-Pipelines referenziert und gekennzeichnet.

* Die Pipeline-Karte wurde aktualisiert und zeigt jetzt ein einziges, integriertes Gesicht, das sowohl Produktions- als auch produktionsfremde Pipelines anzeigt, und der Benutzer kann direkt aus dem Aktionsmenü, das mit jeder Pipeline verknüpft ist, Ausführen/Pause/Fortsetzen auswählen.

* Ein Benutzer mit der Rolle „Implementierungs-Manager“ kann nun im Self-Service die Produktions-Pipeline über die Benutzeroberfläche löschen.

* Das Hinzufügen und Bearbeiten von Pipelines wurde aufgefrischt und verwendet jetzt vertraute, moderne Bedienelemente.

* Benutzer von Cloud Manager können ihr Feedback jetzt direkt über die Benutzeroberfläche über **Feedback** rechts oben auf der Landingpage übermitteln.

* Von der Cloud Manager-Benutzeroberfläche können jetzt jährliche SLA-Diagramme heruntergeladen werden.

* Ausführungen von Code-Qualitäts- und produktionsfremden Pipelines verwenden während des Build-Schritts jetzt einen effizienteren Prozess zum Klonen von flachen Elementen, was zu einer schnelleren Build-Zeit für Kunden mit besonders großen Git-Repositorys führt.

* Die Dokumentation zur Cloud Manager-API enthält jetzt einen interaktiven Playground, auf dem angemeldete Benutzer über ihren Browser mit der API experimentieren können. Weitere Informationen dazu finden sie unter [Cloud Manager-API-Playground](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/).

* Wenn eine Auswahloption unter „Navigieren zu“ deaktiviert ist, wird die QuickInfo auf der Programmkarte anschaulicher. Auf ihr steht nun: „Eine Produktionsumgebung existiert nicht.“


## Fehlerbehebungen {#bug-fixes}

* Wenn aus internen Systemen gelesene Daten nicht korrekt eingegeben werden, führt dies nicht mehr dazu, dass von CSEs bereitgestellte nicht verwandte Daten nicht ordnungsgemäß in Cloud Manager angezeigt werden.

* In bestimmten Kundensituationen werden ungültige Artefakte, die während des Build-Schritts heruntergeladen wurden und einen Build-Fehler verursacht haben sollten, nicht mehr ignoriert.
