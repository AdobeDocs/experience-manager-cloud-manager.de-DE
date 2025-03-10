---
title: Benachrichtigungen
description: Erfahren Sie, wie Sie von Cloud Manager über wichtige Ereignisse benachrichtigt werden.
exl-id: cfd5655f-2d2c-4304-b25c-6cdffe7ff64c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 100%

---


# Benachrichtigungen {#notifications}

Erfahren Sie, wie Sie von Cloud Manager über wichtige Ereignisse benachrichtigt werden.

## Benachrichtigungen in Cloud Manager {#cloud-manager-notifications}

[!UICONTROL Cloud Manager] sendet Ihnen zu Beginn einer Produktionsimplementierung beim Start und beim Abschluss der Produktions-Pipeline (erfolgreich oder nicht erfolgreich) Benachrichtigungen. Und wenn die Schritte **Genehmigung einer Live-Schaltung** und **Geplant** erreicht sind. Diese Benachrichtigungen werden über das [!UICONTROL Experience Cloud]-Benachrichtigungssystem gesendet.

>[!NOTE]
>
>Die Genehmigung und geplanten Benachrichtigungen werden nur an Anwender mit den Rollen **Geschäftsinhaber**, **Programm-Manager** und **Bereitstellungs-Manager** gesendet.

Die Benachrichtigungen werden in einer Seitenleiste der [!UICONTROL Cloud Manager]-Benutzeroberfläche und überall in Adobe [!UICONTROL Experience Cloud] angezeigt.

Das Glockensymbol in der Kopfzeile zeigt ein Badge, wenn es neue Benachrichtigungen für Sie gibt.

![Benachrichtigungssymbol](/help/assets/notifications-bell-badged.png)

Klicken Sie auf das Glockensymbol, um die Seitenleiste zu öffnen und die Benachrichtigungen anzuzeigen. Die Registerkarte **Benachrichtigungen** in der Seitenleiste listet die neuesten Benachrichtigungen wie beispielsweise Bereitstellungsbestätigungen auf. Benachrichtigungen beziehen sich auf Ihre Umgebungen.

![Benachrichtigungsseitenleiste](/help/assets/notifications-activities.png)

Die Registerkarte **Ankündigungen** enthält Ankündigungen zu Adobe-Produkten. Ankündigungen beziehen sich auf das Produkt.

![Benachrichtigungsseitenleiste](/help/assets/notificaitons-announcements.png)

Klicken Sie auf eine Benachrichtigung oder Mitteilung, um deren Details anzuzeigen. Benachrichtigungen, die mit Aktivitäten wie Pipeline-Bereitstellungen verknüpft sind, führen Sie zu den Details dieser Aktivität, beispielsweise dem Pipeline-Ausführungsfenster.

Klicken Sie unten im Bedienfeld auf die Option **Alle anzeigen**, um alle Mitteilungen in Ihrem Posteingang anzuzeigen.

Klicken Sie unten im Bedienfeld auf die Option **Alle als gelesen markieren**, um alle ungelesenen Benachrichtigungen als gelesen zu markieren und das aktivierte Glockensymbol zurückzusetzen.

## Konfiguration von Benachrichtigungen {#configuration}

Sie können einstellen, wie Sie welche Benachrichtigungen erhalten möchten.

Klicken Sie auf das Zahnradsymbol oben in der Benachrichtigungsseitenleiste.

![Symbol für Benachrichtigungseinstellungen](/help/assets/notifications-configuration.png)

Das Fenster **Experience Cloud-Einstellungen**, in dem Sie Benachrichtigungsabonnements auswählen und festlegen können, wie Sie Benachrichtigungen erhalten, wird geöffnet.

### Abonnements {#subscriptions}

Mit den Abonnements legen Sie fest, welche Benachrichtigungen Sie für welche Produkte erhalten.

![Abonnements für Benachrichtigungen](/help/assets/notifications-subscriptions.png)

Standardmäßig erhalten Sie alle Benachrichtigungen für alle Produkte. Klicken Sie neben einem Produkt auf **Anpassen**, um festzulegen, welche Arten von Benachrichtigungen Sie für dieses Produkt erhalten möchten.

![Anpassung des Benachrichtigungsabonnements](/help/assets/notifications-subscriptions-customize.png)

### Priorität {#priority}

Prioritätswarnungen werden mit einem **HOCH**-Tag gekennzeichnet. Sie können sie so konfigurieren, dass sie ausschließlich als Warnungen empfangen werden. Im Abschnitt **Priorität** können Sie festlegen, welche Kategorien als Prioritätsbenachrichtigungen eingestuft werden.

![Benachrichtigungspriorität](/help/assets/notifications-priority.png)

Verwenden Sie die Dropdown-Liste, um die Liste der Kategorien zu erweitern, die als prioritär eingestuft werden. Klicken Sie auf das `X` neben den Kategorienamen, um sie zu entfernen.

### Warnhinweise {#alerts}

Warnhinweise werden für einige Sekunden in der oberen rechten Ecke des Fensters angezeigt. Im Abschnitt **Warnhinweise** können Sie festlegen, für welche Benachrichtigungen Sie Warnhinweise erhalten möchten.

![Benachrichtigungs-Warnhinweise](/help/assets/notifications-alerts.png)

Sie können das Verhalten der Warnhinweise definieren.

* **Warnhinweise anzeigen für**: Definiert die Arten von Benachrichtigungen, die Warnhinweise auslösen.
* **Warnhinweise sollen am Bildschirm angezeigt werden, bis ich sie schließe**: Legt fest, ob die Warnhinweise bestehen bleiben sollen, bis Sie sie aktiv deaktivieren.
* **Dauer**: Legt fest, wie lange ein Warnhinweis auf dem Bildschirm eingeblendet werden soll, außer Sie haben ausgewählt, dass ein Warnhinweis auf dem Bildschirm verbleiben soll.

### E-Mails {#emails}

Benachrichtigungen sind in der Web-Benutzeroberfläche aller Adobe [!UICONTROL Experience Cloud]-Lösungen verfügbar. Sie können auch im Abschnitt **E-Mails** festlegen, dass diese Benachrichtigungen per E-Mai gesendet werden sollen.

![Benachrichtigungs-E-Mails](/help/assets/notifications-emails.png)

Standardmäßig werden keine E-Mails versendet. Sie haben für den E-Mail-Empfang folgende Wahlmöglichkeiten:

* Sofort
* Täglich
* Wöchentlich

Wenn die Option **Sofortige Benachrichtigungen** ausgewählt ist, werden für jede Benachrichtigung sofort E-Mails versendet. Bei einer **täglichen Zusammenfassung** können Sie die Uhrzeit und bei einer **wöchentlichen Zusammenfassung** können Sie den Tag und die Uhrzeit des Versands auswählen.
