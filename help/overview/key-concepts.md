---
title: Wichtige Konzepte
description: Wie alle leistungsstarken Tools umfasst Cloud Manager viele Konzepte und Begriffe. Dieses Dokument fasst einige der wichtigsten Informationen für Sie bei den ersten Schritten mit Cloud Manager zusammen.
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
TQID: https://experienceleague.adobe.com/usnXqDujeZ04U5hOtiI76aemlj-ceToAOtAYS9U0UuM
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 628eceafe63153d64151937df85937135bdc8e7b
workflow-type: tm+mt
source-wordcount: 421
ht-degree: 60%

---

# Wichtige Konzepte {#key-concepts}

Cloud Manager umfasst viele Konzepte und Begriffe. Dieser Artikel fasst einige der wichtigsten Konzepte für Sie zusammen, wenn Sie mit der Arbeit mit Cloud Manager beginnen.

## Programm {#application}

Eine Anwendung ist eine Reihe von Anpassungen und Konfigurationen, die von Kundinnen und Kunden erstellt werden, um die zugrundeliegende [Lösung](#solution) (z. B. AEM Sites oder AEM Assets) an ihre spezifischen Anwendungsfälle und individuellen Bedürfnisse anzupassen. Ein Programm ist eine logische Einheit, die aus mehreren [Artefakten“ &#x200B;](#artifact).

Eine Beispielanwendung ist die fiktive [WKND-Lifestyle-Anwendung](https://experienceleague.adobe.com/de/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview).

## Artefakt {#artifact}

Ein Artefakt ist eine bereitstellbare Einheit und das Ergebnis eines Build-Prozesses, der den Quell-Code in eine einzige Einheit umwandelt. z. B. eine ZIP-Datei mit dem Quell-Code.

## Artefakt-Repository {#artifact-repository}

Ein Artefakt-Repository ist ein Speicherort, an dem kundenspezifische [Artefakte](#artifact) gespeichert und gesichert werden.

## Umgebung {#environment}

Eine Umgebung ist ein einzelnes Cluster virtueller Maschinen innerhalb eines [Programms](#program). Bei AEM besteht diese Umgeung aus einer Autoreninstanz (optional mit einer zusätzlichen Cold-Standby-Autoreninstanz), möglicherweise Veröffentlichungsinstanzen, einer oder mehreren Dispatcher-Instanzen sowie einem Load-Balancer.

## Git-Repository {#git-repository}

Ein Git-Repository ist ein Speicherort, an dem kundenspezifischer Quell-Code [unter Verwendung von Git](https://git-scm.com) gespeichert und zugänglich ist.

## Instanz {#instance}

Eine Instanz ist ein bestimmter virtueller Server, auf dem die [AEM-Lösung](#solution) ausgeführt wird. Instanzen stehen für eine einzige logische Einheit aus der Bereitstellungsperspektive.

## Organisation {#organization}

Eine Organisation ist ein Adobe-Konstrukt, das einen Unternehmenskunden repräsentiert. Ein Unternehmen kann über mehrere Organisationen verfügen, je nachdem, wie sie im Identity Management System (IMS) von Adobe bereitgestellt werden.

## Pipeline {#pipeline}

Eine Pipeline ist ein Satz von Bereitstellungsschritten, die nacheinander ausgeführt werden.

## Produkt {#product}

Ein Produkt ist ein bestimmter Funktionssatz innerhalb einer von einer Organisation lizenzierten [Lösung](#solution). Verschiedene [Programme](#program) innerhalb einer Organisation haben Anspruch auf verschiedene Produktgruppen, z. B. AEM Sites, AEM Assets oder AEM Forms.

## Programm {#program}

Bei einem Programm handelt es sich um eine Reihe von Umgebungen, die eine logische Gruppierung von Kundeninitiativen unterstützen. Diese entsprechen in der Regel einer erworbenen service level agreement (SLA). Jedes Programm verfügt über genau eine Produktionsumgebung und viele produktionsfremde Umgebungen.

## Lösung {#solution}

Eine Lösung ist eine der Adobe [!UICONTROL Experience Cloud]-Lösungen, z. B. Adobe Experience Manager, Adobe Target oder Adobe Analytics.

## Schritt {#step}

Ein Schritt ist eine konfigurierte Anweisung für bestimmte Arbeitseinheiten, z. B. eine Komponente einer [Pipeline](#pipeline).
