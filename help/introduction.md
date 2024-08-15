---
title: Einführung in Cloud Manager für AMS
description: Hier erfahren Sie mehr über Cloud Manager für Adobe Managed Services (AMS) und darüber, wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.
exl-id: 58344d8a-b869-4177-a9cf-6a8b7dfe9588
source-git-commit: 4c4a2688cab8e5c81efa4b7b5e26f3c7b5dc30d6
workflow-type: tm+mt
source-wordcount: '1256'
ht-degree: 49%

---


# Einführung in [!UICONTROL Cloud Manager] für AMS {#introduction-to-cloud-manager}

Hier erfahren Sie mehr über Cloud Manager für AMS (Adobe Managed Services) und wie Unternehmen Adobe Experience Manager in der Cloud selbst verwalten können.

>[!CONTEXTUALHELP]
>id="aemcloud_cloudmanager_introduction"
>title="Einführung in Cloud Manager für AMS"
>abstract="Ermöglicht Organisationen die Selbstverwaltung von Adobe Experience Manager in der Cloud. Das umfasst ein Framework für die fortlaufende Integration und Bereitstellung (CI/CD), mit dem IT-Teams und Implementierungspartner die Bereitstellung von Anpassungen oder Aktualisierungen beschleunigen können, ohne die Leistung oder Sicherheit zu beeinträchtigen."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/programs#cloud-manager" text="Programme erstellen"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/cloud-manager/environments#cloud-manager" text="Umgebungen erstellen"

## Einführung {#introduction}

[!UICONTROL Cloud Manager] für Adobe Experience Manager bietet Entwicklern die Möglichkeit, durch optimierte Workflows, die auf Best Practices von Adobe Experience Manager basieren, überzeugende Kundenerlebnisse zu erstellen. CI/CD-Pipelines, die für Adobe Experience Manager optimiert sind, ermöglichen das einfache Zusammenführen von Entwicklungs-Workflows, indem Sie einfach Ihren Code einchecken, der dann den ganzen Weg bis zur Produktionsbereitschaft ebnet. Während der Build-Phase werden Ihre benutzerdefinierten Code-Updates gründlich anhand von Best Practices getestet, sodass Sie zuverlässige Programme für Ihre Kunden bereitstellen. Cloud Manager arbeitet mit offenen APIs und ermöglicht Ihnen die Integration mit Ihren Systemen, ohne bestehende Prozesse und Tools zu stören.

>[!NOTE]
>
>Auf dieser Dokumentations-Website werden speziell die Funktionen von Cloud Manager beschrieben, die für Kunden von Adobe Managed Services (AMS) relevant sind.
>
>Die entsprechende Dokumentation für AEM as a Cloud Service finden Sie in der [AEM as a Cloud Service-Dokumentation](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/home).

Mit Cloud Manager profitiert Ihr Entwicklungs-Team von den folgenden Funktionen:

* Kontinuierliche Integration/kontinuierliche Bereitstellung (CI/CD) von Code zur Verkürzung der Markteinführungszeit von Monaten/Wochen auf Tage/Stunden.

* Codeüberprüfung, Leistungstests und Sicherheitsvalidierung basierend auf Best Practices, bevor sie an die Produktion gesendet werden, um Produktionsunterbrechungen zu minimieren.

* API-Konnektivität zur Ergänzung vorhandener DevOps-Prozesse.

* Automatische Skalierung, die intelligent erkennt, dass eine höhere Kapazität erforderlich ist, und automatisch zusätzliche Dispatcher-/Veröffentlichungssegmente online stellt.

![CI/CD-Ablauf](/help/assets/screen_shot_2018-05-12at73843pm.png)Der CI/CD-Prozessablauf, der in [!UICONTROL Cloud Manager] verwendet wird.

## Wichtige Funktionen in [!UICONTROL Cloud Manager] {#key-features-in-cloud-manager}

Im Folgenden werden ausgewählte Funktionen von Cloud Manager genauer erläutert.

### Self-Service-Benutzeroberfläche {#self-service-interface}

Die Benutzeroberfläche für [!UICONTROL Cloud Manager] ermöglicht Ihnen den einfachen Zugriff auf und die Verwaltung der Cloud-Umgebung sowie der CI/CD-Pipeline für Ihre Adobe Experience Manager-Anwendungen.

