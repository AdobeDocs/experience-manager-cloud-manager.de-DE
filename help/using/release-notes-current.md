---
title: Versionshinweise für 2021.10.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.10.0
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b28f8f1bedb92428d332716510cbf0fd714fada6
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 20%

---

# Versionshinweise für 2021.10.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] Version 2021.10.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.10.0 wurde am 14. Oktober 2021 veröffentlicht.
Die nächste Version ist für den 4. November 2021 geplant.

## Neue Funktionen {#whats-new}

* Produktions-Pipelines können jetzt im &quot;Notfall&quot;-Modus ausgeführt werden, wobei die Sicherheits- und Leistungstestschritte für Notbereitstellungen umgangen werden.

* Um die Konsistenz mit Cloud Service sicherzustellen, werden bestehende Implementierungs-Pipelines nun in der Benutzeroberfläche als &quot;Full Stack&quot;-Pipelines referenziert und gekennzeichnet.

* Die Pipeline-Karte wurde aktualisiert und zeigt jetzt ein einziges, integriertes Gesicht, das sowohl Produktions- als auch Nicht-Produktions-Pipelines anzeigt, und der Benutzer kann Ausführen/Aussetzen/Fortsetzen direkt aus dem Aktionsmenü auswählen, das mit jeder Pipeline verknüpft ist.

* Ein Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;kann nun die Produktions-Pipeline über die Benutzeroberfläche auf Self-Service-Weise löschen.

* Das Hinzufügen und Bearbeiten von Pipeline-Erlebnissen wurde aktualisiert und verwendet jetzt vertraute, moderne Modale.

* Benutzer von Cloud Manager können jetzt über die Schaltfläche **Feedback** oben rechts auf der Landingpage Feedback direkt aus der Benutzeroberfläche senden.

* Jährliche SLA-Diagramme können jetzt von der Cloud Manager-Benutzeroberfläche heruntergeladen werden.

* Code-Qualitäts- und Nicht-Produktions-Pipeline-Ausführungen verwenden jetzt während des Build-Schritts einen effizienteren Prozess zum Klonen von flachen Elementen, was zu einer schnelleren Build-Zeit für Kunden mit besonders großen Git-Repositorys führt.

* Die Dokumentation zur Cloud Manager-API enthält jetzt einen interaktiven Spielplatz, auf dem angemeldete Benutzer über ihren Browser mit der API experimentieren können. Weitere Informationen finden Sie unter [Cloud Manager API Playground](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) .

* Die QuickInfo auf der Programmkarte ist beschreibender, wenn eine Auswahloption unter &quot;Navigieren zu&quot;deaktiviert ist. Es wird nun gesagt: &quot;Eine Produktionsumgebung existiert nicht.&quot;


## Fehlerbehebungen {#bug-fixes}

* Wenn aus internen Systemen gelesene Daten nicht korrekt eingegeben wurden, kann dies dazu führen, dass von CSEs bereitgestellte nicht verwandte Daten nicht ordnungsgemäß in Cloud Manager angezeigt werden.

* In bestimmten Kundensituationen wurden ungültige Artefakte, die während des Build-Schritts heruntergeladen wurden und einen Build-Fehler verursacht haben sollten, ignoriert.
