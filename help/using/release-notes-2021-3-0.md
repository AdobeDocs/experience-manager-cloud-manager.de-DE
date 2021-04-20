---
title: Versionshinweise für 2021.3.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea,e05b22fe-f071-4b69-9db1-e3d7ee4cfbcc
translation-type: tm+mt
source-git-commit: 9c3e748f8aed969af861b505ee336eb5501d826f
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 18%

---

# Versionshinweise für 2021.3.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.3.0 wurde am 11. März 2021 veröffentlicht.
Die nächste Version ist für den 08. April 2021 geplant.

## Neue Funktionen {#whats-new}

* Zur Validierung der Kundendienstkonfiguration wurde ein neues Code-Qualitätstool [Dispatcher-Optimierungstool](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=en#dispatcher-optimization-tool-rules) eingeführt.

* Die Benutzer können nun ihre Cloud Manager-Rolle(en) anzeigen, indem sie nach dem Navigieren zum Symbol &quot;User Profil&quot;(oben rechts) von Unified Shell die Option **Ansicht Cloud Manager-Rolle(en)** auswählen.

* Die Beschriftung **Antrag auf Genehmigung** wurde zur besseren Klarheit in **Produktionsgenehmigung** umbenannt.

* Die Beschriftung **Version** wurde im Bildschirm &quot;Produktions-Pipeline-Ausführung&quot;in **Git-Tag** umbenannt.

* Die Beschriftungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr wahres Verhalten widerzuspiegeln - **Sofort abbrechen** und **Sofort genehmigen**. Weitere Informationen finden Sie unter [Konfigurieren der Pipeline-Einstellungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#configuring-the-pipeline-settings-from-cloud-manager).

* Die Listen zum Entfernen von Klassen und Methoden wurden auf der Grundlage der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet wurden.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite für die Ausführung der Pipeline wegnavigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich Beginn ist.
