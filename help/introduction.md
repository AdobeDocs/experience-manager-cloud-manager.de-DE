---
title: Einführung in Cloud Manager für AMS
description: Hier erfahren Sie mehr über Cloud Manager für Adobe Managed Services (AMS) und darüber, wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: b0dbb602253939464ff034941ffbad84b7df77df
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 23%

---


# Einführung in [!UICONTROL Cloud Manager] für AMS {#introduction-to-cloud-manager}

Hier erfahren Sie mehr zu Cloud Manager für Adobe-Verwaltungsdienste (AMS) und dazu, wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Einführung in Cloud Manager für AMS"
>abstract="Ermöglicht es Unternehmen, Adobe Experience Manager in der Cloud selbst zu verwalten. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de#cloud-manager" text="Programme erstellen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de#cloud-manager" text="Umgebungen erstellen"

## Einführung {#introduction}

[!UICONTROL Cloud Manager] für Adobe Experience Manager bietet Entwicklern die Möglichkeit, durch optimierte Workflows, die auf Best Practices von Adobe Experience Manager basieren, überzeugende Kundenerlebnisse zu erstellen. CI/CD-Pipelines, die für Adobe Experience Manager optimiert sind, ermöglichen Ihnen das einfache Zusammenführen von Entwicklungs-Workflows, indem Sie einfach Ihren Code einchecken, der dann den ganzen Weg zur Produktionsbereitschaft ebnet. Während der Build-Phase werden Ihre benutzerspezifischen Code-Aktualisierungen gründlich anhand von Best Practices getestet, um zuverlässige Anwendungen für Ihre Kunden bereitzustellen. Cloud Manager verwendet einen offenen API-Ansatz und ermöglicht Ihnen die Integration in Ihre Systeme, ohne bestehende Prozesse und Tools zu stören.

>[!NOTE]
>
>In dieser Dokumentation werden speziell die Funktionen von Cloud Manager für Adobe Managed Services (AMS) beschrieben.
>
>Die entsprechende Dokumentation für AEM as a Cloud Service finden Sie im [AEM as a Cloud Service Dokumentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/home.html?lang=de)

Mit Cloud Manager profitiert Ihr Entwicklungsteam von den folgenden Funktionen:

* Kontinuierliche Integration/kontinuierliche Bereitstellung (CI/CD) von Code zur Verkürzung der Markteinführungszeit von Monaten/Wochen auf Tage/Stunden

* Codeüberprüfung, Leistungstests und Sicherheitsvalidierung basierend auf Best Practices, bevor sie an die Produktion gesendet werden, um Produktionsunterbrechungen zu minimieren

* API-Konnektivität zur Ergänzung vorhandener DevOps-Prozesse

* Automatische Skalierung, die intelligent erkennt, dass eine höhere Kapazität erforderlich ist, und automatisch zusätzliche Dispatcher-/Veröffentlichungssegmente online stellt

Diese Abbildung zeigt den CI/CD-Prozessfluss, der in [!UICONTROL Cloud Manager]:

