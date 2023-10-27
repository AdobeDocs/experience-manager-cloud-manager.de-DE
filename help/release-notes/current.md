---
title: Versionshinweise für 2023.10.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2023.10.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851364e74864c28b3bcd9285dfbe06ddb530eb10
workflow-type: ht
source-wordcount: '226'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2023.10.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2023.10.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] Version 2023.10.0 ist der 5. Oktober 2023. Die nächste Version ist für den 2. November 2023 geplant.

## Neue Funktionen {#what-is-new}

* Die Rolle **Bereitstellungs-Manager** kann [eine Reihe von Inhaltspfaden konfigurieren, die entweder ungültig gemacht oder aus dem AEM-Dispatcher-Cache gelöscht werden, wenn eine produktionsfremde Pipeline ausgeführt wird.](/help/using/non-production-pipelines.md)
   * Wenn diese Cache-Aktionen konfiguriert sind, werden sie im Rahmen der Einrichtung der Bereitstellungs-Pipeline direkt nach der Bereitstellung etwaiger Inhaltspakete durchgeführt.
   * Diese Einstellungen verwenden das Standardverhalten von AEM Dispatcher.
* Mit der Cloud Manager-Version Oktober 2023 werden Java-Versionen schrittweise aktualisiert.
   * Die kleineren Versionen für Java 8 und 11 und Maven wurden aktualisiert und werden in den nächsten zwei Monaten schrittweise eingeführt. Die neue Version verfügt über mehrere Sicherheitskorrekturen und Fehlerbehebungen. Die neuen Versionen sind:
   * *Maven 3.8.8*
   * *Java 8-Version: /usr/lib/jvm/jdk1.8.0_371*
   * *Java 11-Version: /usr/lib/jvm/jdk-11.0.20*
   * [Siehe die OpenJDK-Beratung](https://openjdk.org/groups/vulnerability/advisories/) für Details zur Sicherheit und zu Fehlerbehebungen in diesen JDK-Updates.