Sie definieren anwendungsspezifische KPIs (Key Performance Indicators) wie Spitzenwerte für Seitenansichten pro Minute oder erwartete Seitenladereaktionszeiten. Diese KPIs dienen als Grundlage für die Messung des Implementierungserfolgs. Rollen und Berechtigungen für verschiedene Team-Mitglieder können einfach definiert werden. Die Self-Service-Oberfläche bietet Ihnen volle Kontrolle. Es bietet auch Links zu Best Practice-Ressourcen und Zugang zu Adobe-Experten, um bei Bedarf Orientierungshilfen zu erhalten.

Weitere Informationen zur Benutzeroberfläche von [!UICONTROL Cloud Manager] und zu den ersten Schritten finden Sie unter [Erste Anmeldung](/help/getting-started/first-time-login.md).

### CI/CD-Pipeline {#ci-cd-pipeline}

Eine der Hauptfunktionen von [!UICONTROL Cloud Manager] ist die Möglichkeit, eine optimierte CI/CD-Pipeline einzurichten, um die Bereitstellung von benutzerspezifischem Code oder Aktualisierungen (z. B. hinzugefügte neue Website-Komponenten) zu beschleunigen.

Über die [!UICONTROL Cloud Manager]-Benutzeroberfläche können Sie CI/CD-Pipelines konfigurieren und starten. Im Rahmen dieser Pipeline wird ein gründlicher Codescan durchgeführt, um sicherzustellen, dass nur hochwertige Programme in die Produktionsumgebung übertragen werden.

Weitere Informationen zum Konfigurieren der Pipeline über die Benutzeroberfläche von [!UICONTROL Cloud Manager] finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md).

### Flexible Bereitstellungsmodi {#flexible-deployment-modes}

[!UICONTROL Cloud Manager] bietet flexible und konfigurierbare Bereitstellungsmodi, damit Erlebnisse entsprechend den sich ändernden Geschäftsanforderungen bereitgestellt werden können.

Im automatischen Auslösermodus wird der Code basierend auf bestimmten Ereignissen (z. B. einem Code-Commit) automatisch in einer Umgebung bereitgestellt. Sie können Code-Breitstellungen auch innerhalb bestimmter Zeitrahmen (auch außerhalb der Geschäftszeiten) planen.

Unabhängig vom Bereitstellungsauslöser werden bei einer CI/CD-Pipeline-Ausführung immer Qualitätsprüfungen durchgeführt. Das gilt für jede ausgelöste Bereitstellung. Zu den Qualitätsprüfungen gehören Codeprüfungen, Sicherheitstests und Leistungstests, die alle sofort und ohne Aufwand von Ihnen oder Ihren Partnern bereitgestellt werden.

Weitere Informationen zur Bereitstellung von Code und Qualitätsprüfungen finden Sie unter [Bereitstellen von Code](/help/using/code-deployment.md).

## Optionale Funktionen in Cloud Manager {#optional-features-in-cloud-manager}

Cloud Manager bietet zusätzliche, erweiterte Funktionen, die je nach Umgebungseinrichtung und Anforderungen für Ihr Projekt von Vorteil sein können. Wenn diese Funktionen für Sie von Interesse sind, wenden Sie sich an Ihren Customer Success Engineer (CSE) oder Adobe-Support-Mitarbeiter, um weitere Informationen zu erhalten.

### Automatische Skalierung {#autoscaling}

Wenn die Produktionsumgebung ungewöhnlich stark ausgelastet ist, erkennt [!UICONTROL Cloud Manager] den Bedarf an zusätzlicher Kapazität und stellt mit seiner Funktion zur automatischen Skalierung automatisch zusätzliche Kapazität online bereit.

In einem solchen Fall löst [!UICONTROL Cloud Manager] automatisch die Skalierung aus, sendet eine Benachrichtigung über die automatische Skalierung und macht die zusätzliche Kapazität innerhalb von Minuten online verfügbar. Die zusätzliche Kapazität wird in der Produktionsumgebung in denselben Regionen bereitgestellt und entspricht den Systemspezifikationen der laufenden Dispatcher-/Veröffentlichungsknoten.

Die Funktion zur automatischen Skalierung gilt für die Dispatcher-/Veröffentlichungsstufe, wobei die horizontale Skalierung verwendet wird, um ein bis zehn Segmente von Dispatcher-/Veröffentlichungspaaren hinzuzufügen. Jede zusätzliche bereitgestellte Kapazität wird innerhalb von zehn Werktagen manuell skaliert, wie vom Adobe CSE (Customer Success Engineer) bestimmt.

