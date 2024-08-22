---
title: Navigation durch die Cloud Manager-Benutzeroberfläche
description: Erfahren Sie, wie die Benutzeroberfläche von Cloud Manager aufgebaut ist und wie Sie Ihre Programme und Umgebungen verwalten.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 40%

---


# Navigieren zur Cloud Manager-Benutzeroberfläche {#navigation}

Erfahren Sie, wie die Benutzeroberfläche von Cloud Manager aufgebaut ist und wie Sie Ihre Programme und Umgebungen verwalten.

Die Benutzeroberfläche von Cloud Manager besteht hauptsächlich aus zwei grafischen Schnittstellen:

* [In der Konsole &quot;Meine Programme&quot;](#my-programs-console) können Sie alle Programme anzeigen und verwalten.
* [Im Fenster &quot;Programmübersicht&quot;](#program-overview) können Sie die Details eines einzelnen Programms anzeigen und verwalten.

## Meine Programmkonsole {#my-programs-console}

Wenn Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) anmelden und die entsprechende Organisation auswählen, gelangen Sie in die Konsole **Meine Programme**.

![Konsole „Meine Programme“](assets/my-programs-console.png)

Die Konsole „Meine Programme“ bietet einen Überblick über alle Programme, auf die Sie in der ausgewählten Organisation Zugriff haben. Sie besteht aus mehreren Teilen.

1. [Symbolleisten](#toolbars-my-programs-toolbars) für die Organisationsauswahl, Warnhinweise und Kontoeinstellungen.
1. Registerkarten, mit denen Sie die aktuelle Ansicht Ihrer Programme umschalten können.

   * **Home** -Ansicht (Standard), die die Ansicht **My Programs** mit einer Übersicht aller Programme auswählt.
   * **Lizenz** für den Zugriff auf das Lizenz-Dashboard. Das Lizenz-Dashboard gilt nur für *AEM as a Cloud Service-Programme* (AEMaaCS), nicht für AMS-Programme. Informationen zum Festlegen des Diensttyps für Ihr Programm (AEMaaCS oder AMS) finden Sie im Abschnitt [Programmkarten](#program-cards) dieses Artikels.
   * Die Registerkarten werden standardmäßig geschlossen und können über das Dropdown-Menü des Hamburger-Symbols auf der linken Seite der Kopfzeile [Cloud Manager](#cloud-manager-header) angezeigt werden.

1. [Aktionsaufrufe und Statistiken](#cta-statistics) für einen Überblick über Ihre aktuellen Aktivitäten
1. [**Meine Programme**](#my-programs-section) mit einem Überblick über Ihre gesamten Programme
1. [Quick links](#quick-links) für den einfachen Zugriff auf zugehörige Ressourcen

>[!TIP]
>
>Weitere Informationen zu Programmen finden Sie unter [Programme und Programmtypen](/help/getting-started/program-setup.md) .

### Symbolleisten {#my-programs-toolbars}

Es gibt zwei Symbolleisten übereinander.

#### Cloud Manager-Kopfzeile {#cloud-manager-header}

Der erste ist der Cloud Manager-Header. Die Kopfzeile ist beim Navigieren in Cloud Manager persistent. Er ist ein Anker, der Ihnen Zugriff auf Einstellungen und Informationen bietet, die für alle Cloud Manager-Programme gelten.

![Die Kopfzeile von Experience Cloud](assets/experience-cloud-header.png)

1. Das Hamburger-Symbol auf der linken Seite der Kopfzeile ist ein Dropdown-Menü, das Zugriff auf Registerkarten für bestimmte Teile eines Programms bietet. Je nach Kontext können Sie damit auch zwischen dem Lizenz-Dashboard und der Konsole **[Meine Programme](#my-programs-console)** wechseln.
   * Das Lizenz-Dashboard gilt nur für AEM as a Cloud Service-Programme, nicht für AMS-Programme.
   * Informationen zum Festlegen des Diensttyps für Ihr Programm (AMS oder AEMaaCS) finden Sie im Abschnitt [Programmkarten-Abschnitt](#program-cards) dieses Dokuments.
1. Über die Schaltfläche Cloud Manager gelangen Sie zurück zur Konsole &quot;Meine Programme&quot;von Cloud Manager, unabhängig davon, wo Sie sich in Cloud Manager befinden.
1. Klicken Sie auf die Schaltfläche Feedback , um Adobe Feedback zu Cloud Manager zu geben.
1. Der Organisationsselektor zeigt die Organisation an, bei der Sie sich derzeit angemeldet haben (in diesem Beispiel &quot;Foundation Intern&quot;). Klicken Sie auf , um zu einer anderen Organisation zu wechseln, wenn Ihre Adobe ID mehreren zugeordnet ist.
1. Durch Klicken auf den Lösungsschalter können Sie schnell zu anderen Experience Cloud-Lösungen wechseln.
1. Über das Hilfesymbol erhalten Sie schnellen Zugriff auf Lern- und Support-Ressourcen.
1. Das Benachrichtigungssymbol wird mit der Anzahl der derzeit zugewiesenen unvollständigen [Benachrichtigungen](/help/using/notifications.md) gekennzeichnet
1. Wählen Sie das Symbol für Ihre Benutzerin bzw. Ihren Benutzer aus, um auf Ihre Benutzereinstellungen zuzugreifen. Wenn Sie kein Benutzerbild auswählen, wird ein Symbol zufällig zugewiesen.

#### Programm-Symbolleiste {#program-toolbar}

Die Programmsymbolleiste enthält Links zum Wechseln zwischen Cloud Manager-Programmen und -Aktionen, die dem Kontext entsprechen.

![Programmsymbolleiste](assets/program-toolbar.png)

1. Die Programmauswahl wird in einer Dropdown-Liste geöffnet, in der Sie schnell andere Programme auswählen oder kontextbezogene Aktionen ausführen können, z. B. die Erstellung eines neuen Programms.
1. Über den Link &quot;Erste Schritte&quot;erhalten Sie Zugriff auf die Journey](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/overview) der Onboarding-Dokumentation, die Ihnen den Einstieg in Cloud Manager ermöglicht.
[
Die Onboarding-Journey wurde für Cloud Manager auf Adobe Experience Manager as a Cloud Service (AEMaaCS) und nicht für Cloud Manager auf Adobe Managed Services (AMS) entwickelt. Viele Konzepte sind jedoch gleich.
1. Die Aktionsschaltfläche bietet kontextbezogene Aktionen, z. B. die Erstellung eines neuen Programms.

### Aktionsaufrufe und Statistiken {#cta-statistics}

Im Abschnitt für Aktionsaufrufe und Statistiken finden Sie zusammengefasste Daten zu Ihrer Organisation. Wenn Sie z. B. Ihre Programme erfolgreich eingerichtet haben, können Sie hier Statistiken über Ihre Aktivitäten der letzten 90 Tage einsehen, u. a.:

* Anzahl der [Bereitstellungen](/help/using/code-deployment.md)
* Anzahl der identifizierten [Code-Qualitätsprobleme](/help/using/code-quality-testing.md)
* Anzahl der Builds

Oder wenn Sie gerade mit der Einrichtung Ihrer Organisation beginnen, gibt es Tipps zu den nächsten Schritten oder Dokumentationsressourcen.

### Meine Programme {#my-programs-section}

Der Hauptinhalt der Konsole „Meine Programme“ ist der Abschnitt **Meine Programme**, in dem Ihre Programme als einzelne Karten aufgeführt sind. Klicken Sie auf eine Karte, um die Seite **Programmübersicht** des Programms mit Details zum Programm aufzurufen.

>[!NOTE]
>
>Je nach Ihren Berechtigungen können Sie bestimmte Programme möglicherweise nicht auswählen.

Verwenden Sie die folgenden Sortieroptionen, damit Sie das benötigte Programm besser finden können:

![Sortieroptionen](assets/my-programs-sorting.png)

* Sortieren nach
   * Erstellungsdatum (Standard)
   * Programmname
   * Status
* Aufsteigend (Standard)/Absteigend
* Rasteransicht (Standard)
* Listenansicht

#### Programmkarten {#program-cards}

Eine Karte oder Zeile in einer Tabelle stellt jedes Programm dar, bietet einen Überblick über das Programm und schnelle Links, über die Maßnahmen ergriffen werden können.

![Programmkarte](assets/program-card.png)

* Programmbild (falls konfiguriert)
* Programmname
* Diensttyp:
   * **Experience Manager** für AMS-Programme
   * **Experience Manager Cloud** für [AEM as a Cloud Service-Programme](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/home)
* Status
* Konfigurierte Lösungen
* Erstellungsdatum

Über das Informationssymbol erhalten Sie auch Schnellzugriff auf zusätzliche Informationen zum Programm (nützlich in der Listenansicht).

![Informationen](assets/information-view.png)

Über das Symbol mit Auslassungspunkten haben Sie Zugriff auf weitere Aktionen, die Sie im Programm ausführen können.

![Schaltfläche mit Auslassungspunkten für Programme](assets/program-ellipsis.png)

* Navigieren zu einer bestimmten [Umgebung](/help/using/managing-environments.md) des Programms
* Öffnen der [Programmübersicht](#program-overview)
* [Bearbeiten des Programms](/help/getting-started/program-setup.md)
* Anzeigen der Überwachung

### Schnell-Links {#quick-links}

Über den Schnelllink-Bereich erhalten Sie Zugriff auf hilfreiche, zugehörige Ressourcen.

## Fenster &quot;Programmübersicht&quot; {#program-overview}

Wenn Sie ein Programm in der Konsole [**Meine Programme**](#my-programs-console) auswählen, gelangen Sie zur Seite **Programmübersicht** .

![Programmübersicht](assets/program-overview.png)

Über die Programmübersicht erhalten Sie Zugriff auf alle Details eines Cloud Manager-Programms. Wie die Konsole „Meine Programme“ besteht sie aus mehreren Teilen.

1. [Symbolleisten](#program-overview-toolbar) , um schnell zur Konsole **Meine Programme** zurückzuspringen und durch das Programm zu navigieren.
1. [Registerkarten](#program-tabs) verwenden, um zwischen verschiedenen Aspekten des Programms zu wechseln.
1. Ein [Aktionsaufruf](#cta) , der auf den letzten Aktionen des Programms basiert.
1. Eine [Übersicht über die Umgebungen](#environments) des Programms.
1. Eine [Übersicht über die Pipelines](#pipelines) des Programms.
1. Links zu [nützlichen Ressourcen](#useful-resources).

### Symbolleisten {#program-overview-toolbar}

Die Symbolleisten für die Programmübersicht ähneln den Symbolleisten der Konsole [Meine Programme](#my-programs-toolbars). Hier werden nur die Unterschiede veranschaulicht.

#### Cloud Manager-Kopfzeile {#cloud-manager-header-2}

Der Cloud Manager-Header verfügt über ein Dropdown-Menü für Hamburger-Symbole, das automatisch geöffnet wird und die navigierbaren Registerkarten der Programmübersicht anzeigt.

![Cloud Manager Hamburger-Symbol-Dropdown-Menü](assets/cloud-manager-hamburger.png)

Klicken Sie auf das Hamburger-Symbol, um die Registerkarten auszublenden.

#### Programm-Symbolleiste {#program-toolbar-2}

Die Programmsymbolleiste bietet Ihnen weiterhin Zugriff auf den schnellen Wechsel zu anderen Programmen, bietet aber zusätzlich Zugriff auf kontextbezogene Aktionen wie das Hinzufügen und Bearbeiten des Programms.

![Programmsymbolleiste](assets/cloud-manager-program-toolbar.png)

Wenn Sie die Registerkarten über das Hamburger-Symbol ausblenden, kann die Symbolleiste auch die Registerkarte anzeigen, auf der Sie sich gerade befinden.

### Programm-Tabs {#program-tabs}

Jedem Programm sind zahlreiche Optionen und Daten zugeordnet. Diese Daten werden in Registerkarten zusammengefasst, um die Navigation im Programm zu vereinfachen. Die Registerkarten bieten Zugriff auf:

* Übersicht: Die im aktuellen Dokument beschriebene Programmübersicht
* [Aktivität](/help/using/managing-pipelines.md#activity): Verlauf der Pipeline-Ausführungen des Programms
* [Pipelines](/help/using/managing-pipelines.md#pipelines): Alle für das Programm konfigurierten Pipelines
* [Repositorys](/help/managing-code/managing-repositories.md): Alle für das Programm konfigurierten Repositorys
* [Berichte](/help/using/monitoring-environments.md#system-monitoring-overview): Metriken wie SLA-Daten
* [Umgebungen](/help/using/managing-environments.md): Alle für das Programm konfigurierten Umgebungen
* [Content-Sets](/help/using/content-copy.md): Sätze von Inhalten, die zu Kopierzwecken festgelegt wurden
* [Aktivität „Inhalt kopieren“](/help/using/content-copy.md): Aktivitäten zur Inhaltskopie
* Lernpfade: Zusätzliche Lernressourcen zu Cloud Manager

Wenn Sie ein Programm öffnen, gelangen Sie standardmäßig zur Registerkarte **Übersicht**. Die aktuelle Registerkarte ist hervorgehoben. Wählen Sie eine andere Registerkarte aus, um deren Details anzuzeigen.

Verwenden Sie das Hamburger-Symbol in der Kopfzeile [Cloud Manager](#cloud-manager-header-2), um die Registerkarten auszublenden.

### Aktionsaufruf {#cta}

Im Abschnitt Aktionsaufruf finden Sie nützliche Informationen in Abhängigkeit vom Status Ihres Programms. Für ein neues Programm werden möglicherweise die nächsten Schritte und eine Erinnerung an ein Live-Datum angezeigt, [bei der Programmerstellung festgelegt](/help/getting-started/program-setup.md).

Bei einem Live-Programm den Status Ihrer letzten Bereitstellung mit Links zu Details und zum Beginn einer neuen Bereitstellung.

![Aktionsaufruf](assets/info-banner.png)

### Umgebungskarte {#environments}

Die Karte **Umgebungen** bietet Ihnen einen Überblick über Ihre Umgebungen und Links für Schnellaktionen.

Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicken Sie auf **Alle anzeigen**, um alle Umgebungen des Programms zu sehen.

Weitere Informationen zum Verwalten Ihrer Umgebungen finden Sie unter [Verwalten von Umgebungen](/help/using/managing-environments.md) .

### Pipelines-Karte {#pipelines}

Die Karte **Pipelines** bietet Ihnen einen Überblick über Ihre Pipelines und Links für Schnellaktionen.

Auf der Karte **Pipelines** sind nur drei Pipelines aufgeführt. Klicken Sie auf **Alle anzeigen**, um alle Pipelines des Programms zu sehen.

Weitere Informationen zur Verwaltung Ihrer Pipelines finden Sie unter [Verwalten von Pipelines](/help/using/managing-pipelines.md) .

### Nützliche Ressourcen {#useful-resources}

Der Abschnitt **Nützliche Ressourcen** enthält Links zu zusätzlichen Lernressourcen für Cloud Manager.
