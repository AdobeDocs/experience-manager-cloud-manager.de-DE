---
title: Einrichten von Programmen
description: Nach dem Onbarding muss der Geschäftsinhaber verschiedene Ersteinstellungen am Programm vornehmen.
exl-id: 795c7112-d564-4fbf-96a1-152a6c286bf2
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '585'
ht-degree: 100%

---


# Einrichten von Programmen {#program-setup}

Nach dem Onboarding vervollständigt der Geschäftsinhaber die anfängliche Einrichtung des Programms, einschließlich der Festlegung der Programmbeschreibung und der Definition der wichtigsten Leistungsindikatoren (KPIs), die für Leistungstests verwendet werden.

## Einrichten von Programmen mit [!UICONTROL Cloud Manager] {#program-setup-cloud-manager}

Führen Sie die folgenden Schritte aus, um das Programm einzurichten und KPIs zu definieren.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf **Programm einrichten**, um den Einrichtungsprozess zu starten.

   ![Programm einrichten](/help/assets/set-up-program/setup1.png)

1. Im Dialogfeld **Programm einrichten** können Sie in drei Registerkarten Informationen zum Programm eingeben:

   * **Allgemein**
   * **KPI**
   * **Bereitstellung**

1. Fügen Sie auf der Registerkarte **Allgemein** eine Beschreibung für Ihr Programm hinzu und laden Sie optional eine Miniaturansicht hoch, indem Sie auf **Foto ändern** klicken.

   ![Registerkarte „Allgemein“](/help/assets/Setup_Program-General.png)

1. Auf der Registerkarte **KPI** definieren Sie Ihre KPIs. In diesem Beispiel werden separate KPIs für **AEM Sites** und **AEM Assets** definiert. Sie können die KPIs für die von Ihnen lizenzierten Produkte angeben.

   * Im Abschnitt [KPIs](#kpis) finden Sie weitere Informationen darüber, wie die KPIs in Cloud Manager gemessen werden.

   ![Definieren von KPIs](/help/assets/Setup_Program-KPIs.png)

1. Auf der Registerkarte **Bereitstellung** können Sie die bedarfsorientierten Skalierungsoptionen für Ihre Umgebungen festlegen, wenn für Ihr Programm die automatische Skalierung aktiviert ist.

   * Die Funktion zur automatischen Skalierung ist nur auf die Produktionsumgebung anwendbar und steht ggf. nicht für alle Kundenprogramme zur Verfügung.

   ![Bereitstellungsoptionen](/help/assets/Setup_Program-Provisioning.png)

1. Klicken Sie auf **Speichern**, um den Einrichtungsassistenten abzuschließen.

Ihr Programm wird erstellt. Die Bereitstellung von Ressourcen kann mehrere Minuten dauern, bevor das Programm einsatzbereit ist.

## Bearbeiten von Programmen {#editing-program}

Sie können Programme nach ihrer Einrichtung bearbeiten. Führen Sie diese Schritte aus, um ein Programm zu bearbeiten.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Gehen Sie zum Programm auf dem Cloud Manager-Startbildschirm.

1. Klicken Sie auf **Programm bearbeiten**, um Ihr Programm über die Seite **Übersicht** zu aktualisieren oder zu verändern.

   ![Option „Programm bearbeiten“](/help/assets/set-up-program/edit-program1.png)

1. Das Dialogfeld **Programm bearbeiten** wird angezeigt, sodass Sie Ihr Programm ändern können. Weitere Informationen zu den verfügbaren Feldern finden Sie im Abschnitt [Einrichten von Programmen mit Cloud Manager](#program-setup-cloud-manager).

   ![Dialog „Programm bearbeiten“](/help/assets/set-up-program/edit-program-general.png)

1. Klicken Sie auf **Aktualisieren**, um Ihre Änderungen zu speichern.

Beachten Sie, dass die Änderungen sofort in Cloud Manager gespeichert werden, aber erst bei der nächsten Ausführung der Pipeline in Ihre Umgebungen übernommen werden.

Wenn Sie noch keine Pipeline erstellt haben, lesen Sie die Dokumente [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/using/non-production-pipelines.md).

## Wechsel zwischen Programmen {#swithing-programs}

Wenn Sie an einem Programm arbeiten, können Sie schnell zu einem anderen Programm wechseln, ohne zur Übersichtsseite von Cloud Manager zurückzukehren.

Verwenden Sie die Aktionsleiste, um zu einem anderen Programm zu wechseln, das aktuelle Programm zu bearbeiten oder ein neues Programm hinzuzufügen.

![Programmumschalter](/help/assets/set-up-program/setup2.png)

## KPIs {#kpis}

Die KPIs einer Website werden bei Tests gemessen, die in der Staging-Umgebung ausgeführt werden. Normalerweise werden diese KPIs entsprechend den Kapazitäten der Staging-Umgebung herunterskaliert.

Anwenderinnen und Anwender, die beispielsweise durchschnittlich 1000 Seitenaufrufe pro Minute in der Produktionsumgebung erwartem und vier Dispatcher-/Veröffentlichungs-Server in der Produktion haben, sollten dies auf 250 Seitenaufrufe pro Minute skalieren. Dabei wird davon ausgegangen, dass die Staging-Umgebung nur aus einem einzigen Paar aus Dispatcher- und Veröffentlichungs-Server besteht.

Assets-Leistungstests erfolgen, indem Assets während eines 30-minütigen Testzeitraums wiederholt hochgeladen und die Verarbeitungszeit für jedes Asset sowie verschiedene Metriken auf Systemebene gemessen werden.

Vielleicht haben Sie ein Content Delivery Network (CDN) wie Akamai oder CloudFront vor Ihrer Produktionsumgebung vorgeschaltet. Da [!UICONTROL Cloud Manager] direkt in Bezug zur Staging-Umgebung getestet wird, sollten die KPIs dem erwarteten Traffic entsprechen, der durch das CDN weitergeleitet wird, d. h. ohne Cache. In der Regel handelt es sich dabei um eine relativ kleine Teilmenge des gesamten Produktions-Traffics.

## Videoüberblick {#video}

>[!VIDEO](https://video.tv.adobe.com/v/26313/)
