---
title: Programmeinrichtung
description: Nach dem Onbarding muss der Geschäftsinhaber verschiedene Ersteinstellungen am Programm vornehmen.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 22%

---


# Programmeinrichtung {#program-setup}

Nach dem Onboarding schließt der Business Owner die Ersteinrichtung des Programms ab, einschließlich der Festlegung der Programmbeschreibung und der Definition der für Leistungstests verwendeten KPIs (Key Performance Indicators).

## Programmeinrichtung mit [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Führen Sie diese Schritte aus, um das Programm einzurichten und KPIs zu definieren.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken **Programm einrichten** um den Einrichtungsprozess zu starten.

   ![Programm einrichten](/help/assets/set-up-program/setup1.png)

1. Im **Programm einrichten** -Dialogfeld können Sie Programminformationen über drei Registerkarten eingeben:

   * **Allgemein**
   * **KPI**
   * **Bereitstellung**

1. Im **Allgemein** hinzufügen, eine Beschreibung für Ihr Programm hinzufügen und optional eine Miniaturansicht hochladen, indem Sie auf **Foto ändern**.

   ![Registerkarte „Allgemein“](/help/assets/Setup_Program-General.png)

1. Im **KPI** definieren Sie Ihre KPIs. In diesem Beispiel werden separate KPIs für **AEM Sites** und **AEM Assets**. Sie können die KPIs für die von Ihnen lizenzierten Produkte angeben.

   * Siehe Abschnitt . [KPIs](#kpis) für weitere Details zur Messung von KPIs in Cloud Manager.

   ![Definieren von KPIs](/help/assets/Setup_Program-KPIs.png)

1. Im **Bereitstellung** können Sie die Skalierungsoptionen für On-Demand-Umgebungen definieren, wenn die automatische Skalierung für Ihr Programm aktiviert ist.

   * Die automatische Skalierung gilt nur für die Produktionsumgebung und ist möglicherweise nicht für alle Kundenprogramme verfügbar.

   ![Bereitstellungsoptionen](/help/assets/Setup_Program-Provisioning.png)

1. Klicken Sie auf **Speichern**, um den Einrichtungsassistenten abzuschließen.

Ihr Programm wird erstellt. Es kann mehrere Minuten dauern, bis Ressourcen bereitgestellt werden, bevor das Programm einsatzbereit ist.

## Bearbeiten von Programmen {#editing-program}

Sie können Programme nach ihrer Einrichtung bearbeiten. Führen Sie diese Schritte aus, um ein Programm zu bearbeiten.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Gehen Sie zum Programm auf dem Cloud Manager-Startbildschirm.

1. Klicken Sie auf **Programm bearbeiten** , um Ihr Programm über die **Übersicht** Seite.

   ![Option „Programm bearbeiten“](/help/assets/set-up-program/edit-program1.png)

1. Die **Programm bearbeiten** angezeigt, sodass Sie Ihr Programm aktualisieren können. Siehe Abschnitt . [Programmeinrichtung mit Cloud Manager](#program-setup-cloud-manager) für Details zu den verfügbaren Feldern.

   ![Dialog „Programm bearbeiten“](/help/assets/set-up-program/edit-program-general.png)

1. Klicken Sie auf **Aktualisieren** , um Ihre Änderungen zu speichern.

Beachten Sie, dass die Änderungen sofort in Cloud Manager gespeichert werden, aber erst bei der nächsten Pipeline-Ausführung in Ihren Umgebungen übernommen werden.

Wenn Sie noch keine Pipeline erstellt haben, lesen Sie die Dokumente . [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von Nicht-Produktions-Pipelines.](/help/using/non-production-pipelines.md)

## Wechsel zwischen Programmen {#swithing-programs}

Bei der Arbeit an einem Programm können Sie schnell zu einem anderen Programm wechseln, ohne zur Übersichtsseite von Cloud Manager zurückzukehren.

Verwenden Sie die Symbolleiste, um zu einem anderen Programm zu wechseln, das aktuelle Programm zu bearbeiten oder ein neues Programm hinzuzufügen.

![Programmwechsel](/help/assets/set-up-program/setup2.png)

## KPIs {#kpis}

Sites-KPIs werden bei Tests gemessen, die in der Staging-Umgebung ausgeführt werden. In der Regel werden diese KPIs entsprechend den Funktionen der Staging-Umgebung herunterskaliert.

Beispiel: Ein Benutzer, der von durchschnittlich 1.000 Seitenaufrufen pro Minute in seiner Produktionsumgebung ausgeht und über vier Dispatcher-/Publishing-Server in der Produktion verfügt, sollte diese Anzahl auf 250 Seitenaufrufe pro Minute skalieren. Dabei wird davon ausgegangen, dass ihre Staging-Umgebung nur aus einem einzigen Dispatcher-/Veröffentlichungs-Server-Paar besteht.

Assets-Leistungstests erfolgen, indem Assets während eines 30-minütigen Testzeitraums wiederholt hochgeladen und die Verarbeitungszeit für jedes Asset sowie verschiedene Metriken auf Systemebene gemessen werden.

Möglicherweise verfügen Sie vor Ihrer Produktionsumgebung über ein CDN (Content Delivery Network) wie Akamai oder CloudFront. Seit [!UICONTROL Cloud Manager] Tests direkt mit der Staging-Umgebung verglichen werden, sollten die KPIs nur den erwarteten Traffic widerspiegeln, der durch das CDN weitergeleitet wird, d. h. der Cache fehlt. In der Regel handelt es sich dabei um eine relativ kleine Teilmenge des gesamten Produktionstraffics.

## Videoüberblick {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
