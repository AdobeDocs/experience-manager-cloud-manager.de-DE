---
title: Überwachen von Umgebungen
description: Informationen zum Überwachen von Umgebungen in Cloud Manager.
exl-id: 32886133-d6c0-4aed-8bb0-81b84f63e825
source-git-commit: ab527beb706ab73a14cc933a3414873dee6b7a9e
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 100%

---


# Überwachen von Umgebungen {#monitoring-environments}

Informationen zum Überwachen von Umgebungen in Cloud Manager.

## Schwellenwerte für Metriken {#thresholds}

Die Systemüberwachung in [!UICONTROL Cloud Manager] erfolgt durch Beobachtung der einzelnen Instanzen innerhalb einer Umgebung und Verfolgung verschiedener Metriken für jede Instanz. Jede Metrik hat zwei definierte Schwellenwerte: einen Warnschwellenwert und einen kritischen Schwellenwert.

Wenn eine Metrik über ihrem kritischen Schwellenwert liegt, wird dies als kritischer Status betrachtet. Wenn eine Metrik über dem Warnschwellenwert liegt (aber unter ihrem kritischen Schwellenwert), wird dies als Warnstatus betrachtet. Die Schwellenwerte werden von Adobe Managed Services festgelegt und können in [!UICONTROL Cloud Manager] visualisiert werden. In den meisten Fällen sind die Schwellenwerte zwischen Kunden konsistent. Es gibt jedoch Fälle, in denen Adobe Managed Services Schwellenwerte für bestimmte Kundenanforderungen anpasst. Fragen zu Schwellenwerten richten Sie bitte an Ihren Customer Success Engineer (CSE).

## Zugriff auf die Systemüberwachung {#accessing-system-monitoring}

Führen Sie diese Schritte aus, um auf die Systemüberwachung zuzugreifen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Tippen oder klicken Sie für das Programm, das Sie überwachen möchten, auf die Schaltfläche mit den Auslassungspunkten und wählen Sie die Option **Überwachung anzeigen**.

   ![Einstellungen](/help/assets/first-timea1.png)

Die Seite **Berichte** wird geöffnet, um Informationen zur Systemüberwachung anzuzeigen.

## Systemüberwachung – Übersicht {#system-monitoring-overview}

Der Abschnitt **Systemüberwachung** auf der Seite **Berichte** listet die überwachten Umgebungen im Programm auf und berichtet über ihren Zustand in vier verschiedenen Kategorien:

* Host
* Speicherung
* Netzwerk
* Programm

Der Status in jeder Kategorie ist eine Zusammenfassung einzelner Metriken. Wenn eine Metrik in einer Kategorie einen kritischen Status aufweist, hat die gesamte Kategorie einen kritischen Status auf der Seite „Übersicht“. Dieselbe Zusammenfassung kann auf Umgebungs- und Instanzebene angezeigt werden.

![Systemüberwachung – Übersicht](/help/assets/System-Monitoring-Reports.png)

>[!NOTE]
>
>Beim Navigieren zu dieser Seite werden die Instanzen der Produktionsumgebung standardmäßig angezeigt, aber es können auch andere Umgebungen angezeigt werden.

## Details zur Systemüberwachung {#system-monitoring-detail}

Um die Details zu einer bestimmten Metrik anzuzeigen, tippen oder klicken Sie auf eine der Kategoriespalten einer bestimmten Instanz oder auf den Kategorietitel im linken Navigationsbereich. Jede Detailseite präsentiert eine Reihe von Diagrammen für die Metriken in dieser Kategorie. Sie können die Metriken entweder für alle Instanzen in einer Umgebung oder für eine bestimmte Instanz anzeigen. Mithilfe der Dropdownfelder oben rechts können Sie zwischen der Umgebung und den Instanzen wechseln.

![Umgebung auswählen](/help/assets/System_Monitoring1.png)

Im Navigationsbereich auf der linken Seite finden Sie die verfügbaren Metriken innerhalb der aktuell ausgewählten Kategorie, für die Daten für die aktuell ausgewählte Umgebung und die Instanzen vorhanden sind.

In einem einzelnen Diagramm werden der Status und ein Graph der Daten zusammen mit den Schwellenwerten angezeigt. Wenn mehrere Instanzen angezeigt werden, befinden sich die Daten jeder Instanz in einer separaten Reihe.

![Metrikdiagramm](/help/assets/Monitoring_Graphs1.png)

Einzelne Reihen können in einem Diagramm ausgeblendet werden, indem Sie auf die Reihe in der Legende klicken.
Wenn Sie beispielsweise auf die Warnschwellenwert-Reihe klicken, wird nur der kritische Schwellenwert angezeigt.

![Diagramm ändern](/help/assets/Monitoring_Graphs2.png)

