---
title: Überwachen von Umgebungen
description: Informationen zum Überwachen von Umgebungen in Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 5907ca6337d33c26ff19a14bfeb358cd9f7b935d
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 52%

---


# Überwachen von Umgebungen {#monitoring-environments}

Informationen zum Überwachen von Umgebungen in Cloud Manager.

## Metrikschwellen {#thresholds}

Die Systemüberwachung in [!UICONTROL Cloud Manager] erfolgt durch Beobachtung der einzelnen Instanzen innerhalb einer Umgebung und Verfolgung verschiedener Metriken für jede Instanz. Jede Metrik hat zwei definierte Schwellenwerte: eine Warnschwelle und eine kritische Schwelle.

Wenn eine Metrik ihren kritischen Schwellenwert überschreitet, wird sie als kritisch betrachtet. Wenn eine Metrik über ihrem Warnschwellenwert liegt (aber unter ihrem kritischen Schwellenwert), wird sie als Warnstatus betrachtet. Die Schwellenwerte werden von Adobe Managed Services festgelegt und können in [!UICONTROL Cloud Manager] visualisiert werden. In den meisten Fällen sind die Schwellenwerte zwischen Kunden konsistent. Es gibt jedoch Fälle, in denen Adobe Managed Services Schwellenwerte für bestimmte Kundenanforderungen anpasst. Fragen zu Schwellenwerten richten Sie bitte an Ihren Customer Success Engineer (CSE).

## Zugriff auf die Systemüberwachung {#accessing-system-monitoring}

Führen Sie diese Schritte aus, um auf die Systemüberwachung zuzugreifen.

1. Melden Sie sich auf der Landingpage **Managed Services – Programme** an.

   ![Managed Services-Programme](/help/assets/ProgramLanding.png)

1. Klicken Sie auf das vierte Symbol auf der Programmkarte.

   ![Einstellungen](/help/assets/first-timea1.png)


Alternativ können Sie zur **Systemüberwachung** Landingpage durch **Berichte** globales Navigationsmenüelement innerhalb von [!UICONTROL Cloud Manager].

## Systemüberwachung - Übersicht {#system-monitoring-overview}

Auf der Übersichtsseite Systemüberwachung werden die überwachten Umgebungen im Programm aufgelistet und Berichte zu deren allgemeinen Zustand in vier verschiedenen Kategorien erstellt:

* Host
* Speicherung
* Netzwerk
* Anwendung

Der Status in jeder Kategorie ist eine Zusammenfassung einzelner Metriken. Wenn eine Metrik in einer Kategorie den kritischen Status aufweist, befindet sich die gesamte Kategorie in einem kritischen Zustand für die Zwecke der Übersichtsseite. Dieselbe Zusammenfassung kann auf Umgebungs- und Instanzebene angezeigt werden.

