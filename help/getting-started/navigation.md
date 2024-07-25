---
title: Navigation durch die Cloud Manager-Benutzeroberfläche
description: Erfahren Sie, wie die Benutzeroberfläche von Cloud Manager aufgebaut ist und wie Sie Ihre Programme und Umgebungen verwalten.
exl-id: 9c1545ce-1c6d-417f-a6f4-fe53caef3433
source-git-commit: d4d9a9f38c5a969f276140dca98731c670547a3d
workflow-type: tm+mt
source-wordcount: '1439'
ht-degree: 80%

---


# Navigation durch die Cloud Manager-Benutzeroberfläche {#navigation}

Erfahren Sie, wie die Benutzeroberfläche von Cloud Manager aufgebaut ist und wie Sie Ihre Programme und Umgebungen verwalten.

Die Benutzeroberfläche für die Cloud-Verwaltung besteht in erster Linie aus zwei grafischen Schnittstellen:

* [Die Konsole „Meine Programme“](#my-programs-console), in der Sie alle Ihre Programme anzeigen und verwalten können.
* [Das Fenster „Programmübersicht“](#program-overview), in dem Sie die Details eines einzelnen Programms sehen und verwalten können.

## Konsole „Meine Programme“ {#my-programs-console}

Wenn Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) anmelden und die entsprechende Organisation auswählen, gelangen Sie in die Konsole **Meine Programme**.

![Konsole „Meine Programme“](assets/my-programs-console.png)

Die Konsole „Meine Programme“ bietet einen Überblick über alle Programme, auf die Sie in der ausgewählten Organisation Zugriff haben. Sie besteht aus mehreren Teilen.

1. [Symbolleisten](#toolbars-my-programs-toolbars) für die Auswahl von Organisationen, Warnmeldungen und Kontoeinstellungen
1. Registerkarten, mit denen Sie die aktuelle Ansicht Ihrer Programme umschalten können.
   * Ansicht **Home** (Standard), die die Ansicht **My Programs** mit einer Übersicht aller Programme auswählt
   * **Lizenz**, die auf das Lizenz-Dashboard zugreift. Das Lizenz-Dashboard gilt nur für AEM as a Cloud Service-Programme, nicht für AMS-Programme.
      * Informationen zum Bestimmen des Diensttyps Ihres Programms (AMS oder AEMaaCS) finden Sie im Abschnitt [Programmkarten](#program-cards) dieses Dokuments.
   * Beachten Sie, dass die Registerkarten standardmäßig geschlossen sind und über das Hamburger-Menü in der Kopfzeile [Cloud Manager](#cloud-manager-header) angezeigt werden können.
1. [Aktionsaufrufe und Statistiken](#cta-statistics) für einen Überblick über Ihre jüngste Aktivität
1. [**Meine Programme** Abschnitt](#my-programs-section) mit einer Übersicht über alle Ihre Programme
1. [Schnell-Links](#quick-links) für den einfachen Zugriff auf verwandte Ressourcen

>[!TIP]
>
>Einzelheiten zu den Programmen sind dem Dokument [Programme und Programmarten](/help/getting-started/program-setup.md) zu entnehmen.

### Symbolleisten {#my-programs-toolbars}

Es gibt zwei Symbolleisten übereinander.

#### Cloud Manager-Header {#cloud-manager-header}

Die erste ist der Header von Cloud Manager, der bestehen bleibt, wenn Sie in Cloud Manager navigieren. Er ist ein Anker, der Ihnen Zugriff auf Einstellungen und Informationen bietet, die für alle Cloud Manager-Programme gelten.

![Die Kopfzeile von Experience Cloud](assets/experience-cloud-header.png)

1. Das Hamburger-Menü, über das Sie auf Registerkarten zugreifen können, die Sie zu bestimmten Teilen eines Programms in einem einzelnen Programm führen oder je nach Kontext zwischen dem Lizenz-Dashboard und der Konsole **[Meine Programme](#my-programs-console)** wechseln können.
   * Das Lizenz-Dashboard gilt nur für AEM as a Cloud Service-Programme, nicht für AMS-Programme.
   * Informationen zum Bestimmen des Diensttyps Ihres Programms (AMS oder AEMaaCS) finden Sie im Abschnitt [Programmkarten](#program-cards) dieses Dokuments.
1. Über die Schaltfläche „Cloud Manager“ gelangen Sie zurück zur Konsole „Meine Programme“ von Cloud Manager, unabhängig davon, wo Sie sich in Cloud Manager befinden.
1. Tippen oder klicken Sie auf die Schaltfläche „Feedback“, um Adobe Feedback zu Cloud Manager zu geben.
1. Der Organisationsselektor zeigt die Organisation an, bei der Sie sich derzeit angemeldet haben (in diesem Beispiel „Foundation Intern“). Tippen oder klicken Sie, um zu einer anderen Organisation zu wechseln, wenn Ihre Adobe ID mit mehreren Organisationen verknüpft ist.
1. Durch Tippen oder Klicken auf den Lösungsumschalter können Sie schnell zu anderen Experience Cloud-Lösungen wechseln.
1. Das Hilfesymbol bietet schnellen Zugriff auf Lern- und Support-Ressourcen.
1. Dieses Benachrichtigungssymbol wird mit der Anzahl der aktuell zugewiesenen unvollständigen [Benachrichtigungen](/help/using/notifications.md) gekennzeichnet.
1. Wählen Sie das Symbol für Ihre Benutzerin bzw. Ihren Benutzer aus, um auf Ihre Benutzereinstellungen zuzugreifen. Wenn Sie kein Benutzerbild konfiguriert haben, wird ein zufälliges Symbol zugewiesen.

#### Programmsymbolleiste {#program-toolbar}

Die Programmsymbolleiste enthält Links zum Wechseln zwischen Cloud Manager-Programmen und -Aktionen, die dem Kontext entsprechen.

![Programmsymbolleiste](assets/program-toolbar.png)

1. Die Programmauswahl wird in einer Dropdown-Liste geöffnet, in der Sie schnell andere Programme auswählen oder kontextbezogene Aktionen ausführen können, z. B. die Erstellung eines neuen Programms.
1. Über den Link „Erste Schritte“ erhalten Sie Zugriff auf die [Journey zur Onboarding-Dokumentation](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/onboarding/journey/overview), die Ihnen den Einstieg in Cloud Manager erleichtert.
   * Beachten Sie, dass die Onboarding-Journey für AEM as a Cloud Service und nicht für AMS-Cloud Service konzipiert ist. Viele Konzepte sind jedoch gleich.
1. Die Aktionsschaltfläche bietet kontextbezogene Aktionen, z. B. die Erstellung eines neuen Programms.

### Aktionsaufrufe und Statistiken {#cta-statistics}

Der Abschnitt Aktionsaufruf und Statistiken enthält aggregierte Daten für Ihre Organisation. Wenn Sie beispielsweise Ihre Programme erfolgreich eingerichtet haben, können Statistiken über Ihre Aktivitäten aus den letzten 90 Tagen angezeigt werden, darunter:

* Anzahl der [Bereitstellungen](/help/using/code-deployment.md)
* Anzahl der identifizierten [Code-Qualitätsprobleme](/help/using/code-quality-testing.md)
* Anzahl der Builds

Oder wenn Sie gerade mit der Einrichtung Ihrer Organisation beginnen, gibt es Tipps zu den nächsten Schritten oder Dokumentationsressourcen.

### Eigene Programmbereiche {#my-programs-section}

Der Hauptinhalt der Konsole &quot;Meine Programme&quot;ist der Abschnitt &quot;**Meine Programme**&quot;, in dem Ihre Programme als einzelne Karten aufgelistet werden. Tippen oder klicken Sie auf eine Karte, um die Seite **Programmübersicht** des Programms aufzurufen, auf der Sie Details zum Programm finden.

>[!NOTE]
>
>Je nach Ihren Berechtigungen können Sie bestimmte Programme möglicherweise nicht auswählen.

Verwenden Sie die Sortieroptionen, um das benötigte Programm leichter zu finden.

![Sortieroptionen](assets/my-programs-sorting.png)

* Sortieren nach
   * Erstellungsdatum (Standard)
   * Programmname
   * Status
* Aufsteigend (Standard)/Absteigend
* Rasteransicht (Standard)
* Listenansicht

#### Programmkarten {#program-cards}

Jedes Programm wird durch eine Karte (oder eine Zeile in einer Tabelle) dargestellt, die einen Überblick über das Programm und Schnell-Links bietet, um Maßnahmen zu ergreifen.

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

Über das Symbol mit Auslassungspunkten gelangen Sie zu weiteren Aktionen, die Sie im Programm ausführen können.

![Schaltfläche mit Auslassungspunkten für Programme](assets/program-ellipsis.png)

* Navigieren zu einer bestimmten [Umgebung](/help/using/managing-environments.md) des Programms
* Öffnen der [Programmübersicht](#program-overview)
* [Bearbeiten des Programms](/help/getting-started/program-setup.md)
* Anzeigen der Überwachung

### Schnell-Links {#quick-links}

Über den Abschnitt „Schnell-Links“ erhalten Sie Zugriff auf häufig verwendete, zugehörige Ressourcen.

## Fenster „Programmübersicht“ {#program-overview}

Nachdem Sie ein Programm in der Konsole [**Meine Programme**,](#my-programs-console) ausgewählt haben, gelangen Sie zur Programmübersicht.

![Programmübersicht](assets/program-overview.png)

Die Programmübersicht bietet Zugriff auf alle Details eines Cloud Manager-Programms. Wie die Konsole „Meine Programme“ besteht sie aus mehreren Teilen.

1. [Symbolleisten](#program-overview-toolbar), um schnell zur Konsole „Meine Programme“ zurückzukehren und durch das Programm zu navigieren.
1. [Registerkarten](#program-tabs), um zwischen den verschiedenen Aspekten des Programms zu wechseln
1. Ein [Aktionsaufruf](#cta) basierend auf den letzten Aktionen des Programms
1. Eine [Übersicht über die Umgebungen](#environments) des Programms
1. Eine [Übersicht über die Pipelines](#pipelines) des Programms
1. Links zu [nützlichen Ressourcen](#useful-resources)

### Symbolleisten {#program-overview-toolbar}

Die Symbolleisten für die Programmübersicht sind denen der Konsole [Meine Programme](#my-programs-toolbars) sehr ähnlich. Hier werden nur die Unterschiede veranschaulicht.

#### Cloud Manager-Header {#cloud-manager-header-2}

Der Header von Cloud Manager verfügt über ein Hamburger-Menü, das automatisch geöffnet wird, um die navigierbaren Registerkarten der Programmübersicht anzuzeigen.

![Cloud Manager-Hamburger-Menü](assets/cloud-manager-hamburger.png)

Tippen oder klicken Sie auf das Hamburger-Menüsymbol, um die Registerkarten auszublenden.

#### Programmsymbolleiste {#program-toolbar-2}

Die Programmsymbolleiste ermöglicht weiterhin den schnellen Wechsel zu anderen Programmen, bietet aber auch Zugriff auf kontextbezogene Aktionen wie das Hinzufügen und Bearbeiten des Programms.

![Programmsymbolleiste](assets/cloud-manager-program-toolbar.png)

Außerdem zeigt die Symbolleiste jederzeit an, auf welcher Registerkarte Sie sich befinden, wenn Sie die Registerkarten über das Hamburger-Menü ausgeblendet haben.

### Programmregisterkarten {#program-tabs}

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

Verwenden Sie das Hamburger-Menü im [Cloud Manager-Header](#cloud-manager-header-2), um die Registerkarten auszublenden.

### Aktionsaufruf {#cta}

Der Aktionsaufrufs-Abschnitt gibt Ihnen je nach Status Ihres Programms hilfreiche Informationen. Für ein neues Programm werden Ihnen möglicherweise die nächsten Schritte angeboten sowie eine Erinnerung an das Startdatum, [das bei der Programmerstellung festgelegt wurde.](/help/getting-started/program-setup.md)

Bei einem Live-Programm den Status Ihrer letzten Bereitstellung mit Links zu Details und zum Beginn einer neuen Bereitstellung.

![Aktionsaufruf](assets/info-banner.png)

### Umgebungskarte {#environments}

Die Karte **Umgebungen** gibt Ihnen einen Überblick über Ihre Umgebungen sowie Links für Schnellaktionen.

Die Karte **Umgebungen** listet nur drei Umgebungen auf. Klicken Sie auf **Alle anzeigen**, um alle Umgebungen des Programms zu sehen.

Bitte lesen Sie das Dokument [Verwaltung von Umgebungen](/help/using/managing-environments.md), um zu erfahren, wie Sie Ihre Umgebungen verwalten können.

### Pipelines-Karte {#pipelines}

Die Karte **Pipelines** gibt Ihnen einen Überblick über Ihre Pipelines sowie Links für Schnellaktionen.

Auf der Karte **Pipelines** sind nur drei Pipelines aufgeführt. Klicken Sie auf **Alle anzeigen**, um alle Pipelines des Programms zu sehen.

Bitte lesen Sie das Dokument [Verwaltung von Pipelines](/help/using/managing-pipelines.md), um zu erfahren, wie Sie Ihre Pipelines verwalten können.

### Nützliche Ressourcen {#useful-resources}

Der Abschnitt **Nützliche Ressourcen** enthält Links zu weiteren Lernressourcen für Cloud Manager.
