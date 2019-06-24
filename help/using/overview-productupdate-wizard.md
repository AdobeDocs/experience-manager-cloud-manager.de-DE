---
title: Assistent für Produktaktualisierungen
seo-title: Assistent für Produktaktualisierungen
description: 'Diese Seite dient als Ausgangspunkt für den Produktaktualisierungsassistenten. '
seo-description: 'Diese Seite dient als Ausgangspunkt für den Produktaktualisierungsassistenten. '
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 9a1af88238a232c64d9f0229059c5001f314c736

---


# Overview to Product Update Wizard {#overview-product-update-wizard}

Der Assistent zur Produktaktualisierung ist ein Assistent für die Cloud Manager-Kunden, die auf den neuesten Adobe Experience Manager (AEM) 6.5 aktualisieren. Es optimiert den End-to-End-Prozess, gewährleistet die Einhaltung bewährter Verfahren in AEM mithilfe des CI/CD-Frameworks von Cloud Manager und integrierten automatisierten Tests.

Der Assistent umfasst fünf Phasen, die den Benutzer während eines AEM-Produktupdates anleiten. Die fünf Phasen sind:

* **Test**
* **Optimierung**
* **Ausführung**
* **Validierung**
* **Abschluss**

>[!NOTE]
>The current release of Product Update feature in Cloud Manager supports the **Evaluation** phase only. The other four phases namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon.


## Using Product Update Wizard {#using-product-update-wizard}

>[!NOTE]
>Kunden, die zu Cloud Manager geleitet wurden und die Berechtigung zum Aktualisieren auf AEM 6.5 haben, können den Produktaktualisierungsassistenten nutzen. Weitere Informationen erhalten Sie von Ihrem Customer Success Engineer (CSE).

1. Sie erhalten über Cloud Manager eine Pulse-Benachrichtigung, in der Sie darauf hingewiesen werden, dass eine neue Version von AEM 6.5 für Ihr Programm verfügbar ist.

1. An **[!UICONTROL AEM 6.5 Update]** card displays on the overview screen of [!UICONTROL Cloud Manager]. Diese Karte hilft Ihnen, die Phase des Aktualisierungsprozesses zu verfolgen, in dem Sie sich gerade befinden, und Sie werden darüber informiert, wie der nächste Schritt ausgeführt werden soll. Select **[!UICONTROL Start Update]** to start the update wizard.

   ![](assets/Start-Update.png)

### Die nächsten Schritte {#next-steps}

Once you click the **[!UICONTROL Start Update]** from the **[!UICONTROL AEM 6.5 Update]** card, the **Evaulation** phase starts.
Navigate to the [Evaluation Phase](evaluation.md) to learn more.
