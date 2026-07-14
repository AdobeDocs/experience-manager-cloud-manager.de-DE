---
title: Einrichten von Programmen
description: Nach dem Onbarding muss die Geschäftsinhaberin bzw. der Geschäftsinhaber verschiedene Ersteinstellungen am Programm vornehmen.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
TQID: https://experienceleague.adobe.com/AqaA4GSOptV11h2y4V1Mt15KmEhEYBaiM-RvBFjtfWY
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 65%

---

# Einrichten von Programmen {#program-setup}

Nach dem Onboarding richtet der Business Lead das Programm ein, indem er eine Beschreibung hinzufügt und Key Performance Indicators (KPIs) definiert. Diese KPIs werden dann für Leistungstests verwendet.

## Einrichten von Programmen mit [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf **Programm einrichten**, um den Einrichtungsprozess zu starten.

   ![Programm einrichten](/help/assets/set-up-program/setup1.png)

1. Im Dialogfeld **Programm einrichten** können Sie auf drei Registerkarten Informationen zum Programm eingeben:

   * **Allgemein**
   * **KPI**
   * **Bereitstellung**

1. Fügen Sie auf der Registerkarte **Allgemein** eine Beschreibung für Ihr Programm hinzu und laden Sie optional eine Miniaturansicht hoch, indem Sie auf **Foto ändern** klicken.

   ![Registerkarte „Allgemein“](/help/assets/Setup_Program-General.png)

1. Auf der Registerkarte **KPI** definieren Sie Ihre KPIs. In diesem Beispiel werden separate KPIs für **AEM Sites** und **AEM Assets** definiert. Geben Sie die KPIs für die Produkte an, die Sie lizenziert haben.

   Im Abschnitt [KPIs](#kpis) finden Sie weitere Informationen darüber, wie die KPIs in Cloud Manager gemessen werden.

   ![Definieren von KPIs](/help/assets/Setup_Program-KPIs.png)

1. Auf der Registerkarte **Bereitstellung** können Sie die bedarfsorientierten Skalierungsoptionen für Ihre Umgebungen festlegen, wenn für Ihr Programm die automatische Skalierung aktiviert ist.

   Die automatische Skalierung gilt nur für die Produktionsumgebung und ist für einige Kundenprogramme nicht verfügbar.

   ![Bereitstellungsoptionen](/help/assets/Setup_Program-Provisioning.png)

1. Klicken Sie auf **Speichern**.

Ihr Programm wird erstellt. Die Bereitstellung von Ressourcen dauert mehrere Minuten, bevor das Programm einsatzbereit ist.

## Bearbeiten eines Programms {#editing-program}

Sie können Programme nach ihrer Einrichtung bearbeiten.

**Bearbeiten eines Programms:**

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Gehen Sie zum Programm auf dem Cloud Manager-Startbildschirm.

1. Klicken Sie auf **Programm bearbeiten**, um Ihr Programm über die Seite **Übersicht** zu aktualisieren oder zu ändern.

   ![Option „Programm bearbeiten“](/help/assets/set-up-program/edit-program1.png)

1. Das Dialogfeld **Programm bearbeiten** wird angezeigt, sodass Sie Ihr Programm ändern können. Weitere Informationen zu den verfügbaren Feldern finden Sie im Abschnitt [Einrichten von Programmen mit Cloud Manager](#program-setup-cloud-manager).

   ![Dialog „Programm bearbeiten“](/help/assets/set-up-program/edit-program-general.png)

1. Klicken Sie auf **Aktualisieren**, um Ihre Änderungen zu speichern.

Die Änderungen werden sofort in Cloud Manager gespeichert, aber erst bei der nächsten Ausführung der Pipeline in Ihre Umgebungen übernommen.

Wenn Sie noch keine Pipeline erstellt haben, lesen Sie die Dokumente [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren produktionsfremder Pipelines](/help/using/non-production-pipelines.md).

## Wechseln zwischen Programmen {#swithing-programs}

Wenn Sie an einem Programm arbeiten, können Sie schnell zu einem anderen Programm wechseln, ohne zur Übersichtsseite von Cloud Manager zurückzukehren.

Verwenden Sie die Aktionsleiste, um zu einem anderen Programm zu wechseln, das aktuelle Programm zu bearbeiten oder ein neues Programm hinzuzufügen.

![Programmumschalter](/help/assets/set-up-program/setup2.png)

## KPIs {#kpis}

Die KPIs werden bei Tests gemessen, die in der Staging-Umgebung ausgeführt werden. Normalerweise werden diese KPIs an die Funktionen der Staging-Umgebung angepasst.

Ein Anwender, der beispielsweise durchschnittlich 1.000 Seitenansichten pro Minute in seiner Produktionsumgebung erwartet und der vier Dispatcher-/Veröffentlichungs-Server in der Produktion hat, reduziert dieses Szenario auf 250 Seitenansichten pro Minute. Bei diesem Szenario wird davon ausgegangen, dass die Staging-Umgebung nur aus einem einzigen Paar aus Dispatcher- und Veröffentlichungs-Server besteht.

Assets-Leistungstests umfassen das wiederholte Hochladen von Assets über einen Zeitraum von 30 Minuten. Die Verarbeitungszeit für jedes Asset und verschiedene Metriken auf Systemebene werden während der gesamten Testdauer gemessen.

Sie haben ein Content Delivery Network (CDN) wie Akamai oder CloudFront für Ihre Produktionsumgebung konfiguriert. Da [!UICONTROL Cloud Manager] direkt in Bezug zur Staging-Umgebung getestet wird, spiegelt der KPI nur den Traffic wider, der voraussichtlich durch das CDN weitergeleitet wird. Das heißt, der Cache fehlt. Normalerweise ist dieser Traffic eine relativ kleine Teilmenge des gesamten Produktions-Traffics.

## Videoüberblick {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
