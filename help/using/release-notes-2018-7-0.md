---
title: Versionshinweise für 2018.7.0
seo-title: Versionshinweise für 2018.7.0
description: Weitere Informationen zu Cloud Manager 2018.7.0
seo-description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2018.7.0.
uuid: d7b49e32-01dc-48ce-b744-e6a806fbdd8a
contentOwner: jsyal
topic-tags: release-notes
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: b64bf9ab-27ed-4f33-adc8-d73d34094f1b
feature: Versionshinweise
exl-id: fc0214b4-d138-470a-9b04-191224927f7b
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2018.7.0 {#release-notes-for}

Im folgenden Abschnitt wird die Cloud [!UICONTROL Manager]-Version 2018.7.0 mit ihrer Funktion zur *automatischen Skalierung* vorgestellt.

Die **automatische Skalierung** wird über eine horizontale Ausskalierung`Dispatcher/Publish` von Segmenten in der Produktionsumgebung ermöglicht, um einen plötzlichen Anstieg bei Auslastung, Volumen, Zugriff und anderen definierten überwachten Metriken zu unterstützen.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2018.7.0 wurde am 10. September 2018 veröffentlicht.

## Neuigkeiten {#what-s-new}

* **Bereitstellung**: [!UICONTROL Cloud Manager] bietet jetzt die Möglichkeit, die Produktionsumgebung im Kundenprogramm durch eine horizontale Ausskalierung mit Dispatcher-/Veröffentlichungssegmenten automatisch zu skalieren. Neu in der UI ist der Abschnitt „Bereitstellung“ in der Programmeinrichtung. Dieser wird angezeigt, wenn die Funktion zur automatischen Skalierung im Kundenprogramm aktiviert ist. Weitere Informationen finden Sie unter [Einrichten des Programms](setting-up-program.md).

* **Umgebungen**: Es ist nun möglich, eine detaillierte Ansicht der Produktions- und Staging-Umgebung zusammen mit der Größe, dem Speicher, der Region und dem Status der mit den einzelnen Umgebungen verknüpften Knoten anzuzeigen. Weitere Informationen finden Sie unter [Verwalten von Umgebungen](manage-your-environment.md).

* **Analyse der Code-Qualität**: Neue Regel zur Erkennung einer fehlerhaften API-Nutzung. Weitere Informationen finden Sie unter [Qualitätsregeln für benutzerdefinierten Code](custom-code-quality-rules.md).

* **Leistungstests**: Bei der Anzeige von Leistungstestergebnissen werden CPU-Auslastung, Festplatten-I/O-Wartezeit, Seitenfehlerrate, Festplatten-Bandbreitenauslastung, Netzwerk-Bandbreitenauslastung, maximale Seitenreaktionszeit und 95. Perzentil der Seitenreaktionszeit grafisch dargestellt. Weitere Informationen finden Sie im Abschnitt *Leistungstests* auf der Seite [Wissenswertes zu Testergebnissen](understand-your-test-results.md).

* **Leistungstests**: Beim Anzeigen der Leistungstestergebnisse können Sie eine Liste der Seitenfehler und langsamen Anforderungen herunterladen. Weitere Informationen finden Sie im Abschnitt *Leistungstests* auf der Seite [Wissenswertes zu Testergebnissen](understand-your-test-results.md).

## Fehlerbehebungen {#bug-fixes}

* Unter bestimmten Umständen schlug die interne Synchronisierung unpassenderweise fehl, was inkonsistente Datenansichten zur Folge hatte.
* In einigen Fällen wurde der manuelle Pipelineauslöser nicht automatisch ausgewählt. Hierdurch traten Problemen bei der Formularüberprüfung auf.
* Bestimmte Kunden-Buildskripte konnten aufgrund von Plug-in-Inkompatibilitäten Fehler während des Buildschritts verursachen.

## Bekannte Probleme {#known-issues}

* Obwohl Kunden den Commitauslöser auswählen können, wird die Pipeline möglicherweise nicht auf Grundlage neuer Commits gestartet.
* In der Seitenleiste für [!UICONTROL Experience Cloud]-Benachrichtigungen werden Benachrichtigungen möglicherweise nicht konsistent geladen. Benachrichtigungen werden jedoch in [!UICONTROL Experience Cloud] angezeigt und, sofern konfiguriert, weiterhin per E-Mail gesendet.
