---
title: Einführung in Cloud Manager für AMS
description: Hier erfahren Sie mehr über Cloud Manager für Adobe Managed Services (AMS) und darüber, wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 8f29a06f63b8dc10cb3d28e2f38da1ead84f32f5
workflow-type: tm+mt
source-wordcount: '1250'
ht-degree: 95%

---


# Einführung in [!UICONTROL Cloud Manager] für AMS {#introduction-to-cloud-manager}

Hier erfahren Sie mehr über Cloud Manager für AMS (Adobe Managed Services) und darüber, wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Einführung in Cloud Manager für AMS"
>abstract="Ermöglicht Organisationen die Selbstverwaltung von Adobe Experience Manager in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen."
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Erstellen von Programmen"
>additional-url="https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Umgebungen erstellen"

## Einführung {#introduction}

[!UICONTROL Cloud Manager] für Adobe Experience Manager bietet Entwicklern die Möglichkeit, durch optimierte Workflows, die auf Best Practices von Adobe Experience Manager basieren, überzeugende Kundenerlebnisse zu erstellen. Für Adobe Experience Manager optimierte CI/CD-Pipelines ermöglichen es Ihnen, Entwicklungs-Workflows einfach zusammenzuführen, indem Sie Ihren Code einchecken und bis zur Produktionsbereitschaft führen. Während der Build-Phase werden Ihre benutzerdefinierten Code-Updates gründlich anhand von Best Practices getestet, sodass Sie zuverlässige Programme für Ihre Kunden bereitstellen. Cloud Manager arbeitet mit offenen APIs und ermöglicht Ihnen die Integration mit Ihren Systemen, ohne bestehende Prozesse und Tools zu stören.

>[!NOTE]
>
>Auf dieser Dokumentations-Website werden speziell die Funktionen von Cloud Manager beschrieben, die für Kunden von Adobe Managed Services (AMS) relevant sind.
>
>Die entsprechende Dokumentation für AEM as a Cloud Service finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/home).

Mit Cloud Manager profitiert Ihr Entwicklungs-Team von den folgenden Funktionen:

* Kontinuierliche Integration/Bereitstellung (CI/CD, Continuous Integration/Continuous Delivery) von Code zur Verkürzung der Markteinführungszeit von Monaten/Wochen auf Tage/Stunden
* Code-Prüfungen, Leistungstests und Sicherheitsprüfungen basierend auf Best Practices, bevor der Code an die Produktion gesendet wird, um Produktionsunterbrechungen zu minimieren.
* API-Konnektivität zur Ergänzung vorhandener DevOps-Prozesse.
* Automatische Skalierungsfunktion zur intelligenten Erkennung eines erhöhten Kapazitätsbedarfs und automatischen Online-Bereitstellung zusätzlicher Dispatcher-/Veröffentlichungssegmente.

![CI/CD-Fluss](/help/assets/screen_shot_2018-05-12at73843pm.png)Der CI/CD-Prozessfluss, wie er in [!UICONTROL Cloud Manager] verwendet wird.

## Wichtige Funktionen in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

In den folgenden Abschnitten werden wichtige Funktionen von Cloud Manager hervorgehoben.

### Self-Service-Benutzeroberfläche {#self-service-interface}

Weitere Informationen zur Benutzeroberfläche von [!UICONTROL Cloud Manager] und zu den ersten Schritten finden Sie unter [Erste Anmeldung](/help/getting-started/first-time-login.md).

Mit der Benutzeroberfläche für [!UICONTROL Cloud Manager] können Sie einfach auf die Cloud-Umgebung zugreifen und sie verwalten und die CI/CD-Pipeline für Ihre Adobe Experience Manager-Programme einfach einrichten.

Sie definieren anwendungsspezifische Key Performance Indicators (KPIs) wie Spitzenwerte für Seitenansichten pro Minute oder erwartete Seitenladereaktionszeiten. Diese KPIs dienen als Grundlage für die Messung des Bereitstellungserfolgs. Rollen und Berechtigungen für verschiedene Team-Mitglieder können einfach definiert werden. Die Self-Service-Oberfläche bietet Ihnen volle Kontrolle. Sie bietet außerdem Links zu Ressourcen für Best Practices und Zugang zu Adobe-Fachleuten, um bei Bedarf Orientierungshilfen zu erhalten.

