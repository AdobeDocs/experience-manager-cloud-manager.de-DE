---
title: Einrichten von Programmen
description: Nach dem Onboarding muss der Business Owner einige Ersteinstellungen am Programm vornehmen.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 49%

---


# Programmeinrichtung {#program-setup}

Nach dem Onboarding richtet der Business Owner das Programm ein, indem er eine Beschreibung hinzufügt und wichtige Leistungsindikatoren (KPIs) definiert. Diese KPIs werden dann für Leistungstests verwendet.

## Programmeinrichtung mit [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Führen Sie die folgenden Schritte aus, um das Programm einzurichten und KPIs zu definieren.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf **Programm einrichten**, um den Einrichtungsprozess zu starten.

   ![Programm einrichten](/help/assets/set-up-program/setup1.png)

1. Im Dialogfeld **Programm einrichten** können Sie Programminformationen auf drei Registerkarten eingeben:

   * **Allgemein**
   * **KPI**
   * **Bereitstellung**

1. Fügen Sie auf der Registerkarte **Allgemein** eine Beschreibung für Ihr Programm hinzu und laden Sie optional eine Miniaturansicht hoch, indem Sie auf **Foto ändern** klicken.

   ![Registerkarte „Allgemein“](/help/assets/Setup_Program-General.png)

1. Auf der Registerkarte **KPI** definieren Sie Ihre KPIs. In diesem Beispiel werden separate KPIs für **AEM Sites** und **AEM Assets** definiert. Geben Sie die KPIs für die Produkte an, die Sie lizenziert haben.

   Im Abschnitt [KPIs](#kpis) finden Sie weitere Informationen darüber, wie die KPIs in Cloud Manager gemessen werden.

   ![Definieren von KPIs](/help/assets/Setup_Program-KPIs.png)

1. Auf der Registerkarte **Bereitstellung** können Sie die bedarfsorientierten Skalierungsoptionen für Ihre Umgebungen festlegen, wenn für Ihr Programm die automatische Skalierung aktiviert ist.

   Die automatische Skalierung gilt nur für die Produktionsumgebung und ist möglicherweise nicht für alle Kundenprogramme verfügbar.

   ![Bereitstellungsoptionen](/help/assets/Setup_Program-Provisioning.png)

1. Klicken Sie auf **Speichern**.

Ihr Programm wird erstellt. Die Bereitstellung von Ressourcen kann mehrere Minuten dauern, bevor das Programm einsatzbereit ist.

## Programm bearbeiten {#editing-program}

Sie können Programme nach ihrer Einrichtung bearbeiten. Führen Sie diese Schritte aus, um ein Programm zu bearbeiten.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Gehen Sie zum Programm auf dem Cloud Manager-Startbildschirm.

1. Klicken Sie auf **Programm bearbeiten** , um Ihr Programm auf der Seite **Überblick** zu aktualisieren oder zu ändern.

   ![Option „Programm bearbeiten“](/help/assets/set-up-program/edit-program1.png)

1. Das Dialogfeld **Programm bearbeiten** wird angezeigt, sodass Sie Ihr Programm ändern können. Weitere Informationen zu den verfügbaren Feldern finden Sie im Abschnitt [Einrichten von Programmen mit Cloud Manager](#program-setup-cloud-manager).

   ![Dialog „Programm bearbeiten“](/help/assets/set-up-program/edit-program-general.png)

1. Klicken Sie auf **Aktualisieren** , um Ihre Änderungen zu speichern.

Die Änderungen werden sofort in Cloud Manager gespeichert, werden jedoch erst bei der nächsten Pipeline-Ausführung in Ihren Umgebungen übernommen.

Wenn Sie noch keine Pipeline erstellt haben, finden Sie weitere Informationen unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md).

## Zwischen Programmen wechseln {#swithing-programs}

Wenn Sie an einem Programm arbeiten, können Sie schnell zu einem anderen Programm wechseln, ohne zur Übersichtsseite von Cloud Manager zurückzukehren.

Verwenden Sie die Aktionsleiste, um zu einem anderen Programm zu wechseln, das aktuelle Programm zu bearbeiten oder ein neues Programm hinzuzufügen.

![Programmumschalter](/help/assets/set-up-program/setup2.png)

## KPIs {#kpis}

Sites-KPIs werden bei Tests gemessen, die in der Staging-Umgebung ausgeführt werden. Normalerweise werden diese KPIs entsprechend den Kapazitäten der Staging-Umgebung herunterskaliert.

Beispiel: Ein Anwender, der von durchschnittlich 1.000 Seitenaufrufen pro Minute in seiner Produktionsumgebung ausgeht und über vier Dispatcher-/Veröffentlichungsserver in der Produktion verfügt, sollte dieses Szenario auf 250 Seitenaufrufe pro Minute skalieren. In diesem Szenario wird davon ausgegangen, dass ihre Staging-Umgebung nur aus einem einzigen Dispatcher-/Veröffentlichungs-Server-Paar besteht.

Assets-Leistungstests erfordern das wiederholte Hochladen von Assets über einen Zeitraum von 30 Minuten. Die Verarbeitungszeit für jedes Asset und verschiedene Metriken auf Systemebene werden während des Tests gemessen.

Vielleicht haben Sie ein Content Delivery Network (CDN) wie Akamai oder CloudFront vor Ihrer Produktionsumgebung vorgeschaltet. Da [!UICONTROL Cloud Manager] direkt gegen die Staging-Umgebung getestet wird, sollten die KPI nur den erwarteten Traffic widerspiegeln, der durch das CDN weitergeleitet wird. Das heißt, der Cache fehlt. In der Regel handelt es sich bei diesem Erlebnis um eine relativ kleine Teilmenge des gesamten Produktions-Traffics.

## Videoübersicht {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
