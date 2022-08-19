---
title: Einführung in Cloud Manager für AMS
description: Hier erfahren Sie mehr über Cloud Manager für Adobe Managed Services (AMS) und darüber, wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 14e35882765783b234ca35da14257279af5130a0
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 57%

---


# Einführung in [!UICONTROL Cloud Manager] für AMS {#introduction-to-cloud-manager}

Hier erfahren Sie mehr über Cloud Manager für Adobe Managed Services (AMS) und darüber, wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Einführung in Cloud Manager für AMS"
>abstract="Ermöglicht Organisationen die Selbstverwaltung von Adobe Experience Manager in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de#cloud-manager" text="Programme erstellen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de#cloud-manager" text="Umgebungen erstellen"

## Einführung {#introduction}

[!UICONTROL Cloud Manager] für Adobe Experience Manager bietet Entwicklern die Möglichkeit, durch optimierte Workflows, die auf Best Practices von Adobe Experience Manager basieren, überzeugende Kundenerlebnisse zu erstellen. Für Adobe Experience Manager optimierte CI/CD-Pipelines ermöglichen es Ihnen, Entwicklungs-Workflows einfach zusammenzuführen, indem Sie Ihren Code einchecken und bis zur Produktionsbereitschaft führen. Während der Build-Phase werden Ihre benutzerdefinierten Code-Updates gründlich anhand von Best Practices getestet, sodass Sie zuverlässige Programme für Ihre Kunden bereitstellen. Cloud Manager arbeitet mit offenen APIs und ermöglicht Ihnen die Integration mit Ihren Systemen, ohne bestehende Prozesse und Tools zu stören.

>[!NOTE]
>
>Auf dieser Dokumentations-Website werden speziell die Funktionen von Cloud Manager beschrieben, die für Kunden von Adobe Managed Services (AMS) relevant sind.
>
>Die entsprechende Dokumentation für AEM as a Cloud Service finden Sie in der [Dokumentation zu AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html).

Mit Cloud Manager profitiert Ihr Entwicklungs-Team von den folgenden Funktionen:

* Kontinuierliche Integration/Bereitstellung (CI/CD, Continuous Integration/Continuous Delivery) von Code zur Verkürzung der Markteinführungszeit von Monaten/Wochen auf Tage/Stunden

* Code-Prüfungen, Leistungstests und Sicherheitsprüfungen basierend auf Best Practices, bevor der Code an die Produktion gesendet wird, um Produktionsunterbrechungen zu minimieren

* API-Konnektivität zur Ergänzung vorhandener DevOps-Prozesse

* Automatische Skalierung, die intelligent erkennt, dass eine höhere Kapazität erforderlich ist, und automatisch zusätzliche Dispatcher-/Publishing-Segmente online stellt

Die folgende Abbildung zeigt den CI/CD-Prozessfluss, wie er in [!UICONTROL Cloud Manager] verwendet wird:

![CI/CD-Fluss](/help/assets/screen_shot_2018-05-12at73843pm.png)

## Wichtige Funktionen in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Im Folgenden werden ausgewählte Funktionen von Cloud Manager genauer erläutert.

### Self-Service-Benutzeroberfläche {#self-service-interface}

Die [!UICONTROL Cloud Manager]-Benutzeroberfläche ermöglicht den einfachen Zugriff und die Verwaltung der Cloud-Umgebung sowie der CI/CD-Pipeline für Adobe Experience Manager-Programme.

Man definiert programmspezifische wichtige Leistungskennzahlen (Key Performance Indicators, KPIs) (z. B. maximale Seitenaufrufe pro Minute und erwartete Antwortzeit beim Laden einer Seite), die die Grundlage für die Messung einer erfolgreichen Bereitstellung bilden. Rollen und Berechtigungen für verschiedene Team-Mitglieder können einfach definiert werden. Die Self-Service-Benutzeroberfläche gibt Ihnen nicht nur die volle Kontrolle, sondern bietet außerdem Links zu Best Practices und Zugang zu Experten von Adobe, die bei Bedarf die erforderliche Anleitung zur Verfügung stellen.

