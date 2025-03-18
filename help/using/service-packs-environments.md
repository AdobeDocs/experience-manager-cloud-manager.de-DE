---
title: Service Pack-Aktualisierungen für Entwicklungsumgebungen - Early Adopter
description: Erfahren Sie, wie Sie jetzt Service Pack-Aktualisierungen für Entwicklungsumgebungen über die Benutzeroberfläche von Cloud Manager initiieren können.
exl-id: 996a8eee-843f-45a6-8f7a-31ea405c2b32
source-git-commit: 91691878a2c135cc9fe123c06afcf775a962a2e0
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# Service Pack-Aktualisierungen für Entwicklungsumgebungen (Early Adopter) {#stage-prod-only}

Erfahren Sie, wie Sie über die Benutzeroberfläche von Cloud Manager Service Pack-Aktualisierungen für Entwicklungsumgebungen initiieren können.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/release-notes/current.md#early-adoption) verfügbar.

## Übersicht {#service-pack-updates-overview}

Sie können Service Pack-Aktualisierungen für Entwicklungsumgebungen über die Benutzeroberfläche von Cloud Manager initiieren. Mit dieser Funktion können Sie nach verfügbaren Service Pack-Updates suchen und den Installationsprozess unabhängig verwalten.

**Die wichtigsten Vorteile**

* Bietet mehr Kontrolle über Aktualisierungen des Cloud Manager Service Packs.
* Verringert die Abhängigkeit von Adobe Customer Success Engineers (CSEs) beim Initiieren von Aktualisierungen.
* Verfolgt den gesamten Aktualisierungsprozess über Cloud Manager.

**Aktuelle Einschränkungen**

* Die Option „Self-Service-Update“ ist nur für Entwicklungsumgebungen verfügbar.
* Für fehlgeschlagene Aktualisierungen ist eine begrenzte Fehlerberichterstattung verfügbar.
* Wenn Probleme auftreten, müssen Sie sich zur weiteren Untersuchung an die CSEs von Adobe wenden.

## Starten einer Service Pack-Aktualisierung

1. Melden Sie sich bei Cloud Manager mit Berechtigungen als Bereitstellungs-Manager an.
1. Navigieren Sie zur Seite Programmübersicht .
1. Klicken Sie im Abschnitt Umgebungen auf ![Mehr-Symbol, Auslassungspunkte](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

   ![Suchen Sie im Dropdown-Menü nach Service Pack-Aktualisierung](/help/using/assets/service-pack-check-for-updates.png)

1. Klicken Sie im Dropdown-Menü auf ![Symbol „In Licht öffnen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_OpenInLight_18_N.svg) **Nach Updates suchen**, um nach verfügbaren Service Pack-Updates zu suchen.

   ![Eine Liste der verfügbaren Aktualisierungen wird angezeigt, die verfügbar sind](/help/using/assets/service-pack-versions.png)

1. Klicken Sie in der Liste auf die gewünschte Service Pack-Version.
1. Klicken Sie auf **Service Pack aktualisieren**, um den Aktualisierungsprozess zu starten.
1. Überprüfen Sie im Bestätigungsdialogfeld die Details und bestätigen Sie die Aktualisierung.

   Nach der Bestätigung wird der Installationsprozess gestartet, und der Fortschritt kann in Cloud Manager verfolgt werden.

## Verfolgen der Service Pack-Aktualisierung

Nach Initiierung des Updates können Sie den Fortschritt auf der Aktivitätsseite von Cloud Manager überwachen.

**So verfolgen Sie die Aktualisierung des Service Packs:**

1. Navigieren Sie vom Cloud Manager-Dashboard zur Aktivitätsseite .
1. Suchen Sie nach dem Eintrag Service Pack-Installation .

   ![Service Pack-Installationen](/help/using/assets/service-pack-installation.png)

1. Klicken Sie auf den Eintrag, um detaillierte Fortschritts- und Statusaktualisierungen ähnlich den folgenden anzuzeigen:

   ![Fortschritt der Service Pack-Installation](/help/using/assets/service-pack-progression.png)

### Fehlerbehebung bei Installationsfehlern

* Wenn die Installation fehlschlägt, wird in Cloud Manager automatisch ein Rollback zum vorherigen Status Trigger.
* Wenn das Problem weiterhin besteht **klicken Sie auf „Protokoll herunterladen**, um Fehlerprotokolle zu erfassen. Wenden Sie sich dann zur Fehlerbehebung an den Adobe-Support.

## Ausführung des Service Packs genehmigen oder ablehnen

Nach Abschluss der Installation ist Ihre Genehmigung - oder Ablehnung - erforderlich, um die Aktualisierung abzuschließen.

**So genehmigen Sie die Ausführung des Service Packs oder lehnen sie ab:**

1. Öffnen Sie die Aktivitätsseite in Cloud Manager.
1. Suchen Sie die ausstehende Genehmigungsanfrage für die Aktualisierung des Service Packs.

   ![Die Aktualisierung des Service Packs ablehnen oder genehmigen](/help/using/assets/service-pack-reject-approve.png)

1. Führen Sie eine der folgenden Aktionen aus:

   * Um die Aktualisierung abzuschließen, klicken Sie auf **Genehmigen**.

   ![Genehmigung des Service Packs](/help/using/assets/service-pack-approve.png)

   * Um die Aktualisierung abzubrechen, klicken Sie auf **Ablehnen**.
Die Installation des Service Packs wird abgebrochen, und es werden keine Änderungen angewendet.

   ![Ablehnung des Service Packs](/help/using/assets/service-pack-reject.png)
