---
title: Überwachen von Umgebungen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre Umgebungen überwachen.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 74%

---


# Überwachen von Umgebungen {#monitoring-environments}

Erfahren Sie, wie Sie mit Cloud Manager Ihre Umgebungen überwachen.

## Schwellenwerte für Metriken {#thresholds}

Die Systemüberwachung in [!UICONTROL Cloud Manager] erfolgt durch Beobachtung der einzelnen Instanzen innerhalb einer Umgebung und Verfolgung verschiedener Metriken für jede Instanz. Jede Metrik hat zwei definierte Schwellenwerte: einen *Warnschwellenwert* und einen *kritischen Schwellenwert*.

Wenn eine Metrik über ihrem Warnschwellenwert liegt (aber unter ihrem kritischen Schwellenwert), gilt für sie ein Warnstatus.

Wenn eine Metrik ihren kritischen Schwellenwert überschreitet, wird sie als kritisch betrachtet.

Adobe Managed Services legt die Schwellenwerte fest, die Sie über [!UICONTROL Cloud Manager] anzeigen können. In den meisten Fällen sind die Schwellenwerte zwischen Kundinnen und Kunden konsistent. Es gibt jedoch Fälle, in denen Adobe Managed Services Schwellenwerte für bestimmte Kundenanforderungen bearbeitet. Wenden Sie sich bei allen Fragen zu den Schwellenwerten an Ihr Customer Success Engineer(CSE)-Team.

## Zugreifen auf die Systemüberwachung {#accessing-system-monitoring}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Auslassungspunkte des Programms, das Sie überwachen möchten.
1. Klicken Sie im Menü unter **Verwalten** auf **Überwachung anzeigen**, um die Seite **Berichte** mit Informationen zur Systemüberwachung zu öffnen.

   ![Einstellungen](/help/assets/first-timea1.png)

.

## Überblick über die Systemüberwachung {#system-monitoring-overview}

Im Abschnitt **Systemüberwachung** der Seite **Berichte** werden die überwachten Umgebungen im Programm aufgelistet. Dort finden Sie Angaben zum allgemeinen Zustand in den vier folgenden Kategorien:

* Host
* Speicher
* Netzwerk
* Programm

Der Status in jeder Kategorie ist eine Zusammenfassung einzelner Metriken. Wenn eine Metrik in einer Kategorie einen kritischen Status aufweist, befindet sich auf der Übersichtsseite die gesamte Kategorie in einem kritischen Zustand. Dieselbe Zusammenfassung kann auf Umgebungs- und Instanzebene angezeigt werden.

