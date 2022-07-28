---
title: Einführung in Cloud Manager für AMS
description: Hier erfahren Sie mehr über Cloud Manager für Adobe Managed Services (AMS) und darüber, wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 14e35882765783b234ca35da14257279af5130a0
workflow-type: tm+mt
source-wordcount: '1311'
ht-degree: 16%

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
>Die entsprechende Dokumentation für AEM as a Cloud Service finden Sie im [AEM as a Cloud Service Dokumentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/home.html)

Mit Cloud Manager profitiert Ihr Entwicklungsteam von den folgenden Funktionen:

* Kontinuierliche Integration/kontinuierliche Bereitstellung (CI/CD) von Code zur Verkürzung der Markteinführungszeit von Monaten/Wochen auf Tage/Stunden

* Codeüberprüfung, Leistungstests und Sicherheitsvalidierung basierend auf Best Practices, bevor sie an die Produktion gesendet werden, um Produktionsunterbrechungen zu minimieren

* API-Konnektivität zur Ergänzung vorhandener DevOps-Prozesse

* Automatische Skalierung, die intelligent erkennt, dass eine höhere Kapazität erforderlich ist, und automatisch zusätzliche Dispatcher-/Publishing-Segmente online stellt

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

## Optionale Funktionen in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager bietet zusätzliche erweiterte Funktionen, die je nach Einrichtung und Anforderungen Ihrer Umgebung für Ihr Projekt von Vorteil sein können. Wenn diese Funktionen für Sie von Interesse sind, wenden Sie sich an Ihren Customer Success Engineer (CSE) oder an einen Adobe Support-Mitarbeiter, um weitere Informationen zu erhalten.

### Automatische Skalierung {#autoscaling}

Wenn die Produktionsumgebung ungewöhnlich stark ausgelastet ist, [!UICONTROL Cloud Manager] erkennt den Bedarf an zusätzlicher Kapazität und bringt automatisch zusätzliche Kapazität über seine Funktion zur automatischen Skalierung online.

In einem solchen Fall [!UICONTROL Cloud Manager] automatisch den automatischen Skalierungs-Bereitstellungsprozess Trigger, eine Benachrichtigung über die automatische Skalierung sendet und innerhalb von Minuten zusätzliche Kapazitäten verfügbar macht. Die zusätzliche Kapazität wird in der Produktionsumgebung bereitgestellt, in denselben Regionen und entsprechend den Systemspezifikationen wie die laufenden Dispatcher-/Veröffentlichungsknoten.

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
