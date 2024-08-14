---
title: Versionshinweise für Cloud Manager 2024.8.0
description: Informationen zu den Versionshinweisen für Cloud Manager 2024.8.0.
feature: Release Information
source-git-commit: 34f15aff7478a6a0884f88f534a7dff996a8570e
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 5%

---


# Versionshinweise für Cloud Manager 2024.8.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für [!UICONTROL Cloud Manager] 2024.8.0.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Cloud Manager in den aktuellen Versionshinweisen zu AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Veröffentlichungsdatum {#release-date}

Die Version von [!UICONTROL Cloud Manager] 2024.8.0 wurde am 13. August 2024 veröffentlicht. Die nächste Version wird am 9. September 2021 veröffentlicht.

## Neuerungen {#what-is-new}

* Für reine Staging- und reine Produktions-Pipelines (verfügbar als Bestandteil des [frühen Adopter-Programms](#staging-production-only-pipelines)) können Sie sie jetzt im [Notmodus ausführen, ](/help/using/stage-prod-only.md#emergency-mode) Staging-Tests überspringen.

## Frühzeitige Annahme {#early-adoption}

Nehmen Sie an Adobe teil und haben Sie die Möglichkeit, einige bevorstehende Funktionen zu testen.

### Nur-Staging- und reine Produktionslinien {#staging-production-only-pipelines}

Adobe freut sich, die Einführung der Unterstützung für [reine Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) anzukündigen. Mit dieser neuen Funktion können Sie produktionsbezogene Pipelines in kleinere, speziellere Implementierungen unterteilen.

Wenn Sie diese Funktion testen und Feedback geben möchten, senden Sie eine E-Mail an `Grp-cloudmanager_splitpipelines@adobe.com` und verwenden Sie dabei die E-Mail-Adresse, die Ihrer Adobe ID zugeordnet ist.

## Fehlerbehebungen

* Ein seltenes Problem wurde behoben, bei dem Pipeline-Schritte nach dem Löschen der Pipeline ausgeführt wurden.
* Die erneute Ausführung der Pipeline funktioniert jetzt beim ersten Versuch und behebt ein seltenes Problem, bei dem eine Wiederholung mehrmals gestartet werden musste.
* Geplante Implementierungsschritte für Vollstapel-Pipelines berücksichtigen jetzt das ausgewählte geplante Datum und kehren nicht auf **Jetzt** zurück.
* Die Status von fehlgeschlagenen Inhaltsaufgaben für das Kopieren werden jetzt korrekt angezeigt und zeigen in seltenen Fällen nicht mehr fälschlicherweise den Status &quot;`In Progress`&quot; an.

## Bekannte Probleme {#known-issues}

{{content-copy-known-issues}}