### Metrikdefinitionen {#metric-definitions}

#### Host {#host}

* **Last pro Kern**: Die Anzahl der Prozesse, die von der CPU ausgeführt werden oder sich in einem über einen Zeitraum von einer (load1), fünf (load5) und fünfzehn (load15) Minuten gemittelten Wartestatus befinden
* **Prozessanzahl**: Die Anzahl der derzeit geöffneten Prozesse
* **Anwenderanzahl**: Die Anzahl der Anwender mit einer aktiven Shell-Sitzung
* **Speicherauslastung**: Der Prozentsatz des aktuell zugewiesenen Systemspeichers
* **JVM-Arbeitsspeicher**: Die Größe (in Megabyte) des zugewiesenen Java Heap
* **Bereich für die alte Generation von Objekten (Old Generation Space)**: Der Prozentsatz, der derzeit dem JVM-Speicher für die alte Generation von Objekten zugewiesen ist

#### Netzwerk {#network}

* **CQ-Port-Prüfung**: Die Reaktionszeit in Sekunden, um auf den AEM- oder Dispatcher-Port zuzugreifen
   * Es gibt verschiedene Metriken für Autor, Veröffentlichung und Dispatcher.

#### Speicherung {#storage}

* **Speicherplatz**: Der für jeden einzelnen Bereitstellungspunkt auf dem Host belegte Speicherplatz (in Megabyte)
   * Für jeden Bereitstellungspunkt gibt es verschiedene Metriken.
   * Es werden zumindest Metriken für `/` und `/mnt` angezeigt. Abhängig von der jeweiligen Instanzkonfiguration können jedoch weitere Bereitstellungspunkt-Metriken verfügbar sein.
* **Ordnergröße**
* **AEM-Segmentspeicher**: Der für den AEM-Segmentspeicher belegte Speicherplatz (in Gigabyte)

#### Programm {#application}

* **Replizierungsagent**: Die Zeit (in Sekunden) für eine Testreplikation
   * Für jeden Replizierungsagenten gibt es verschiedene Metriken.
* **Dispatcherflush**: Die Anzahl der sich aktuell in der Dispatcherflush-Warteschlange befindlichen Elemente

## SLA-Berichte {#sla-reporting}

Sie können die Leistung Ihrer AEM-Produktionsumgebung im Vergleich zu Ihrem vertraglich vereinbarten Service Level Agreement (SLA) sehen.

Das folgende Diagramm zeigt die monatliche SLA-Erreichung für 2019.

![SLA-Diagramm 2018](/help/assets/SLA-Reports-one.png)

Wie bei den Systemüberwachungsdiagrammen werden beim Bewegen der Maus über einen Datenpunkt die spezifischen Werte für diesen Monat angezeigt.

![Datenpunkt-Rollover](/help/assets/SLA-Reports-two.png)

Der Abschnitt **Ereignisanalyse** unter diesem Diagramm zeigt die Anzahl von Vorfällen, die im aktuell ausgewählten Jahr beim Programm aufgetreten sind. Für jeden Vorfall werden Zeitraum und Ursache mitsamt Kommentaren angegeben.

![Ereignisanalyse](/help/assets/sla-reporting3.png)

## SLA-Metriken {#sla-metrics}

* **Autor-Vertrag**: Dies ist der SLA, der in Ihrem Vertrag mit Adobe Managed Services für die Autorenstufe definiert ist.
* **AMS-Autor-SLA**: Dies ist die gemessene Produktionszeit im Hinblick auf Factoring-Vorfälle in der Produktions-Autorenstufe, die von Adobe oder unseren Anbietern verursacht wurden.
* **Autor-SLA**: Dies ist die gemessene Produktionszeit der Autorenstufe ohne Berücksichtigung geplanter Ausfallzeiten wie z. B. Wartungsfenster.
* **Endbenutzervertrag**: Dies ist der SLA, der in Ihrem Vertrag mit Adobe Managed Services für die Veröffentlichungsstufe definiert ist.
* **AMS-Endbenutzer-SLA**: Dies ist die gemessene Produktionszeit im Hinblick auf Factoring-Vorfälle in der Produktionsveröffentlichungsstufe, die von Adobe oder unseren Anbietern verursacht wurden.
* **Endbenutzer-SLA**: Dies ist die gemessene Produktionszeit der Veröffentlichungsstufe ohne Berücksichtigung geplanter Ausfallzeiten wie z. B. Wartungsfenster.

## Video-Tutorial {#video-tutorial}

Dieses Video bietet einen Überblick über die Verwendung der von Cloud Manager Reports erstellten Diagramme, die einen Einblick in Ihre Programmumgebungen geben.

>[!VIDEO](https://video.tv.adobe.com/v/26315/)
