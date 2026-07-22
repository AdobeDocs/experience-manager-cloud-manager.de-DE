---
title: Überwachen von Umgebungen
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre Umgebungen überwachen.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
TQID: https://experienceleague.adobe.com/1WlZ7i3267CTPVQrvLi9FlzJuTjzSzpghePEMlSygjY
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 59ab2b4824e516576d0905376b80c37edc49e53d
workflow-type: tm+mt
source-wordcount: 843
ht-degree: 57%

---

# Überwachen von Umgebungen {#monitoring-environments}

Erfahren Sie, wie Sie mit Cloud Manager Ihre Umgebungen überwachen.

## Schwellenwerte für Metriken {#thresholds}

Die Systemüberwachung in [!UICONTROL Cloud Manager] erfolgt durch Beobachtung der einzelnen Instanzen innerhalb einer Umgebung und Verfolgung verschiedener Metriken für jede Instanz. Jede Metrik hat zwei definierte Schwellenwerte: einen *Warnschwellenwert* und einen *kritischen Schwellenwert*.

Wenn eine Metrik über ihrem Warnschwellenwert liegt (aber unter ihrem kritischen Schwellenwert), gilt für sie ein Warnstatus.

Wenn eine Metrik ihren kritischen Schwellenwert überschreitet, wird sie als kritisch betrachtet.

Adobe Managed Services legt die Schwellenwerte fest, die Sie über [!UICONTROL Cloud Manager] anzeigen können. Normalerweise sind die Schwellenwerte für die verschiedenen Kunden gleich, aber es gibt Fälle, in denen Adobe Managed Services die Schwellenwerte entsprechend den spezifischen Kundenanforderungen bearbeitet. Wenden Sie sich bei allen Fragen zu den Schwellenwerten an Ihr Customer Success Engineer(CSE)-Team.

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

Der Status in jeder Kategorie ist eine Zusammenfassung einzelner Metriken. Wenn eine Metrik in einer Kategorie einen kritischen Status erreicht, ist die gesamte Kategorie auf der Übersichtsseite kritisch. Dieselbe Zusammenfassung kann auf Umgebungs- oder Instanzebene angezeigt werden.

