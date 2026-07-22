---
title: Benachrichtigungen
description: Erfahren Sie, wie Sie von Cloud Manager über wichtige Ereignisse benachrichtigt werden.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
TQID: https://experienceleague.adobe.com/WBAHeIAH1XL6oVy342wLaUAoAHkUoN1AbcAl2Erkte4
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 65b260abe417925f26d647fb9857d32c30455f9b
workflow-type: tm+mt
source-wordcount: 562
ht-degree: 56%

---

# Benachrichtigungen {#notifications}

Erfahren Sie, wie Sie von Cloud Manager über wichtige Ereignisse benachrichtigt werden.

## Benachrichtigungen in Cloud Manager {#cloud-manager-notifications}

Benachrichtigungen werden gesendet, wenn eine Produktions-Pipeline gestartet und während einer Produktionsbereitstellung (erfolgreich oder nicht erfolgreich) abgeschlossen wird. Und wenn die Schritte **Genehmigung einer Live-Schaltung** und **Geplant** erreicht sind. Diese Benachrichtigungen werden über das [!UICONTROL Experience Cloud]-Benachrichtigungssystem gesendet.

>[!NOTE]
>
>Die Genehmigung und geplanten Benachrichtigungen werden nur an Anwender mit den Rollen **Geschäftsinhaber**, **Programm-Manager** und **Bereitstellungs-Manager** gesendet.

Die Benachrichtigungen werden in einer Seitenleiste der [!UICONTROL Cloud Manager]-Benutzeroberfläche und überall in Adobe [!UICONTROL Experience Cloud] angezeigt.

Das Glockensymbol in der Kopfzeile zeigt einen Indikator an, wenn Sie neue Benachrichtigungen haben.

![Benachrichtigungssymbol](/help/assets/notifications-bell-badged.png)

Klicken Sie auf das Glockensymbol, um die Seitenleiste zu öffnen und die Benachrichtigungen anzuzeigen. Die Registerkarte **Benachrichtigungen** in der Seitenleiste listet die neuesten Benachrichtigungen wie beispielsweise Bereitstellungsbestätigungen auf. Benachrichtigungen beziehen sich auf Ihre Umgebungen.

![Benachrichtigungsseitenleiste](/help/assets/notifications-activities.png)

Die Registerkarte **Ankündigungen** enthält Ankündigungen zu Adobe-Produkten. Ankündigungen enthalten Informationen zum Produkt.

![Benachrichtigungsseitenleiste](/help/assets/notificaitons-announcements.png)

Klicken Sie auf eine Benachrichtigung oder Mitteilung, um deren Details anzuzeigen. Benachrichtigungen, die mit Aktivitäten wie Pipeline-Bereitstellungen verknüpft sind, führen Sie zu den Details dieser Aktivität, z. B. zum Pipeline-Ausführungsfenster.

Klicken Sie auf die Option **Alles anzeigen** am Ende des Bedienfelds, um alle Benachrichtigungen in Ihrem Posteingang anzuzeigen.

Klicken Sie auf **Option Alle als gelesen markieren** unten im Bedienfeld, um alle ungelesenen Benachrichtigungen als gelesen zu markieren und das Badge vom Glockensymbol zu entfernen.

## Konfiguration von Benachrichtigungen {#configuration}

Sie können einstellen, wie Sie welche Benachrichtigungen erhalten möchten.

Klicken Sie auf das Zahnradsymbol oben in der Benachrichtigungsseitenleiste.

![Symbol für Benachrichtigungseinstellungen](/help/assets/notifications-configuration.png)

Das Fenster **Experience Cloud** Einstellungen“ wird geöffnet. Darin können Sie Ihre Benachrichtigungsabonnements und den Empfang Ihrer Benachrichtigungen definieren.

### Abonnements {#subscriptions}

Abonnements definieren, für welche Produkte Sie Benachrichtigungen erhalten und welche Benachrichtigungen Sie erhalten.

![Abonnements für Benachrichtigungen](/help/assets/notifications-subscriptions.png)

Standardmäßig erhalten Sie alle Benachrichtigungen für alle Produkte. Klicken Sie zum Definieren der Benachrichtigungstypen, die Sie für ein Produkt erhalten **neben** auf „Anpassen“.

![Anpassung des Benachrichtigungsabonnements](/help/assets/notifications-subscriptions-customize.png)

### Priorität {#priority}

Prioritätswarnungen werden mit einem **HOCH**-Tag gekennzeichnet. Sie können sie so konfigurieren, dass sie ausschließlich als Benachrichtigungen gesendet werden. Im Abschnitt **Priorität** können Sie festlegen, welche Kategorien als Prioritätsbenachrichtigungen eingestuft werden.

![Benachrichtigungspriorität](/help/assets/notifications-priority.png)

Verwenden Sie die Dropdown-Liste, um die Liste der Kategorien zu erweitern, die als prioritär eingestuft werden. Klicken Sie auf das Löschsymbol neben den Kategorienamen, um sie zu löschen.

### Warnhinweise {#alerts}

Warnhinweise werden für einige Sekunden in der oberen rechten Ecke des Fensters angezeigt. Definieren Sie im **Warnhinweise**, für welche Benachrichtigungen Sie Warnhinweise erhalten möchten.

![Benachrichtigungs-Warnhinweise](/help/assets/notifications-alerts.png)

Sie können das Verhalten der Warnhinweise definieren.

* **Warnhinweise anzeigen für** - Definiert die Arten von Benachrichtigungen, bei denen ein Trigger Warnhinweise ausgibt.
* **Warnhinweise bleiben auf dem Bildschirm, bis Sie sie schließen** - Legt fest, ob die Warnhinweise bestehen bleiben, bis Sie sie aktiv deaktivieren.
* **Dauer** - Legt fest, wie lange der Warnhinweis auf dem Bildschirm eingeblendet wird, außer Sie haben ausgewählt, dass er auf dem Bildschirm verbleibt.

### E-Mails {#emails}

Benachrichtigungen sind in der Web-Benutzeroberfläche aller Adobe [!UICONTROL Experience Cloud]-Lösungen verfügbar. Um diese Benachrichtigungen per E-Mail zu erhalten, melden Sie sich im Abschnitt **E-Mails** an.

![Benachrichtigungs-E-Mails](/help/assets/notifications-emails.png)

Standardmäßig werden keine E-Mails gesendet. Sie können E-Mails wie folgt empfangen:

* Sofort
* Täglich
* Wöchentlich

Wenn die Option **Sofortige Benachrichtigungen** ausgewählt ist, werden für jede Benachrichtigung sofort E-Mails versendet. Bei einer **täglichen Zusammenfassung** können Sie die Uhrzeit und bei einer **wöchentlichen Zusammenfassung** können Sie den Tag und die Uhrzeit des Versands auswählen.
