---
title: Versionshinweise für 2022.4.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.4.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 3d4eea13c0f2e9c4030bbfd3b7c5c25336548498
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Versionshinweise für Cloud Manager Version 2022.4.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für [!UICONTROL Cloud Manager] Version 2022.4.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] Version 2022.4.0 wurde am 7. April 2022 veröffentlicht. Die nächste Version ist für den 5. Mai 2022 geplant.

## Neue Funktionen {#what-is-new}

* Verbesserungen an der Dauer und Erfolgsrate der Pipelineaufbauschritte wurden implementiert und werden schrittweise bis zum April für alle Kunden eingeführt.
* Sie können jetzt eine Git-Verzweigung einfach finden, indem Sie die ersten Zeichen des Namens in das Eingabefeld im Pipeline-Assistenten hinzufügen und bearbeiten und aus vorgeschlagenen Übereinstimmungen auswählen.
* Die **Pipelines** Seite hat jetzt Paginierung, um die Benutzerfreundlichkeit für Programme mit einer großen Anzahl von Pipelines zu verbessern.
   * In der Tabelle werden 50 Zeilen pro Seite angezeigt.
* Die Version der [AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) verwendet von Cloud Manager wurde auf Version 36 aktualisiert.
* Oracle JDK ist jetzt das Standard-JDK für die Entwicklung und den Betrieb von AEM. Der Build-Prozess von Cloud Manager wechselt automatisch zur Verwendung von Oracle JDK, auch wenn in der Maven-Toolchain explizit eine alternative Option ausgewählt ist.
   * Weitere Informationen zum Umstieg auf Oracle JDK finden Sie unter [die Dokumentation zur Build-Umgebung .](/help/using/build-environment-details.md#using-java-support)
   * Siehe [Häufig gestellte Fragen zur Java-Support-Richtlinie für Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/assets/Java_Policy_for_Adobe_Experience_Manager.pdf) um allgemeine Fragen zu dieser Änderung zu beantworten.
