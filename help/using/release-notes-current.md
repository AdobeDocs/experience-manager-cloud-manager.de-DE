---
title: Versionshinweise für 2021.3.0
seo-title: Versionshinweise für AEM Cloud Manager 2021.3.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.3.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2021.3.0.
translation-type: tm+mt
source-git-commit: 47424ea0e087f1f69db0aef8ca2122de2352a6e0
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 19%

---

# Versionshinweise für 2021.3.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.3.0 wurde am 11. März 2021 veröffentlicht.

## Neue Funktionen {#whats-new}

* Benutzer mit entsprechender Berechtigung können jetzt Programm bearbeiten, sodass sie Folgendes selbstständig erledigen können:

   * hinzufügen Sites-Lösung für ein vorhandenes Programm mit Assets (oder umgekehrt).
   * Entfernen Sie Sites (oder Assets) aus einem vorhandenen Programm mit sowohl Sites als auch Assets.
   * Das Hinzufügen (Zurück) einer Lösung kann dem vorhandenen Programm oder als neues Programm vorgenommen werden.

* Zur Validierung der Kundendienstkonfiguration wurde ein neues Code-Qualitätstool [Dispatcher-Optimierungstool](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) eingeführt.

* Die Benutzer können nun ihre Cloud Manager-Rolle(en) anzeigen, indem sie nach dem Navigieren zum Symbol &quot;User Profil&quot;(oben rechts) von Unified Shell die Option **Ansicht Cloud Manager-Rolle(en)** auswählen.

* Die Beschriftung **Antrag auf Genehmigung** wurde zur besseren Klarheit in **Produktionsgenehmigung** umbenannt.

* Die Beschriftung **Version** wurde im Bildschirm &quot;Produktions-Pipeline-Ausführung&quot;in **Git-Tag** umbenannt.

* Die Beschriftungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr wahres Verhalten widerzuspiegeln - **Sofort abbrechen** und **Sofort genehmigen**. Weitere Informationen finden Sie unter [Konfigurieren der Pipeline-Einstellungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager).

* Die Listen zum Entfernen von Klassen und Methoden wurden auf der Grundlage der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite für die Ausführung der Pipeline wegnavigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich Beginn ist.