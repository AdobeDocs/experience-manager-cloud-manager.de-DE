---
title: Versionshinweise für 2019.2.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.2.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.2.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.2.0.
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Versionshinweise für 2019.2.0 {#release-notes-for}

Die [!UICONTROL Cloud Manager]-Version 2019.2.0 umfasst eine neue Funktion zur Systemüberwachung. Darüber können Kunden den Status ihrer Adobe Managed Services-Umgebungen auf Systemebene anzeigen.


## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.2.0 wurde am 21. Februar 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Es gibt eine neue Systemüberwachungsfunktion. Weitere Informationen finden Sie unter [Überwachen von Umgebungen](monitor-your-environments.md).
* Das Dispatchermodul in von Assistenten generierten Projekten enthält jetzt eine README-Datei.
* Die Sortierreihenfolge von Codescanproblemen wurde verbessert und entspricht nun der Priorität des Problems.
* Stage-Instanzen werden jetzt auch im Fall eines Bereitstellungsfehlers immer im Load-Balancer wiederhergestellt.
* In Admin Console ist eine neue API-Entwicklerrolle verfügbar, über die bestimmte Anwender die Berechtigung zum Erstellen von Integrationen in der Adobe I/O-Konsole erhalten können. Weitere Informationen finden Sie unter [Verwalten von Entwicklern](https://www.adobe.com/go/aac_api_prod_learn) .
* Die Version des Maven-Archetyps wurde auf Version 16 aktualisiert.
* Maven wurde auf Version 3.6.0 aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Unter bestimmten Umständen wurden Pipelines nicht ausgeführt, wenn die Zielumgebung in Azure gehostet wurde.
* Die Anordnung der Umgebungen war inkonsistent.
* Leistungstests schlugen fehl, wenn in den erkannten Seitenpfaden ein Komma vorhanden war.
* Wenn eine Pipelineausführung über die Web-UI gestartet wurde, funktionierte die Browserschaltfläche „Zurück“ nicht ordnungsgemäß.
* Über die Links „Mehr erfahren“ auf der Seite „Übersicht“ wurde keine neue Registerkarte geöffnet.
* Beim Hochladen einer Programmminiaturansicht wurde diese möglicherweise nicht sofort angezeigt.
* In einigen Fällen schlug der Codescan aufgrund der projektspezifischen Konfiguration fehl.
* Der Link „Mehr erfahren“ auf der Karte „Nicht-Produktions-Pipelines“ führte nicht zur richtigen Stelle.
* Wenn ein Quality Gate überschrieben wurde, wurde der Status inkonsistent angezeigt.
* Kunden mit Cold-Standby-Topologien erhielten falsche Ergebnisse bei Sicherheitstests.
* Beim Erstellen eines neuen Projekts mit dem Assistenten war es nicht möglich, eine Verzweigung mit einem Bindestrich zu erstellen.

## Bekannte Probleme {#known-issues}

* Wenn Überwachungsdaten aktualisiert werden, werden alle verborgenen Reihen wieder eingeblendet.
* Kunden, die ihre vorhandenen SLA-Berichte anzeigen möchten, müssen bis zur nächsten Version manuell navigieren.

   Zum Formulieren dieser URL folgen Sie dem Muster (`https://<Experience Cloud URL>/content/mac/<Experience Cloud Tenant>/managedservices/sla.html`). Wenn beispielsweise Ihre Experience Cloud-URL (`https://weretailprod.experiencecloud.adobe.com`) lautet, ergibt sich hieraus die SLA-Berichte-URL (`https://weretailprod.experiencecloud.adobe.com/content/mac/weretailprod/managedservices/sla/html`).

   Dies wird in der nächsten Version behoben, wenn SLA-Berichte in [!UICONTROL Cloud Manager] verfügbar sind.
