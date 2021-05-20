---
title: Versionshinweise für 2021.3.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.3.0.
feature: Versionshinweise
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 503d9b25855633737c49e3e278a3a76052ed84d1
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 18%

---

# Versionshinweise für 2021.3.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.3.0 wurde am 11. März 2021 veröffentlicht.
Die nächste Version ist für den 8. April 2021 geplant.

## Neue Funktionen {#whats-new}

* Ein neues Code-Qualitätstool [Dispatcher Optimization Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) wurde eingeführt, um die Konfiguration des Kunden-Dispatchers zu überprüfen.

* Benutzer können nun ihre Cloud Manager-Rollen sehen, indem sie die Option **Cloud Manager-Rolle(en) anzeigen** auswählen, nachdem sie zum Benutzerprofilsymbol (oben rechts) von Unified Shell navigiert sind.

* Der Titel **Antrag auf Genehmigung** wurde zur besseren Übersichtlichkeit in **Produktionsgenehmigung** umbenannt.

* Der Titel **Version** wurde im Bildschirm zur Ausführung der Produktions-Pipeline in **Git-Tag** umbenannt.

* Die Beschriftungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr tatsächliches Verhalten widerzuspiegeln - **Sofort abbrechen** und **Sofort genehmigen**. Weitere Informationen finden Sie unter [Konfigurieren der Pipeline-Einstellungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager) .

* Die Listen zur veralteten Klasse und Methode wurden basierend auf der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* Wenn der Benutzer die Pipeline-Ausführungsseite gelegentlich unmittelbar nach dem Start einer Pipeline verlässt, wird eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich gestartet wird.
