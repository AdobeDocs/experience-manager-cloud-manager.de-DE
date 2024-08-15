---
title: Überwachen von Umgebungen
description: Informationen zum Überwachen von Umgebungen in Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 33%

---


# Umgebungen überwachen {#monitoring-environments}

Informationen zum Überwachen von Umgebungen in Cloud Manager.

## Metrikschwellen {#thresholds}

Die Systemüberwachung in [!UICONTROL Cloud Manager] erfolgt durch Beobachtung der einzelnen Instanzen innerhalb einer Umgebung und Verfolgung verschiedener Metriken für jede Instanz. Jede Metrik hat zwei definierte Schwellenwerte: einen Schwellenwert für *Warnung* und einen Schwellenwert für *Kritisch*.

Wenn eine Metrik über ihrem Warnschwellenwert liegt (aber unter ihrem kritischen Schwellenwert), wird sie als Warnstatus betrachtet.

Wenn eine Metrik ihren kritischen Schwellenwert überschreitet, wird sie als kritisch betrachtet.

Adobe Managed Services legt die Schwellenwerte fest, die Sie in [!UICONTROL Cloud Manager] anzeigen können. In den meisten Fällen sind die Schwellenwerte zwischen den Kunden konsistent. Es gibt jedoch Fälle, in denen Adobe Managed Services Schwellenwerte bearbeitet, um bestimmten Kundenanforderungen zu entsprechen. Weisen Sie alle Fragen zu den Schwellenwerten an Ihren Customer Success Engineer (CSE) zu.

## Systemüberwachung {#accessing-system-monitoring}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf die Suchschaltfläche des Programms, das Sie überwachen möchten.
1. Klicken Sie im Menü unter der Überschrift **Verwalten** auf **Überwachung anzeigen** , um die Seite **Berichte** zu öffnen, auf der Informationen zur Systemüberwachung angezeigt werden.

   ![Einstellungen](/help/assets/first-timea1.png)

.

## Systemüberwachung - Übersicht {#system-monitoring-overview}

Im Abschnitt **Systemüberwachung** der Seite **Berichte** werden die überwachten Umgebungen im Programm aufgelistet. Sie berichtet über ihre allgemeine Gesundheit in den folgenden vier verschiedenen Kategorien:

* Host
* Speicherung
* Netzwerk
* Programm

Der Status in jeder Kategorie ist eine Zusammenfassung einzelner Metriken. Wenn eine Metrik in einer Kategorie den kritischen Status aufweist, befindet sich die gesamte Kategorie in einem kritischen Status für die Zwecke der Übersichtsseite. Dieselbe Zusammenfassung kann auf Umgebungs- und Instanzebene angezeigt werden.

