---
title: Wichtige Konzepte
description: Wie alle leistungsstarken Tools umfasst Cloud Manager viele Konzepte und Begriffe. Dieses Dokument fasst einige der wichtigsten Informationen für Sie bei den ersten Schritten mit Cloud Manager zusammen.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 73e322cf93dc7709b7581860974079c8d94034ba
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 10%

---


# Wichtige Konzepte {#key-concepts}

Wie alle leistungsstarken Tools umfasst Cloud Manager viele Konzepte und Begriffe. Dieses Dokument fasst einige der wichtigsten Informationen für Sie bei den ersten Schritten mit Cloud Manager zusammen.

## Anwendung {#application}

Und die Anwendung ist der Satz von Anpassungen und Konfigurationen, die von einem Kunden erstellt werden, um die zugrunde liegenden [Lösung](#solution) (z. B. AEM Sites oder AEM Assets) für spezifische Anwendungsfälle und Anforderungen. Eine Anwendung ist eine logische Einheit, die aus mehreren [Artefakte.](#artifact)

Eine Beispielanwendung ist die fiktive [WKND Lifestyle-Anwendung.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de)

## Artefakt {#artifact}

Ein Artefakt ist eine bereitstellbare Einheit und das Ergebnis eines Build-Prozesses, der Quellcode in eine Einheit umwandelt. Beispiel: eine ZIP-Datei, die den Quellcode enthält.

## Artefakt-Repository {#artifact-repository}

Ein Artefakt-Repository ist ein Speicherort, an dem kundenspezifische [Artefakte](#artifact) gespeichert und gesichert werden.

## Umgebung {#environment}

Eine Umgebung ist ein einzelnes Cluster virtueller Maschinen innerhalb eines [Programm.](#program) AEM besteht diese aus einer Authoring-Instanz (optional mit einer zusätzlichen Cold-Standby-Authoring-Instanz), null oder mehr Veröffentlichungsinstanzen, einer oder mehreren Dispatcher-Instanzen und einem Lastenausgleich.

## Git-Repository {#git-repository}

Ein Git-Repository ist ein Speicherort, an dem kundenspezifischer Quellcode gespeichert und zugänglich ist. [Verwendung von Git.](https://git-scm.com)

## Instanz {#instance}

Eine Instanz ist ein bestimmter virtueller Server, auf dem die AEM ausgeführt wird. [Lösung.](#solution) Instanzen stehen für eine einzige logische Einheit aus der Bereitstellungsperspektive.

## Firma {#organization}

Eine Organisation ist ein Adobe-Konstrukt, das einen Unternehmenskunden repräsentiert. Ein Unternehmen kann je nach der Bereitstellung im Identity Management System (IMS) der Adobe über mehrere Organisationen verfügen.

## Pipeline {#pipeline}

Eine Pipeline ist eine Reihe von Implementierungsschritten, die nacheinander ausgeführt werden.

## Produkt {#product}

Ein Produkt ist ein bestimmter Funktionssatz innerhalb einer [Lösung](#solution) von einer Organisation lizenziert ist. Unterschiedlich [Programme](#program) innerhalb einer Organisation über verschiedene Produktgruppen verfügen, z. B. über AEM Sites, AEM Assets oder AEM Forms.

## Programm {#program}

Ein Programm ist eine Reihe von Umgebungen, die eine logische Gruppierung von Kundeninitiativen unterstützen, die normalerweise einem erworbenen Service Level Agreement (SLA) entsprechen. Jedes Programm hat genau eine Produktionsumgebung und kann zahlreiche Nicht-Produktionsumgebungen aufweisen.

## Lösung {#solution}

Eine Lösung ist eine der Adoben [!UICONTROL Experience Cloud] Lösungen. Zum Beispiel Adobe Experience Manager, Adobe Target oder Adobe Analytics.

## Schritt {#step}

Ein Schritt ist ein konfigurierter Anweisungssatz, der eine bestimmte Arbeitseinheit als Baustein einer [Pipeline.](#pipeline)