![CI/CD-Fluss](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Wichtige Funktionen in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Im Folgenden werden die wichtigsten Funktionen von Cloud Manager genauer erläutert.

### Self-Service-Benutzeroberfläche {#self-service-interface}

Die Benutzeroberfläche für [!UICONTROL Cloud Manager] ermöglicht Ihnen den einfachen Zugriff auf und die Verwaltung der Cloud-Umgebung und der CI/CD-Pipeline für Ihre Adobe Experience Manager-Anwendungen.

Sie definieren anwendungsspezifische KPIs (Key Performance Indicators) (z. B. Spitzenzeiten der Seitenansichten pro Minute und erwartete Reaktionszeiten für Seitenladevorgänge), die die Grundlage für die Messung einer erfolgreichen Bereitstellung bilden. Rollen und Berechtigungen für verschiedene Teammitglieder können einfach definiert werden. Die Self-Service-Oberfläche gibt Ihnen Kontrolle, bietet aber auch Links zu Best-Practice-Ressourcen und Zugang zu Experten innerhalb der Adobe, die bei Bedarf die nötige Anleitung zur Verfügung stellen können.

Erkunden und Erste Schritte mit [!UICONTROL Cloud Manager]Die Benutzeroberfläche des Dokuments anzeigen [Erstmalige Anmeldung.](/help/getting-started/first-time-login.md)

### CI/CD-Pipeline {#ci-cd-pipeline}

Eine der Hauptfunktionen von [!UICONTROL Cloud Manager] ist die Möglichkeit, eine optimierte CI/CD-Pipeline einzurichten, um die Bereitstellung von benutzerspezifischem Code oder Aktualisierungen (z. B. hinzugefügte neue Website-Komponenten) zu beschleunigen.

Durch die [!UICONTROL Cloud Manager] Benutzeroberfläche können Sie Ihre CI/CD-Pipeline konfigurieren und starten. Im Rahmen dieser Pipeline wird eine gründliche Codescan durchgeführt, um sicherzustellen, dass nur hochwertige Anwendungen in die Produktionsumgebung übertragen werden.

Weitere Informationen zum Konfigurieren der Pipeline in der Benutzeroberfläche von [!UICONTROL Cloud Manager] finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/using/non-production-pipelines.md).

### Flexible Bereitstellungsmodi {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] bietet flexible und konfigurierbare Bereitstellungsmodi, damit Sie Erlebnisse entsprechend den sich ändernden Geschäftsanforderungen bereitstellen können.

Bei einem automatischen Trigger-Modus wird der Code basierend auf bestimmten Ereignissen wie der Codeübergabe automatisch in einer Umgebung bereitgestellt. Sie können Codebereitstellungen auch innerhalb bestimmter Zeitrahmen (auch außerhalb der Geschäftszeiten) planen.

Unabhängig vom Bereitstellungs-Trigger werden bei jeder Auslösung einer Bereitstellung Qualitätskontrollen bei der CI/CD-Pipeline-Ausführung immer durchgeführt. Zu den Qualitätsprüfungen gehören Codeprüfungen, Sicherheitstests und Leistungstests, die alle ohne Aufwand von Ihnen oder Ihren Partnern sofort bereitgestellt werden.

Weitere Informationen zur Bereitstellung von Code und Qualitätsprüfungen finden Sie im Dokument [Bereitstellen von Code.](/help/using/code-deployment.md)

### Automatische Skalierung {#autoscaling}

wenn die Produktionsumgebung ungewöhnlich stark ausgelastet ist; [!UICONTROL Cloud Manager] erkennt den Bedarf an zusätzlicher Kapazität und bringt automatisch zusätzliche Kapazität über seine Funktion zur automatischen Skalierung online.

In einem solchen Fall [!UICONTROL Cloud Manager] automatisch den automatischen Skalierungs-Bereitstellungsprozess Trigger, eine Benachrichtigung über die automatische Skalierung sendet und innerhalb von Minuten zusätzliche Kapazitäten verfügbar macht. Die zusätzliche Kapazität wird in der Produktionsumgebung bereitgestellt, in denselben Regionen und entsprechend den Systemspezifikationen wie die laufenden Dispatcher-/Veröffentlichungsknoten.

Die Funktion zur automatischen Skalierung gilt nur für die Dispatcher-/Veröffentlichungsstufe und wird mit einer horizontalen Skalierungsmethode ausgeführt, wobei mindestens ein zusätzliches Segment eines Dispatcher-/Publishing-Paares bis zu maximal zehn Segmenten verwendet wird. Jede zusätzlich bereitgestellte Kapazität wird innerhalb von zehn Arbeitstagen, wie vom CSE (Customer Success Engineer) bestimmt, manuell zurückgenommen.

>[!NOTE]
>
>Kunden, die herausfinden möchten, ob eine automatische Skalierung für ihre Anwendung geeignet ist, sollten sich an ihren CSE oder Adobe-Support-Mitarbeiter wenden.