![Systemüberwachung – Übersicht](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Beim Navigieren zu dieser Seite werden die Instanzen der Produktionsumgebung standardmäßig angezeigt, aber es können auch andere Umgebungen angezeigt werden.

## Details zur Systemüberwachung {#system-monitoring-detail}

Um die Details bestimmter Metriken anzuzeigen, klicken Sie auf eine der Kategoriespalten einer bestimmten Instanz oder auf den Kategorientitel im linken Navigationsbereich. Jede Detailseite präsentiert eine Reihe von Diagrammen für die Metriken in dieser Kategorie. Sie können die Metriken entweder für alle Instanzen in einer Umgebung oder für eine bestimmte Instanz anzeigen. Mithilfe der Dropdownfelder oben rechts können Sie zwischen der Umgebung und den Instanzen wechseln.

![Umgebung auswählen](/help/assets/System_Monitoring1.png)

Die Navigation auf der linken Seite zeigt die verfügbaren Metriken innerhalb der aktuell ausgewählten Kategorie an, für die Daten für die aktuell ausgewählte Umgebung und Instanzen vorhanden sind.

In einem einzelnen Diagramm werden der Status und ein Graph der Daten zusammen mit den Schwellenwerten angezeigt. Wenn mehrere Instanzen angezeigt werden, befinden sich die Daten jeder Instanz in einer separaten Reihe.

![Metrikdiagramm](/help/assets/Monitoring_Graphs1.png)

Einzelne Reihen können in einem Diagramm ausgeblendet werden, indem Sie auf die Reihe in der Legende klicken.
Wenn Sie beispielsweise auf die Warnungsschwellenreihe klicken, sehen Sie nur den kritischen Schwellenwert.

![Diagramm ändern](/help/assets/Monitoring_Graphs2.png)

### Metrikdefinitionen {#metric-definitions}

#### Host {#host}

* **Pro Core laden**: Die Anzahl der Prozesse, die die CPU ausführt. Oder die Anzahl der Prozesse in der Warteschlange, die sich in einem Wartezustand befinden, gemittelt über einen Zeitraum von einer (load1), fünf (load5) und fünfzehn (load15) Minuten.
* **Prozessanzahl**: Die Anzahl der derzeit geöffneten Prozesse.
* **Benutzeranzahl**: Die Anzahl der Benutzer mit einer aktiven Shell-Sitzung.
* **Speichernutzung**: Der Prozentsatz des zurzeit zugewiesenen Systemspeichers.
* **JVM-Speicher**: Die Größe (in Megabyte) des zugewiesenen Java-Heap.
* **Alter Generationsspeicher**: Der Prozentsatz des JVM-Speicherplatzes der alten Generation, der derzeit zugewiesen ist.

#### Netzwerk {#network}

* **CQ-Port-Prüfung**: Die Antwortzeit in Sekunden für den Zugriff auf den AEM- oder Dispatcher-Port. Es gibt verschiedene Metriken für Autor, Veröffentlichung und Dispatcher.

#### Speicher {#storage}

* **Festplattenspeicher**: Der für jeden Bereitstellungspunkt auf dem Host verwendete Speicherplatz (in Megabyte). Für jeden Bereitstellungspunkt gibt es verschiedene Metriken. Es gibt mindestens Metriken für `/` und `/mnt`, aber je nach der spezifischen Instanzkonfiguration können zusätzliche Bereitstellungspunkt-Metriken verfügbar sein.
* **Ordnergröße**
* **AEM Segmentspeicher**: Der für den AEM Segmentspeicher verwendete Speicherplatz (in Gigabyte).

#### Programm {#application}

* **Replizierungsagent**: Die Zeit (in Sekunden) für eine Testreplikation
   * Für jeden Replizierungsagenten gibt es verschiedene Metriken.
* **Dispatcher Flush**: Die Anzahl der Elemente, die sich derzeit in der Dispatcher-Flush-Warteschlange befinden

## SLA Reporting {#sla-reporting}

Sie können die Leistung Ihrer AEM-Produktionsumgebung im Vergleich zu Ihrem vertraglich vereinbarten Service Level Agreement (SLA) sehen.

Das folgende Diagramm zeigt die monatliche SLA-Erreichung für 2019.

![SLA-Diagramm 2018](/help/assets/SLA-Reports-one.png)

Wie bei den Systemüberwachungsdiagrammen werden beim Bewegen der Maus über einen Datenpunkt die spezifischen Werte für diesen Monat angezeigt.

![Datenpunkt-Rollover](/help/assets/SLA-Reports-two.png)

Der Abschnitt **Ereignisanalyse** unter diesem Diagramm zeigt die Anzahl der Vorfälle, die im aktuell ausgewählten Jahr für das Programm aufgetreten sind. Für jeden Vorfall werden Zeitraum und Ursache mitsamt Kommentaren angegeben.

![Ereignisanalyse](/help/assets/sla-reporting3.png)

## SLA-Metriken {#sla-metrics}

* **Autorenvertrag**: Die in Ihrem Vertrag mit Adobe Managed Services definierte SLA für die Autorenstufe.
* **AMS Author SLA**: Die gemessene Produktionszeit der Produktionsautorenstufe, Factoring-Vorfälle, die von Anbietern oder Adobe verursacht wurden.
* **Autor SLA**: Die gemessene Produktionszeit der Autorenstufe ohne Berücksichtigung geplanter Ausfallzeiten wie z. B. Wartungsfenster.
* **Endbenutzervertrag**: Die in Ihrem Vertrag mit Adobe Managed Services definierte SLA für die Veröffentlichungsstufe.
* **AMS-Endbenutzer-SLA**: Die gemessenen Betriebszeiten der Produktionsveröffentlichungsstufe, Factoring-Vorfälle, die von Anbietern oder Adobe verursacht wurden.
* **Endbenutzer-SLA**: Die gemessene Produktionszeit der Veröffentlichungsstufe ohne Berücksichtigung geplanter Ausfallzeiten wie z. B. Wartungsfenster.

## Video-Tutorial {#video-tutorial}

Dieses Video bietet einen Überblick über die Verwendung der von Cloud Manager Reports erstellten Diagramme, die einen Einblick in Ihre Programmumgebungen geben.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
