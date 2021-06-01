---
title: Schlüsselkonzepte
seo-title: Schlüsselkonzepte
description: Diese Seite listet die mit Cloud Manager verknüpften Schlüsselbegriffe auf.
seo-description: Auf dieser Seite werden die wichtigsten Begriffe im Zusammenhang mit Cloud Manager erklärt.
uuid: 2a37810b-98f8-4f01-90de-1e52c754ad16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: b702dfc0-3534-4d90-af19-8559d8baf6a6
feature: Erste Schritte
level: Beginner
exl-id: 86dfc976-f3da-479a-9faa-08f40ca909e0
source-git-commit: f9b33de0f1f2203175f66f261c8ee553f47e0c3b
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 98%

---

# Schlüsselkonzepte {#key-concepts}

Auf dieser Seite werden verschiedene grundlegende Cloud Manager-Begriffe beschrieben. Wir empfehlen dringend, diese Seite zu lesen, bevor Sie sich die übrige Cloud Manager-Dokumentation ansehen.

**Anwendung** Die von einem Kunden erstellten Individualisierungen und Konfigurationen, um die zugrunde liegende Lösung gemäß seinen Anwendungsfällen und Anforderungen anzupassen. Eine Anwendung ist eine logische Einheit, die aus mehreren Artefakten bestehen kann.

Beispiel: *We.Retail*

**Artefakt** Eine bereitstellbare Einheit. Das Ergebnis einiger Buildprozesse, bei denen Quellcode in eine Einheit umgewandelt wird, z. B. eine ZIP-Datei mit dem Quellcode.

**Artefakt-Repository** Ein Speicherort, an dem kundenspezifische Artefakte gespeichert und gesichert werden.

**Umgebung** Ein einzelnes Cluster virtueller Maschinen innerhalb eines Programms. Bei AEM besteht dieses aus einer Autoreninstanz (optional mit einer zusätzlichen Cold-Standby-Autoreninstanz), keiner oder mehreren Veröffentlichungsinstanzen, einer oder mehreren Dispatcherinstanzen sowie einem Load-Balancer.

**Git-Repository** Ein Speicherort, an dem kundenspezifischer Quellcode gespeichert wird. Zugriff ist über das Git-Protokoll möglich.

**Instanz** Ein bestimmter virtueller Server, auf der die AEM-Lösung ausgeführt wird. Instanzen stehen für eine einzige logische Einheit aus der Bereitstellungsperspektive.

**Organisation** Adobe-Konstrukt, das einen Unternehmenskunden repräsentiert. Ein Unternehmen kann mehrere Organisationen umfassen, je nachdem, wie diese ursprünglich im Identity-Management-System von Adobe bereitgestellt wurden.

**Pipeline** Ein Satz von Bereitstellungsschritten, die nacheinander ausgeführt werden.

**Produkt** Ein bestimmter Funktionssatz innerhalb einer von einer Organisation lizenzierten Lösung. Verschiedene Programme innerhalb einer Organisation können Anspruch auf verschiedene Produkte haben, Zum Beispiel Sites, Assets oder Forms.

**Programm** Ein Satz von Umgebungen, die eine logische Gruppierung von Kundeninitiativen unterstützen. Im Normalfall erfolgt dies gemäß dem erworbenen Service-Level-Agreement (SLA). Jedes Programm hat genau eine Produktionsumgebung und kann zahlreiche Nicht-Produktionsumgebungen aufweisen.

**Lösung** Eine der Adobe [!UICONTROL Experience Cloud]-Lösungen, z. B. Adobe Experience Manager, Adobe Target oder Adobe Analytics.

**Schritt** Konfigurierte Anweisungen für bestimmte Arbeitseinheiten; Baustein einer Pipeline.