![Systemüberwachung – Übersicht](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Beim Navigieren zu dieser Seite werden die Instanzen der Produktionsumgebung standardmäßig angezeigt, aber es können auch andere Umgebungen angezeigt werden.

## Details zur Systemüberwachung {#system-monitoring-detail}

Um die Details zu bestimmten Metriken anzuzeigen, klicken Sie auf eine der Kategoriespalten einer bestimmten Instanz oder auf den Kategorietitel im linken Navigationsbereich. Jede Detailseite präsentiert eine Reihe von Diagrammen für die Metriken in dieser Kategorie. Sie können die Metriken entweder für alle Instanzen in einer Umgebung oder für eine bestimmte Instanz anzeigen. Mithilfe der Dropdownfelder oben rechts können Sie zwischen der Umgebung und den Instanzen wechseln.

![Umgebung auswählen](/help/assets/System_Monitoring1.png)

Im Navigationsbereich auf der linken Seite finden Sie die verfügbaren Metriken innerhalb der aktuell ausgewählten Kategorie, für die Daten für die aktuelle Umgebungs- und Instanzenauswahl vorhanden sind.

In einem Diagramm werden der Status und ein Graph der Daten im Laufe der Zeit zusammen mit den Schwellenwerten angezeigt. Wenn mehrere Instanzen angezeigt werden, werden die Daten jeder Instanz in einer separaten Reihe angezeigt.

![Metrikdiagramm](/help/assets/Monitoring_Graphs1.png)

Einzelne Serien können in einem Diagramm durch Klicken auf die Serie in der Legende aus der Ansicht entfernt werden.
Wenn Sie z. B. auf die Serie Warnschwellenwert klicken, sehen Sie nur den kritischen Schwellenwert.

![Graph ändern](/help/assets/Monitoring_Graphs2.png)

### Metrikdefinitionen {#metric-definitions}

#### Host {#host}

* **`Load Per Core`**: Die Anzahl der Prozesse, die von der CPU ausgeführt werden. Oder die Anzahl der Prozesse in der Warteschlange, die sich in einem Wartezustand befinden, gemittelt über einen Zeitraum von einer Minute (load1), fünf Minuten (load5) und fünfzehn Minuten (load15).
* **`Process Count`**: Die Anzahl der derzeit geöffneten Prozesse.
* **`User Count`**: Die Anzahl der Benutzer mit einer aktiven Shell-Sitzung.
* **`Memory Usage`**: Der Prozentsatz des aktuell zugewiesenen Systemspeichers.
* **`JVM Memory`**: Die Größe (in Megabyte) des zugewiesenen Java Heap.
* **`Old Generation Space`**: Der Prozentsatz des aktuell zugewiesenen JVM-Arbeitsspeichers der alten Generation.

#### Netzwerk {#network}

* **`CQ Port Check`**: Die Reaktionszeit in Sekunden, um auf den AEM- oder Dispatcher-Port zuzugreifen. Es gibt verschiedene Metriken für „author“, „publish“ und „dispatcher“.

#### Speicher {#storage}

* **`Disk Space`**: Der für jeden einzelnen Bereitstellungspunkt auf dem Host belegte Speicherplatz (in Megabyte). Für jeden Bereitstellungspunkt gibt es verschiedene Metriken. Es werden zumindest Metriken für `/` und `/mnt` angezeigt. Abhängig von der jeweiligen Instanzkonfiguration sind jedoch weitere Bereitstellungspunkt-Metriken verfügbar.
* **`Folder Size`**
* **`AEM Segment Store`**: Der für den AEM-Segmentspeicher belegte Speicherplatz (in Gigabyte).

#### Programm {#application}

* **`Replication Agent`**: Die Zeit (in Sekunden) für eine Testreplikation
  * Für jeden Replikationsagenten gibt es verschiedene Metriken.
* **`Dispatcher Flush`**: Die Anzahl der sich derzeit in der Dispatcher-Leerungswarteschlange befindlichen Elemente

## SLA-Berichte {#sla-reporting}

Sie können die Leistung Ihrer AEM-Produktionsumgebung im Vergleich zu Ihrem vertraglich vereinbarten Service Level Agreement (SLA) sehen.

Das folgende Diagramm zeigt die monatliche SLA-Erreichung für 2019.

![SLA-Diagramm 2018](/help/assets/SLA-Reports-one.png)

Wie bei den Systemüberwachungsdiagrammen werden beim Bewegen des Mauszeigers über einen Datenpunkt die spezifischen Werte für diesen Monat angezeigt.

![Datenpunkt-Rollover](/help/assets/SLA-Reports-two.png)

Der Abschnitt **Ereignisanalyse** unter diesem Diagramm zeigt die Vorfälle, die im aktuell ausgewählten Jahr im Zusammenhang mit dem Programm aufgetreten sind. Für jeden Vorfall werden Zeitraum und Ursache mitsamt Kommentaren angegeben.

![Ereignisanalyse](/help/assets/sla-reporting3.png)

## SLA-Metriken {#sla-metrics}

* **`Author Contract`**: Die SLA, die in Ihrem Vertrag mit Adobe Managed Services für die Autorenebene definiert ist.
* **`AMS Author SLA`**: Gemessene Betriebszeit der Produktions-Autorenebene, Factoring-Vorfälle, die von Anbietern oder Adobe verursacht wurden.
* **`Author SLA`**: Die gemessene Betriebszeit in der Autorenebene, wobei geplante Ausfallzeiten wie Wartungsfenster ignoriert werden.
* **`End User Contract`**: Die SLA, die in Ihrem Vertrag mit Adobe Managed Services für die Veröffentlichungsebene definiert ist.
* **`AMS End User SLA`**: Die gemessene Produktionszeit in der Produktions-Publishing-Ebene, Factoring-Vorfälle, die von Anbietern oder Adobe verursacht wurden.
* **`End User SLA`**: Die gemessene Betriebszeit auf der Veröffentlichungsebene, wobei geplante Ausfallzeiten wie Wartungsfenster ignoriert werden.

## Video-Tutorial {#video-tutorial}

Dieses Video bietet einen Überblick über die Verwendung der von Cloud Manager Reports erstellten Diagramme zur Überwachung Ihrer Programmumgebungen.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
