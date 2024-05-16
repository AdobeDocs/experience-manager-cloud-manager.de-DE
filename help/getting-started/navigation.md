---
title: Navigieren zur Cloud Manager-Benutzeroberfläche
description: Erfahren Sie, wie die Cloud Manager-Benutzeroberfläche organisiert ist und wie Sie zur Verwaltung Ihrer Programme und Umgebungen navigieren.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: 9d0f4dd29e2d05ab3f6900ee23c536b91c849e65
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 18%

---

# Navigieren in der Cloud Manager-Benutzeroberfläche {#navigation}

Erfahren Sie, wie die Cloud Manager-Benutzeroberfläche organisiert ist und wie Sie zur Verwaltung Ihrer Programme und Umgebungen navigieren.

Die Benutzeroberfläche für die Cloud-Verwaltung besteht in erster Linie aus zwei grafischen Schnittstellen:

* [Die Konsole &quot;Meine Programme&quot;](#my-programs) wo Sie alle Ihre Programme anzeigen und verwalten können.
* [Das Fenster Programmübersicht](#program-overview) wo Sie die Details eines einzelnen Programms sehen und verwalten können.

## Meine Programmkonsole {#my-programs}

Wenn Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation aus. Sie gelangen zum **Eigene Programme** Konsole.

![Meine Programmkonsole](assets/my-programs-console.png)

Die Konsole My Programs bietet eine Übersicht über alle Programme, auf die Sie in der ausgewählten Organisation Zugriff haben. Er besteht aus mehreren Teilen.

1. [Symbolleisten](#toolbars-my-programs-toolbars) für die Organisationsauswahl, Warnhinweise und Kontoeinstellungen
1. [Statistiken und Aktionsaufrufe](#statistics) für einen Überblick über Ihre aktuelle Aktivität
1. [Programme und Lizenzen](#programs-license) um Ihren aktuellen Lizenzstatus zu verstehen und Ihre Programme zu verwalten
1. [Schnelllinks](#quick-links) einfachen Zugriff auf zugehörige Ressourcen

>[!TIP]
>
>Lesen Sie das Dokument . [Programme und Programmtypen](/help/getting-started/program-setup.md) Einzelheiten zu den Programmen.

### Symbolleisten {#my-programs-toolbars}

Es sind zwei Symbolleisten übereinander.

#### Cloud Manager-Kopfzeile {#cloud-manager-header}

Die erste ist die Kopfzeile von Cloud Manager, die beim Navigieren in Cloud Manager persistent ist. Es ist ein Anker, der Ihnen Zugriff auf Einstellungen und Informationen bietet, die für alle Cloud Manager-Programme gelten.

![Die Kopfzeile von Experience Cloud](assets/experience-cloud-header.png)

1. Über die Schaltfläche &quot;Cloud Manager&quot;gelangen Sie zurück zur Konsole &quot;Meine Programme&quot;von Cloud Manager, unabhängig davon, wo Sie sich in Cloud Manager befinden.
1. Tippen oder klicken Sie auf die Schaltfläche Feedback , um Adobe Feedback zu Cloud Manager zu geben.
1. Der Organisationsselektor zeigt die Organisation an, bei der Sie sich derzeit angemeldet haben (in diesem Beispiel &quot;Foundation Intern&quot;). Tippen oder klicken Sie, um zu einer anderen Organisation zu wechseln, wenn Ihre Adobe ID mit mehreren Organisationen verknüpft ist.
1. Durch Tippen oder Klicken auf den Lösungsumschalter können Sie schnell zu anderen Experience Cloud-Lösungen wechseln.
1. Das Hilfesymbol bietet schnellen Zugriff auf Lern- und Support-Ressourcen.
1. Das Benachrichtigungssymbol wird mit der Anzahl der aktuell zugewiesenen unvollständigen [Benachrichtigungen.](/help/using/notifications.md)
1. Wählen Sie das Symbol für Ihre Benutzerin bzw. Ihren Benutzer aus, um auf Ihre Benutzereinstellungen zuzugreifen. Wenn Sie kein Benutzerbild konfiguriert haben, wird ein zufälliges Symbol zugewiesen.

#### Programmleiste {#program-toolbar}

Die Programmsymbolleiste enthält Links zum Wechseln zwischen Cloud Manager-Programmen und -Aktionen, die dem Kontext entsprechen.

![Programm-Symbolleiste](assets/program-toolbar.png)

1. Die Programmauswahl wird in einer Dropdown-Liste geöffnet, in der Sie schnell andere Programme auswählen oder kontextbezogene Aktionen ausführen können, z. B. ein neues Programm erstellen
1. Über den Link Erste Schritte gelangen Sie zu den [Journey der Onboarding-Dokumentation](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/overview) , um Sie mit Cloud Manager vertraut zu machen.
   * Beachten Sie, dass die Onboarding-Journey für AEM as a Cloud Service und nicht für AMS-Cloud Service konzipiert ist. Viele Konzepte sind jedoch gleich.
1. Die Aktionsschaltfläche bietet kontextbezogene Aktionen, z. B. die Erstellung eines neuen Programms.

### Statistiken {#statistics}

Der Abschnitt Statistiken enthält aggregierte Daten für Ihre Organisation. Wenn Sie beispielsweise Ihre Programme erfolgreich eingerichtet haben, können Statistiken über Ihre Aktivitäten aus den letzten 90 Tagen angezeigt werden, darunter:

* Anzahl der [Bereitstellungen](/help/using/code-deployment.md)
* Anzahl der identifizierten [Code-Qualitätsprobleme](/help/using/code-quality-testing.md)
* Anzahl der Builds

Oder wenn Sie gerade mit der Einrichtung Ihrer Organisation beginnen, gibt es Tipps zu den nächsten Schritten oder Dokumentationsressourcen.

### Programme und Lizenz {#programs-license}

Der Hauptinhalt der Konsole My Programs ist die Liste der Programme und der Status Ihrer Lizenz.

#### Registerkarte „Programme“ {#programs}

Auf der Registerkarte **Programme** finden Sie Karten für jedes Programm, auf das Sie Zugriff haben. Tippen oder klicken Sie auf eine Karte, um die Seite **Programmübersicht** des Programms aufzurufen, auf der Sie Details zum Programm finden.

Verwenden Sie die Sortieroptionen, um das benötigte Programm leichter zu finden.

![Sortieroptionen](assets/my-programs-sorting.png)

* Sortieren nach
   * Erstellungsdatum (Standard)
   * Programmname
   * Status
* Aufsteigend (Standard)/Absteigend
* Rasteransicht (Standard)
* Listenansicht

Jedes Programm wird durch eine Karte (oder eine Zeile in einer Tabelle) dargestellt, die einen Überblick über das Programm und schnelle Links bietet, um Maßnahmen zu ergreifen.

![Programmkarte](assets/program-card.png)

* Programmbild (falls konfiguriert)
* Programmname
* Diensttyp: **Experience Manager Cloud** für [AEM as a Cloud Service Programme](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/home) oder **Experience Manager** für AMS-Programme
* Status
* Konfigurierte Lösungen
* Erstellungsdatum

Über das Informationssymbol erhalten Sie auch schnellen Zugriff auf zusätzliche Informationen zum Programm (nützlich in der Listenansicht).

![Informationen](assets/information-view.png)

Über das Symbol mit Auslassungspunkten gelangen Sie zu weiteren Aktionen, die Sie im Programm ausführen können.

![Schaltfläche &quot;Ellipse&quot;für Programme](assets/program-ellipsis.png)

* Navigieren zu einer bestimmten [Umgebung](/help/using/managing-environments.md) des Programms
* Öffnen Sie die [Programmübersicht](#program-overview)
* [Programm bearbeiten](/help/getting-started/program-setup.md)
* Überwachung anzeigen

#### Registerkarte „Lizenz“ {#license-tab}

Die **Lizenz** bietet Ihnen schnellen Zugriff auf das Lizenz-Dashboard.

### Direkt-Links {#quick-links}

Über den Schnelllink-Abschnitt erhalten Sie Zugriff auf häufig verwendete, zugehörige Ressourcen.

## Programmübersicht {#program-overview}

Nachdem Sie ein Programm in der Konsole Meine Programme ausgewählt haben, gelangen Sie zur Programmübersicht.

![Programmübersicht](assets/program-overview.png)

Die Programmübersicht bietet Zugriff auf alle Details eines Cloud Manager-Programms. Wie die Konsole My Programs besteht sie aus mehreren Teilen.

1. [Symbolleisten](#program-overview-toolbar) um schnell zur Konsole &quot;Meine Programme&quot;zurückzukehren und durch das Programm zu navigieren.
1. [Registerkarten](#program-tabs) Umstellung zwischen verschiedenen Programmaspekten
1. A [Aktionsaufruf](#cta) auf der Grundlage der letzten Aktionen des Programms
1. Ein [Übersicht über die Umgebungen](#environments) des Programms
1. Ein [Pipelines - Übersicht](#pipelines) des Programms
1. Links zu [nützliche Ressourcen](#useful-resources)

### Symbolleisten {#program-overview-toolbar}

Die Symbolleisten für die Programmübersicht ähneln denen der [Meine Programmkonsole.](#my-programs-toolbars) Hier werden nur die Unterschiede veranschaulicht.

#### Cloud Manager-Kopfzeile {#cloud-manager-header-2}

Die Kopfzeile von Cloud Manager verfügt über ein Hamburger-Menü, das automatisch geöffnet wird, um die navigierbaren Registerkarten der Programmübersicht anzuzeigen.

![Cloud Manager-Hamburger-Menü](assets/cloud-manager-hamburger.png)

Tippen oder klicken Sie auf das Hamburger-Menüsymbol, um die Registerkarten auszublenden.

#### Programmleiste {#program-toolbar-2}

Die Programmsymbolleiste bietet Ihnen weiterhin Zugriff auf einen schnellen Wechsel zu anderen Programmen, bietet aber zusätzlich Zugriff auf kontextbezogene Aktionen wie das Hinzufügen und Bearbeiten des Programms.

![Programm-Symbolleiste](assets/cloud-manager-program-toolbar.png)

Darüber hinaus bietet die Symbolleiste immer die Registerkarte, auf der Sie sich befinden, wenn Sie die Registerkarten über das Hamburger Menü ausgeblendet haben.

### Programmregisterkarten {#program-tabs}

Jedem Programm sind viele Optionen und Daten zugeordnet. Diese Daten werden in Tabs zusammengefasst, um die Navigation im Programm zu vereinfachen. Die Tabs bieten Zugriff auf:

* Übersicht - Die im aktuellen Dokument beschriebene Programmübersicht
* [Aktivität](/help/using/managing-pipelines.md#activity) - Verlauf der Pipeline-Ausführungen des Programms
* [Pipelines](/help/using/managing-pipelines.md#pipelines) - Alle für das Programm konfigurierten Pipelines
* [Repositorys](/help/managing-code/repositories.md) - Alle für das Programm konfigurierten Repositorys
* [Berichte](/help/using/monitoring-environments.md#system-monitoring-overview) - Metriken wie SLA-Daten
* [Umgebungen](/help/using/managing-environments.md) - Alle für das Programm konfigurierten Umgebungen
* [Content Sets](/help/using/content-copy.md) - Zu Kopierzwecken erstellte Inhaltssätze
* [Aktivität &quot;Inhalt kopieren&quot;](/help/using/content-copy.md) - Aktivitäten zur Inhaltskopie
* Lernpfade - Zusätzliche Lernressourcen zu Cloud Manager

Wenn Sie ein Programm öffnen, gelangen Sie standardmäßig zum **Übersicht** Registerkarte. Die aktuelle Registerkarte ist hervorgehoben. Wählen Sie eine andere Registerkarte aus, um deren Details anzuzeigen.

Verwenden Sie das Hamburger-Menü im [Cloud Manager-Kopfzeile](#cloud-manager-header-2) um die Registerkarten auszublenden.

### Aktionsaufruf {#cta}

Im Bereich Aktionsaufruf erhalten Sie je nach Status Ihres Programms hilfreiche Informationen. Für ein neues Programm werden Ihnen möglicherweise die nächsten Schritte angeboten sowie eine Erinnerung an das Startdatum, [das bei der Programmerstellung festgelegt wurde.](/help/getting-started/program-setup.md)

Bei einem Live-Programm den Status Ihrer letzten Bereitstellung mit Links zu Details und zum Beginn einer neuen Bereitstellung.

![Aktionsaufruf](assets/info-banner.png)

### Umgebungskarte {#environments}

Die **Umgebungen** bietet Ihnen einen Überblick über Ihre Umgebungen sowie Links für Schnellaktionen.

Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicks **Alle anzeigen** um alle Umgebungen des Programms anzuzeigen.

Lesen Sie das Dokument . [Umgebungen verwalten](/help/using/managing-environments.md) für Details zur Verwaltung Ihrer Umgebungen.

### Pipelines Card {#pipelines}

Die **Pipelines** bietet Ihnen einen Überblick über Ihre Pipelines sowie Links für Schnellaktionen.

Die **Pipelines** Karte listet nur drei Pipelines auf. Klicks **Alle anzeigen** um alle Pipelines des Programms zu sehen.

Lesen Sie das Dokument . [Verwalten von Pipelines](/help/using/managing-pipelines.md) für Details zur Verwaltung Ihrer Pipelines.

### Nützliche Ressourcen {#useful-resources}

Die **Nützliche Ressourcen** enthält Links zu zusätzlichen Lernressourcen für Cloud Manager.
