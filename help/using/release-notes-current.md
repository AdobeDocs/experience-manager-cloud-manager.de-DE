---
title: Versionshinweise für 2021.5.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.5.0.
feature: Versionshinweise
translation-type: tm+mt
source-git-commit: 5f81fdb86b1dfa6c748bb7784ef00dc062c9f8ef
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 21%

---

# Versionshinweise für 2021.5.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2021.5.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.5.0 wurde am 06. Mai 2021 veröffentlicht.
Die nächste Version ist für den 06. Juni 2021 geplant.

## Neue Funktionen {#whats-new}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, und zwar in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Im Arbeitsablauf &quot;Programm bearbeiten&quot;kann der Benutzer nur Nicht-Dezimalzahl-KPI-Werte festlegen.

* Zwischenweise auftretende Fehler beim Senden von Code an Adobe Git wurden nun behoben.

* Das Erlebnis &quot;Programm bearbeiten&quot;wurde aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Gelegentlich wird dem Benutzer der Status &quot;*aktiv*&quot;neben einer IP-Zulassungsliste auch dann grün angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Statt &#39;gelöschte&#39; Variablen zu entfernen, markiert die API der Pipelines-Variablen sie nur mit dem Status &#39;DELETED&#39;.

* Einige Qualitätsprobleme mit Code-Geruch haben die Zuverlässigkeitsbewertung fälschlicherweise beeinflusst.

* Wenn eine Pipeline-Ausführung zwischen Mitternacht und 1am UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als eine Version, die am Vortag erstellt wurde.