![Systemüberwachung - Übersicht](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Standardmäßig sind beim Navigieren zu dieser Seite die Instanzen der Produktionsumgebung sichtbar, aber auch andere Umgebungen können angezeigt werden.

## Details zur Systemüberwachung {#system-monitoring-detail}

Zum Anzeigen von Details bestimmter Metriken können Sie entweder auf eine der Kategorien im linken Navigationsbereich oder auf eine der Kategorieindikatoren einer bestimmten Instanz klicken. Jede Detailseite präsentiert eine Reihe von Diagrammen für die Metriken in dieser Kategorie. Sie können die Metriken entweder für alle Instanzen in einer Umgebung oder für eine bestimmte Instanz anzeigen. Mithilfe der Dropdownfelder oben rechts können Sie zwischen der Umgebung und den Instanzen wechseln.

![Umgebung auswählen](/help/assets/System_Monitoring1.png)

Im Navigationsbereich auf der linken Seite finden Sie die verfügbaren Metriken innerhalb der aktuell ausgewählten Kategorie, für die Daten für die aktuell ausgewählte Umgebung und die Instanzen vorhanden sind.

![Überwachungsmetriken](/help/assets/System_Monitoring2.png)

In einem einzelnen Diagramm werden der Status und ein Graph der Daten zusammen mit den Schwellenwerten angezeigt. Wenn mehrere Instanzen angezeigt werden, befinden sich die Daten jeder Instanz in einer separaten Reihe.

![Metrikdiagramm](/help/assets/Monitoring_Graphs1.png)

Einzelne Reihen können in einem Diagramm ausgeblendet werden, indem Sie auf die Reihe in der Legende klicken.
Wenn Sie beispielsweise auf die Warnschwellenwert-Reihe klicken, wird nur der kritische Schwellenwert angezeigt.

![Diagramm ändern](/help/assets/Monitoring_Graphs2.png)

### Metrikdefinitionen {#metric-definitions}

#### Host {#host}

* **Pro Kern laden**: Die Anzahl der Prozesse, die von der CPU ausgeführt werden oder sich in einem Wartezustand befinden, gemittelt über einen Zeitraum von einer (load1), fünf (load5) und fünfzehn (load15) Minuten
* **Prozessanzahl**: Die Anzahl der derzeit geöffneten Prozesse
* **Benutzeranzahl**: Die Anzahl der Benutzer mit einer aktiven Shell-Sitzung
* **Speichernutzung**: Der derzeit zugewiesene Prozentsatz des Systemspeichers
* **JVM-Speicher**: Die Größe (in Megabyte) des zugewiesenen Java-Heap
* **Alte Generation**: Der Prozentsatz des JVM-Speicherplatzes der alten Generation, der derzeit zugewiesen ist

#### Netzwerk {#network}

* **CQ-Port-Prüfung**: Die Antwortzeit in Sekunden, um auf den AEM- oder Dispatcher-Port zuzugreifen
   * Es gibt verschiedene Metriken für Autor, Veröffentlichung und Dispatcher.

#### Speicherung {#storage}

* **Festplattenspeicher**: Der für jeden Bereitstellungspunkt auf dem Host verwendete Speicherplatz (in Megabyte)
   * Für jeden Bereitstellungspunkt gibt es verschiedene Metriken.
   * Es gibt mindestens Metriken für `/` und `/mnt`, aber je nach der spezifischen Instanzkonfiguration können zusätzliche Bereitstellungspunkt-Metriken verfügbar sein.
* **Ordnergröße**
* **AEM Segmentspeicher**: Der für den AEM Segmentspeicher verwendete Speicherplatz (in Gigabyte).

#### Anwendung {#application}

* **Replikationsagent**: Die Zeit (in Sekunden) für ein Testreplikationsereignis
   * Für jeden Replizierungsagenten gibt es verschiedene Metriken.
* **Dispatcher Flush**: Die Anzahl der Elemente, die sich derzeit in der Dispatcher-Flush-Warteschlange befinden

## SLA-Berichte {#sla-reporting}

Kunden können die Leistung ihrer Produktions-AEM im Verhältnis zu ihrem vertraglich vereinbarten Service Level Agreement (SLA) sehen. Dies ist über ein Untermenü auf der **Berichte** angezeigt.

Das folgende Diagramm zeigt die monatliche SLA-Leistung für 2018.

![SLA-Diagramm 2018](/help/assets/SLA-Reports-one.png)

Wie bei den Systemüberwachungsdiagrammen werden beim Bewegen der Maus über einen Datenpunkt die spezifischen Werte für diesen Monat angezeigt.

![Datenpunkt-Rollover](/help/assets/SLA-Reports-two.png)

Die **Ereignisanalyse** in diesem Diagramm die Anzahl der Vorfälle, die während des aktuell ausgewählten Jahres für das Programm aufgetreten sind. Für jeden Vorfall werden Zeitraum und Ursache mitsamt Kommentaren angegeben.

![Ereignisanalyse](/help/assets/sla-reporting3.png)

## SLA-Metriken {#sla-metrics}

* **Autor-Vertrag**: Dies ist der SLA, der in Ihrem Vertrag mit Adobe Managed Services für die Autorenstufe definiert ist.
* **AMS-Autor-SLA**: Dies ist die gemessene Produktionszeit im Hinblick auf Factoring-Vorfälle in der Produktions-Autorenstufe, die von Adobe oder unseren Anbietern verursacht wurden.
* **Autor-SLA**: Dies ist die gemessene Produktionszeit der Autorenstufe ohne Berücksichtigung geplanter Ausfallzeiten wie z. B. Wartungsfenster.
* **Endbenutzervertrag**: Dies ist der SLA, der in Ihrem Vertrag mit Adobe Managed Services für die Veröffentlichungsstufe definiert ist.
* **AMS-Endbenutzer-SLA**: Dies ist die gemessene Produktionszeit im Hinblick auf Factoring-Vorfälle in der Produktionsveröffentlichungsstufe, die von Adobe oder unseren Anbietern verursacht wurden.
* **Endbenutzer-SLA**: Dies ist die gemessene Produktionszeit der Veröffentlichungsstufe ohne Berücksichtigung geplanter Ausfallzeiten wie z. B. Wartungsfenster.

## Video-Tutorial {#video-tutorial}

In diesem Video erhalten Sie einen Überblick über die Verwendung der von Cloud Manager-Berichten erstellten Diagramme, in denen Sie sich einen Überblick über Ihre Programmumgebungen verschaffen können.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