Weitere Informationen zur Benutzeroberfläche von [!UICONTROL Cloud Manager] und zu den ersten Schritten finden Sie unter [Erste Anmeldung](/help/getting-started/first-time-login.md).

### CI/CD-Pipeline {#ci-cd-pipeline}

Eine der Hauptfunktionen von [!UICONTROL Cloud Manager] ist die Möglichkeit, eine optimierte CI/CD-Pipeline einzurichten, um die Bereitstellung von benutzerspezifischem Code oder Aktualisierungen (z. B. hinzugefügte neue Website-Komponenten) zu beschleunigen.

Über die [!UICONTROL Cloud Manager]-Benutzeroberfläche können Sie CI/CD-Pipelines konfigurieren und starten. Im Rahmen dieser Pipeline wird ein gründlicher Codescan durchgeführt, um sicherzustellen, dass nur hochwertige Programme in die Produktionsumgebung übertragen werden.

Weitere Informationen zum Konfigurieren der Pipeline in der Benutzeroberfläche von [!UICONTROL Cloud Manager] finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/using/non-production-pipelines.md).

### Flexible Bereitstellungsmodi {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] bietet flexible und konfigurierbare Bereitstellungsmodi, damit Erlebnisse entsprechend den sich ändernden Geschäftsanforderungen bereitgestellt werden können.

Im automatischen Auslösermodus wird der Code basierend auf bestimmten Ereignissen (z. B. einem Code-Commit) automatisch in einer Umgebung bereitgestellt. Sie können Code-Breitstellungen auch innerhalb bestimmter Zeitrahmen (auch außerhalb der Geschäftszeiten) planen.

Unabhängig vom Bereitstellungsauslöser werden bei einer CI/CD-Pipeline-Ausführung immer Qualitätsprüfungen durchgeführt. Das gilt für jede ausgelöste Bereitstellung. Zu den Qualitätsprüfungen gehören vorkonfigurierte Code-Prüfungen, Sicherheitstests und Leistungstests, die ohne Aufwand von Ihnen oder Ihren Partnern genutzt werden können.

Weitere Informationen zum Bereitstellen von Code und zu Qualitätsprüfungen finden Sie unter [Bereitstellen von Code](/help/using/code-deployment.md).

## Optionale Funktionen in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager bietet zusätzliche erweiterte Funktionen, die je nach Einrichtung und Anforderungen Ihrer Umgebung für Ihr Projekt von Vorteil sein können. Wenn diese Funktionen für Sie von Interesse sind, wenden Sie sich an Ihren Customer Success Engineer (CSE) oder an einen Adobe Support-Mitarbeiter, um weitere Informationen zu erhalten.

### Automatische Skalierung {#autoscaling}

Wenn die Produktionsumgebung ungewöhnlich stark ausgelastet ist, [!UICONTROL Cloud Manager] erkennt den Bedarf an zusätzlicher Kapazität und bringt automatisch zusätzliche Kapazität über seine Funktion zur automatischen Skalierung online.

In einem solchen Fall löst [!UICONTROL Cloud Manager] automatisch die Skalierung aus, sendet eine Benachrichtigung über die automatische Skalierung und schaltet die zusätzliche Kapazität innerhalb von Minuten aktiv. Die zusätzliche Kapazität wird in der Produktionsumgebung bereitgestellt, in denselben Regionen und entsprechend den Systemspezifikationen wie die laufenden Dispatcher-/Veröffentlichungsknoten.

Die Funktion zur automatischen Skalierung gilt nur für die Dispatcher-/Veröffentlichungsstufe und wird mit einer horizontalen Skalierungsmethode ausgeführt, wobei mindestens ein zusätzliches Segment eines Dispatcher-/Publishing-Paares bis zu maximal zehn Segmenten verwendet wird. Jede zusätzlich bereitgestellte Kapazität wird innerhalb von zehn Arbeitstagen, wie vom CSE (Customer Success Engineer) bestimmt, manuell zurückgenommen.