### CI/CD-Pipeline {#ci-cd-pipeline}

Eine der Hauptfunktionen von [!UICONTROL Cloud Manager] ist die Möglichkeit, eine optimierte CI/CD-Pipeline einzurichten, um die Bereitstellung von benutzerspezifischem Code oder Aktualisierungen (z. B. hinzugefügte neue Website-Komponenten) zu beschleunigen.

Über die [!UICONTROL Cloud Manager]-Benutzeroberfläche können Sie CI/CD-Pipelines konfigurieren und starten. Im Rahmen dieser Pipeline wird ein gründlicher Codescan durchgeführt, um sicherzustellen, dass nur hochwertige Programme in die Produktionsumgebung übertragen werden.

Weitere Informationen zum Konfigurieren der Pipeline in der Benutzeroberfläche von [!UICONTROL Cloud Manager] finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren produktionsfremder Pipelines](/help/using/non-production-pipelines.md).

### Flexible Bereitstellungsmodi {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] bietet flexible und konfigurierbare Bereitstellungsmodi, damit Erlebnisse entsprechend den sich ändernden Geschäftsanforderungen bereitgestellt werden können.

Im automatischen Auslösermodus wird der Code basierend auf bestimmten Ereignissen (z. B. einem Code-Commit) automatisch in einer Umgebung bereitgestellt. Sie können Code-Breitstellungen auch innerhalb bestimmter Zeitrahmen (auch außerhalb der Geschäftszeiten) planen.

Unabhängig vom Bereitstellungsauslöser werden bei einer CI/CD-Pipeline-Ausführung immer Qualitätsprüfungen durchgeführt. Das gilt für jede ausgelöste Bereitstellung. Zu den Qualitätsprüfungen gehören vorkonfigurierte Code-Prüfungen, Sicherheitstests und Leistungstests, die ohne Aufwand von Ihnen oder Ihren Partnern genutzt werden können.

Weitere Informationen zum Bereitstellen von Code und zu Qualitätsprüfungen finden Sie unter [Bereitstellen von Code](/help/using/code-deployment.md).

## Optionale Funktionen in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager bietet zusätzliche erweiterte Funktionen, die je nach Einrichtung und Anforderungen Ihrer Umgebung für Ihr Projekt von Vorteil sein können. Wenn diese Funktionen für Sie von Interesse sind, wenden Sie sich an das Customer Success Engineer(CSE)-Team oder an den Adobe-Support, um weitere Informationen zu erhalten.

### Automatische Skalierung {#autoscaling}

Wenn die Produktionsumgebung ungewöhnlich stark ausgelastet ist, erkennt [!UICONTROL Cloud Manager] den Bedarf an zusätzlicher Kapazität und stellt mit seiner Funktion zur automatischen Skalierung automatisch zusätzliche Kapazität online bereit.

In einem solchen Fall löst [!UICONTROL Cloud Manager] automatisch die Skalierung aus, sendet eine Benachrichtigung über die automatische Skalierung und macht die zusätzliche Kapazität innerhalb von Minuten online verfügbar. Die zusätzliche Kapazität wird in der Produktionsumgebung bereitgestellt, und zwar in denselben Regionen und mit denselben Systemspezifikationen wie in laufenden Dispatcher-/Veröffentlichungsknoten.

Die Funktion zur automatischen Skalierung gilt für die Dispatcher-/Veröffentlichungsebene und verwendet eine horizontale Skalierung zum Hinzufügen von ein bis zehn Segmenten von Dispatcher-/Veröffentlichungspaaren. Jede zusätzlich bereitgestellte Kapazität wird innerhalb von zehn Arbeitstagen, wie vom Adobe CSE (Customer Success Engineer) festgelegt, manuell skaliert.