![Systemüberwachung – Übersicht](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Beim Navigieren zu dieser Seite werden die Instanzen der Produktionsumgebung standardmäßig angezeigt, aber es können auch andere Umgebungen angezeigt werden.

## Details zur Systemüberwachung {#system-monitoring-detail}

Um die Details zu bestimmten Metriken anzuzeigen, klicken Sie auf eine der Kategoriespalten einer bestimmten Instanz oder auf den Kategorietitel im linken Navigationsbereich. Jede Detailseite präsentiert eine Reihe von Diagrammen für die Metriken in dieser Kategorie. Sie können die Metriken entweder für alle Instanzen in einer Umgebung oder für eine bestimmte Instanz anzeigen. Mithilfe der Dropdownfelder oben rechts können Sie zwischen der Umgebung und den Instanzen wechseln.

![Umgebung auswählen](/help/assets/System_Monitoring1.png)

Im Navigationsbereich auf der linken Seite finden Sie die verfügbaren Metriken innerhalb der aktuell ausgewählten Kategorie, für die Daten für die aktuelle Umgebungs- und Instanzenauswahl vorhanden sind.

In einem Diagramm werden der Status und ein Graph der Daten im Laufe der Zeit zusammen mit den Schwellenwerten angezeigt. Wenn mehrere Instanzen angezeigt werden, befinden sich die Daten jeder Instanz in einer separaten Reihe.

![Metrikdiagramm](/help/assets/Monitoring_Graphs1.png)

Einzelne Reihen können in einem Diagramm ausgeblendet werden, indem Sie auf die Reihe in der Legende klicken.
Wenn Sie beispielsweise auf die Warnschwellenwert-Reihe klicken, wird nur der kritische Schwellenwert angezeigt.

![Graph ändern](/help/assets/Monitoring_Graphs2.png)

### Metrikdefinitionen {#metric-definitions}

#### Host {#host}

* **`Load Per Core`**: Die Anzahl der Prozesse, die von der CPU ausgeführt werden. Oder die Anzahl der Prozesse in der Warteschlange, die sich in einem Wartezustand befinden, gemittelt über einen Zeitraum von einer Minute (load1), fünf Minuten (load5) und fünfzehn Minuten (load15).
* **P`rocess Count`**: Die Anzahl der derzeit geöffneten Prozesse.
* **`User Count`**: Die Anzahl der Benutzer mit einer aktiven Shell-Sitzung.
* **`Memory Usage`**: Der Prozentsatz des aktuell zugewiesenen Systemspeichers.
* **`JVM Memory`**: Die Größe (in Megabyte) des zugewiesenen Java Heap.
* **`Old Generation Space`**: Der Prozentsatz des aktuell zugewiesenen JVM-Arbeitsspeichers der alten Generation.

#### Netzwerk {#network}

* **`CQ Port Check`**: Die Reaktionszeit in Sekunden, um auf den AEM- oder Dispatcher-Port zuzugreifen. Es gibt verschiedene Metriken für „author“, „publish“ und „dispatcher“.

#### Speicher {#storage}

* **`Disk Space`**: Der für jeden einzelnen Bereitstellungspunkt auf dem Host belegte Speicherplatz (in Megabyte). Für jeden Bereitstellungspunkt gibt es verschiedene Metriken. Es werden zumindest Metriken für `/` und `/mnt` angezeigt. Abhängig von der jeweiligen Instanzkonfiguration können jedoch weitere Bereitstellungspunkt-Metriken verfügbar sein.
* **`Folder Size`**
* **`AEM Segment Store`**: Der für den AEM-Segmentspeicher belegte Speicherplatz (in Gigabyte).

#### Programm {#application}

* **`Replication Agent`**: Die Zeit (in Sekunden) für eine Testreplikation
   * Für jeden Replizierungsagenten gibt es verschiedene Metriken.
* **`Dispatcher Flush`**: Die Anzahl der sich derzeit in der Dispatcher-Leerungswarteschlange befindlichen Elemente

## SLA-Berichte {#sla-reporting}

Sie können die Leistung Ihrer AEM-Produktionsumgebung im Vergleich zu Ihrem vertraglich vereinbarten Service Level Agreement (SLA) sehen.

Das folgende Diagramm zeigt die monatliche SLA-Erreichung für 2019.

![SLA-Diagramm 2018](/help/assets/SLA-Reports-one.png)

Wie bei den Systemüberwachungsdiagrammen werden beim Bewegen der Maus über einen Datenpunkt die spezifischen Werte für diesen Monat angezeigt.

![Datenpunkt-Rollover](/help/assets/SLA-Reports-two.png)

Der Abschnitt **Ereignisanalyse** unter diesem Diagramm zeigt die Vorfälle, die im aktuell ausgewählten Jahr im Zusammenhang mit dem Programm aufgetreten sind. Für jeden Vorfall werden Zeitraum und Ursache mitsamt Kommentaren angegeben.

![Ereignisanalyse](/help/assets/sla-reporting3.png)

## SLA-Metriken {#sla-metrics}

* **`Author Contract`**: Die SLA, die in Ihrem Vertrag mit Adobe Managed Services für die Autorenebene definiert ist.
* **`AMS Author SLA`**: Gemessene Betriebszeit der Produktions-Autorenebene, Factoring-Vorfälle, die von Anbietern oder Adobe verursacht wurden.
* **`Author SLA`**: Die gemessene Betriebszeit in der Autorenebene, wobei geplante Ausfallzeiten wie Wartungsfenster ignoriert werden.
* **`End User Contract`**: Die SLA, die in Ihrem Vertrag mit Adobe Managed Services für die Veröffentlichungsebene definiert ist.
* **`AMS End User SLA`**: Gemessene Betriebszeiten in der Produktions-Publishing-Ebene, Factoring-Vorfälle, die von Anbietern oder Adobe verursacht wurden.
* **`End User SLA`**: Die gemessene Betriebszeit auf der Veröffentlichungsebene, wobei geplante Ausfallzeiten wie Wartungsfenster ignoriert werden.

## Video-Tutorial {#video-tutorial}

Dieses Video bietet einen Überblick über die Verwendung der von Cloud Manager Reports erstellten Diagramme, die einen Einblick in Ihre Programmumgebungen geben.

>[!VIDEO](https://video.tv.adobe.com/v/34567?captions=ger)