>[!NOTE]
>
>Wenn Sie herausfinden möchten, ob die automatische Skalierung für Ihre Anwendung geeignet ist, wenden Sie sich an Ihren CSE oder Adobe-Support-Mitarbeiter.

### Blau/Grün-Implementierungen {#blue-green}

Eine Blau/Grün-Bereitstellung ist eine Technik, die Ausfallzeiten und Risiken reduziert, indem zwei identische Produktionsumgebungen namens „Blau“ und „Grün“ ausgeführt werden.

Es ist immer nur eine der Umgebungen aktiv, wobei der gesamte Produktions-Traffic über die Live-Umgebung läuft. Generell ist Blau die derzeit aktive Umgebung und Grün ist inaktiv.

* Eine Blau/Grün-Implementierung ist ein Add-on zu CI/CD-Pipelines von Cloud Manager, bei der ein zweiter Satz an Publishing- und Dispatcher-Instanzen (grün) erstellt und für Bereitstellungen verwendet wird. Die grünen Instanzen werden dann an den Produktionslastausgleich angehängt und die alten Instanzen (blau) werden entfernt und beendet.
* Diese Implementierung von Blau/Grün behandelt Instanzen als transient und jede Iteration einer blauen/grünen Pipeline erstellt einen neuen Satz von Veröffentlichungs- und Dispatcher-Servern.
* Im Rahmen des Setups wird ein grüner Lastenausgleich erstellt. Dieser Lastenausgleich ändert sich nie und sollte auf Ihre grüne oder &quot;Test&quot;-URL verweisen.
* Bei einer blauen/grünen Implementierung wird eine exakte Replikation der vorhandenen Dispatcher-/Veröffentlichungsstufen erstellt.

#### Blau/Grün-Implementierungsfluss {#flow}

Wenn die Blau/Grün-Implementierung aktiviert ist, unterscheidet sich der Bereitstellungsfluss vom standardmäßigen Cloud-Service-Bereitstellungsfluss.

| Schritt | Blau/Grün-Bereitstellung | Standard-Bereitstellung |
|---|---|---|
| 1 | Bereitstellung für Autor | Bereitstellung für Autor |
| 2 | Zum Testen pausieren | - |
| 3 | Grün-Infrastruktur erstellt | - |
| 4 | Bereitstellung in grüne Veröffentlichungs-/Dispatcher-Ebenen | Bereitstellung für Veröffentlichung |
| 5 | Zum Testen pausieren (bis zu 24 Stunden) | - |
| 6 | Die grüne Infrastruktur wird zum Produktionslastenausgleich hinzugefügt. | - |
| 7 | Die blaue Infrastruktur wird aus dem Produktionslastenausgleich entfernt. |
| 8 | Pause für die endgültige Abmeldung (bis zu 24 Stunden) | - |
| 9 | Blaue Infrastruktur wird automatisch beendet | - |
| 10 | Pipeline ist abgeschlossen | - |

#### Blau/Grün implementieren {#implementing}

Alle AMS-Benutzer, die Cloud Manager für Produktionsbereitstellungen verwenden, können die blaue/grüne Implementierung verwenden. Die Verwendung einer blauen/grünen Implementierung erfordert jedoch eine zusätzliche Validierung Ihrer Umgebungen und die Einrichtung durch einen Adobe CSE.

Wenn Sie an einer blauen/grünen Implementierung interessiert sind, beachten Sie die folgenden Anforderungen und Einschränkungen und kontaktieren Sie Ihren CSE.

#### Anforderungen und Einschränkungen {#limitations}

* Blau/Grün ist nur für Dispatcher-/Publisher-Paare verfügbar.
* Vorschau-Dispatcher-/Veröffentlichungs-Paare sind nicht Teil von Blau/Grün-Bereitstellungen.
* Jedes Dispatcher/Veröffentlichungspaar ist mit jedem anderen Dispatcher/Publisher-Paar identisch.
* Blau/Grün ist nur in der Produktionsumgebung verfügbar.
* Blau/Grün ist in AWS und Azure verfügbar.
* Blau/Grün steht nur Assets-Kunden zur Verfügung.
