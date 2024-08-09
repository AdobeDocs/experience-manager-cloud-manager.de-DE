---
title: Wichtige Konzepte
description: Wie alle leistungsstarken Tools umfasst Cloud Manager viele Konzepte und Begriffe. Dieses Dokument fasst einige der wichtigsten Informationen für Sie bei den ersten Schritten mit Cloud Manager zusammen.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 72%

---


# Wichtige Konzepte {#key-concepts}

Wie alle leistungsstarken Tools umfasst Cloud Manager viele Konzepte und Begriffe. Dieses Dokument fasst einige der wichtigsten Informationen für Sie bei den ersten Schritten mit Cloud Manager zusammen.

## Programm {#application}

Eine Anwendung ist eine Reihe von Anpassungen und Konfigurationen, die von einer Kundin bzw. einem Kunden erstellt werden, um die zugrundeliegende [Lösung](#solution) (z. B. AEM Sites oder AEM Assets) für ihre spezifischen Anwendungsfälle und Bedürfnisse anzupassen. Eine Anwendung ist eine logische Einheit, die aus mehreren [Artefakten](#artifact) bestehen kann.

Eine Beispielanwendung ist die fiktive [WKND-Lifestyle-Anwendung](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de).

## Artefakt {#artifact}

Ein Artefakt ist eine bereitstellbare Einheit und das Ergebnis eines Build-Prozesses, der den Quell-Code in eine einzige Einheit verwandelt, z. B. eine .zip-Datei mit dem Quell-Code.

## Artefakt-Repository {#artifact-repository}

Ein Artefakt-Repository ist ein Speicherort, an dem kundenspezifische [Artefakte](#artifact) gespeichert und gesichert werden.

## Umgebung {#environment}

Eine Umgebung ist ein einzelnes Cluster virtueller Maschinen innerhalb eines [Programms](#program). AEM besteht diese aus einer Authoring-Instanz (optional mit einer zusätzlichen Cold-Standby-Authoring-Instanz), null oder mehr Veröffentlichungsinstanzen, einer oder mehreren Dispatcher-Instanzen und einem Lastenausgleich.

## Git-Repository {#git-repository}

Ein Git-Repository ist ein Speicherort, an dem kundenspezifischer Quellcode gespeichert wird und [mit git](https://git-scm.com) aufgerufen werden kann.

## Instanz {#instance}

Eine Instanz ist ein bestimmter virtueller Server, auf dem die AEM [Lösung](#solution) ausgeführt wird. Instanzen stehen für eine einzige logische Einheit aus der Bereitstellungsperspektive.

## Organisation {#organization}

Eine Organisation ist ein Adobe-Konstrukt, das einen Unternehmenskunden repräsentiert. Ein Unternehmen kann mehrere Organisationen umfassen, je nachdem, wie diese im Identity-Management-System (IMS) von Adobe bereitgestellt wurden.

## Pipeline {#pipeline}

Eine Pipeline ist ein Satz von Bereitstellungsschritten, die nacheinander ausgeführt werden.

## Produkt {#product}

Ein Produkt ist ein bestimmter Funktionssatz innerhalb einer von einer Organisation lizenzierten [Lösung](#solution). Verschiedene [Programme](#program) innerhalb einer Organisation können Berechtigungen für verschiedene Produktgruppen haben, z. B. AEM Sites, AEM Assets oder AEM Forms.

## Programm {#program}

Ein Programm ist ein Satz von Umgebungen, die eine logische Gruppierung von Kundeninitiativen unterstützen. Im Normalfall erfolgt dies gemäß dem erworbenen Service-Level-Agreement (SLA). Jedes Programm hat genau eine Produktionsumgebung und kann zahlreiche Nicht-Produktionsumgebungen aufweisen.

## Lösung {#solution}

Eine Lösung ist eine der Adobe [!UICONTROL Experience Cloud]-Lösungen, z. B. Adobe Experience Manager, Adobe Target oder Adobe Analytics.

## Schritt {#step}

Ein Schritt ist ein konfigurierter Anweisungssatz, der eine bestimmte Arbeitseinheit als Baustein einer [Pipeline](#pipeline) ausführt.