>[!NOTE]
>
>Wenn Sie herausfinden möchten, ob die automatische Skalierung für Ihre Anwendung geeignet ist, wenden Sie sich an Ihren CSE oder einen Adobe-Support-Mitarbeiter.

### Blau/Grün-Implementierungen {#blue-green}

Eine Blau/Grün-Implementierung ist eine Technik, die Ausfallzeiten und Risiken reduziert, indem zwei identische Produktionsumgebungen namens Blau und Grün ausgeführt werden.

Es ist immer nur eine der Umgebungen aktiv, wobei die Live-Umgebung den gesamten Produktions-Traffic bereitstellt. Im Allgemeinen ist Blau die derzeit aktive Umgebung und Grün ist inaktiv.

* Eine blaue/grüne Implementierung ist ein Add-on zu CI/CD-Pipelines von Cloud Manager, in dem eine zweite Reihe von Veröffentlichungs- und Dispatcher-Instanzen (grün) erstellt und für Bereitstellungen verwendet wird. Die grünen Instanzen werden dann an den Produktionslastausgleich angehängt und die alten Instanzen (blau) werden entfernt und beendet.
* Diese Implementierung von blau/grün behandelt Instanzen als transient und jede Iteration einer blauen/grünen Pipeline erstellt einen neuen Satz von Veröffentlichungs- und Dispatcher-Servern.
* Im Rahmen der Einrichtung wird ein grüner Lastenausgleich erstellt. Dieser Lastenausgleich ändert sich nie und sollte auf Ihre grüne oder &quot;Test&quot;-URL verweisen.
* Bei einer blauen/grünen Implementierung wird eine exakte Replikation der vorhandenen Veröffentlichungs-/Dispatcher-Ebenen erstellt.

#### Blau/Grün-Implementierungsfluss {#flow}

Wenn die Blau/Grün-Implementierung aktiviert ist, unterscheidet sich der Bereitstellungsfluss vom standardmäßigen Cloud Service-Bereitstellungsfluss.

| Schritt | Blau/Grün-Implementierung | Standardbereitstellung |
|---|---|---|
| 1 | Bereitstellung für Autor | Bereitstellung für Autor |
| 2 | Testen pausieren | - |
| 3 | Grüne Infrastruktur geschaffen | - |
| 4 | Implementierung in grüne Veröffentlichungs-/Dispatcher-Ebenen | Bereitstellung für Publisher |
| 5 | Anhalten für Tests (bis zu 24 Stunden) | - |
| 6 | Die grüne Infrastruktur wird zum Produktionslastausgleich hinzugefügt | - |
| 7 | Die blaue Infrastruktur wird aus dem Produktionslastausgleich entfernt. |
| 8 | Blaue Infrastruktur wird automatisch beendet | - |

#### Implementieren von Blau/Grün {#implementing}

Alle AMS-Benutzer, die Cloud Manager für Produktionsbereitstellungen verwenden, können eine blaue/grüne Implementierung verwenden. Die Verwendung einer blauen/grünen Implementierung erfordert jedoch eine zusätzliche Validierung Ihrer Umgebungen und die Einrichtung durch einen Adobe-CSE.

Wenn Sie an einer blauen/grünen Implementierung interessiert sind, beachten Sie die folgenden Anforderungen und Einschränkungen und kontaktieren Sie Ihren CSE.

#### Anforderungen und Einschränkungen {#limitations}

* Blau/Grün ist nur für Veröffentlichungs-/Dispatcher-Paare verfügbar.
* Vorschau-Dispatcher-/Veröffentlichungspaare sind nicht Teil von blauen/grünen Implementierungen.
* Jedes Dispatcher-/Veröffentlichungspaar ist mit jedem anderen Dispatcher-/Veröffentlichungspaar identisch.
* Blau/Grün ist nur in der Produktionsumgebung verfügbar.
* Blau/Grün ist in AWS sowie Azure verfügbar.
* Blau/Grün steht nur Kunden von Assets zur Verfügung.