>[!NOTE]
>
>Wenn Sie herausfinden möchten, ob die automatische Skalierung für Ihre Anwendung geeignet ist, wenden Sie sich an Ihr CSE-Team oder an den Adobe-Support.

### Blau/Grün-Implementierungen {#blue-green}

Eine Blau/Grün-Bereitstellung ist eine Technik, die Ausfallzeiten und Risiken reduziert, indem zwei identische Produktionsumgebungen namens „Blau“ und „Grün“ ausgeführt werden.

Es ist immer nur eine der Umgebungen aktiv, wobei der gesamte Produktions-Traffic über die Live-Umgebung läuft. Generell ist Blau die derzeit aktive Umgebung und Grün ist inaktiv.

* Eine Blau/Grün-Implementierung ist ein Add-on zu CI/CD-Pipelines von Cloud Manager, bei der ein zweiter Satz an Publishing- und Dispatcher-Instanzen (grün) erstellt und für Bereitstellungen verwendet wird. Die grünen Instanzen werden dann an den Produktionslastenausgleich angehängt und die alten Instanzen (blau) werden entfernt und beendet.
* Diese Blau/Grün-Implementierung behandelt Instanzen als transient und jede Iteration einer Blau/Grün-Pipeline erstellt einen neuen Satz von Publishing- und Dispatcher-Servern.
* Im Rahmen der Einrichtung wird ein grüner Lastenausgleich erstellt. Dieser Lastenausgleich ändert sich nie und sollte auf Ihre grüne „Test“-URL verweisen.
* Bei einer Blau/Grün-Implementierung wird eine exakte Replikation der vorhandenen Dispatcher-/Veröffentlichungsebenen erstellt.

#### Blau/Grün-Implementierungsfluss {#flow}

Wenn die Blau/Grün-Implementierung aktiviert ist, unterscheidet sich der Bereitstellungsfluss vom standardmäßigen Cloud-Service-Bereitstellungsfluss.

| Schritt | Blau/Grün-Bereitstellung | Standard-Bereitstellung |
| --- | --- | --- |
| 1 | Bereitstellung für Autor | Bereitstellung für Autor |
| 2 | Zum Testen pausieren | - |
| 3 | Grün-Infrastruktur erstellt | - |
| 4 | Bereitstellung auf grüne Veröffentlichungs-/Dispatcher-Ebenen | Bereitstellung für Veröffentlichung |
| 5 | Zum Testen pausieren (bis zu 24 Stunden) | - |
| 6 | Die grüne Infrastruktur wird zum Produktionslastenausgleich hinzugefügt. | – |
| 7 | Blaue Infrastruktur wird aus dem Produktionslastenausgleich entfernt | – |
| 8 | Pause für die endgültige Abmeldung (bis zu 24 Stunden) | - |
| 9 | Blaue Infrastruktur wird automatisch beendet | - |
| 10 | Pipeline ist abgeschlossen | - |

#### Implementieren von Blau/Grün {#implementing}

Alle AMS-Benutzenden, die Cloud Manager für Produktionsimplementierungen verwenden, können eine Blau/Grün-Implementierung verwenden. Die Verwendung einer Blau/Grün-Implementierung erfordert jedoch eine zusätzliche Validierung Ihrer Umgebungen und die Einrichtung durch einen Adobe CSE.

Wenn Sie an einer Blau/Grün-Bereitstellung interessiert sind, beachten Sie die folgenden Anforderungen und Einschränkungen und wenden Sie sich an Ihr CSE-Team.

#### Anforderungen und Einschränkungen {#limitations}

* Blau/Grün ist nur für Dispatcher/Veröffentlichungspaare verfügbar.
* Vorschau-Dispatcher-/Veröffentlichungs-Paare sind nicht Teil von Blau/Grün-Bereitstellungen.
* Jedes Dispatcher-/Veröffentlichungspaar ist mit jedem anderen Dispatcher-/Veröffentlichungspaar identisch.
* Blau/Grün ist nur in der Produktionsumgebung verfügbar.
* Blau/Grün ist in AWS sowie in Azure verfügbar.
* Blau/Grün steht nur Kundinnen und Kunden von Assets zur Verfügung.
