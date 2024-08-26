---
title: Versionshinweise für Cloud Manager 2024.8.0
description: Dies sind die Versionshinweise für Cloud Manager 2024.8.0.
feature: Release Information
source-git-commit: 5ced643fabe0a670e456cbea72f9da8196ac774a
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 28%

---


# Versionshinweise für Cloud Manager 2024.8.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] 2024.8.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Cloud Manager in den aktuellen Versionshinweisen zu AEM as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2024.8.0 ist der Donnerstag, 14. August 2024. Die nächste Version ist für den 14. September 2024 geplant.

## Neuerungen {#what-is-new}

* Für reine Staging- und reine Produktions-Pipelines (verfügbar als Bestandteil des [frühen Adopter-Programms](#staging-production-only-pipelines)) können Sie sie jetzt im [Notmodus ausführen, ](/help/using/stage-prod-only.md#emergency-mode) Staging-Tests überspringen.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Cloud Manager-Programm teil und haben Sie die Möglichkeit, einige bevorstehende Funktionen zu testen.

### Nur-Staging- und reine Produktionslinien {#staging-production-only-pipelines}

Adobe freut sich, die Einführung der Unterstützung für [reine Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) anzukündigen. Mit dieser neuen Funktion können Sie produktionsbezogene Pipelines in kleinere, speziellere Implementierungen unterteilen.

Wenn Sie diese Funktion testen und Feedback geben möchten, senden Sie eine E-Mail an `Grp-cloudmanager_splitpipelines@adobe.com` und verwenden Sie dabei die E-Mail-Adresse, die Ihrer Adobe ID zugeordnet ist.

## Fehlerbehebungen

* Ein seltenes Problem wurde behoben, durch das Pipeline-Schritte nach dem Löschen der Pipeline ausgeführt wurden.
* Die erneute Ausführung der Pipeline funktioniert jetzt beim ersten Versuch und behebt ein seltenes Problem, bei dem eine Wiederholung mehrmals gestartet werden musste.
* Geplante Implementierungsschritte für Vollstapel-Pipelines berücksichtigen jetzt das ausgewählte geplante Datum und kehren nicht auf **Jetzt** zurück.
* Die Status von fehlgeschlagenen Inhaltsaufgaben für das Kopieren werden jetzt korrekt angezeigt und zeigen in seltenen Fällen nicht mehr fälschlicherweise den Status &quot;`In Progress`&quot; an.

## Bekannte Probleme {#known-issues}

{{content-copy-known-issues}}
