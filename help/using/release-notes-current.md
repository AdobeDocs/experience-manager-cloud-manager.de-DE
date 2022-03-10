---
title: Versionshinweise für 2022.3.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6e98f9d2fcd69799bad86d1e247212b26273bd0b
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 29%

---


# Versionshinweise für Cloud Manager Version 2022.3.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für [!UICONTROL Cloud Manager] Version 2022.3.0.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] Version 2022.3.0 wurde am 10. März 2022 veröffentlicht. Die nächste Version ist für den 7. April 2022 geplant.

## Neue Funktionen {#what-is-new}

* [Die `reliability_rating` kritische Metrik](understand-your-test-results.md) wurde deaktiviert.
* Ein Benutzer kann nun die Spalten im **Pipelines** in Cloud Manager.

## Fehlerbehebungen {#bug-fixes}

* [Die **Änderungen am Lastenausgleich überspringen** option](configuring-production-pipelines.md#adding-production-pipeline) kann jetzt ordnungsgemäß deaktiviert werden.
* [Die **Änderungen am Lastenausgleich überspringen** option](configuring-production-pipelines.md#adding-production-pipeline) wird nun für den Workflow zur Bearbeitung der Bereitstellungs-Pipeline angezeigt.
* Eine Untergruppe manuell erstellter Git-Repositorys hatte falsche Namenswerte, die sich auf [die Funktion zur Wiederverwendung von Build-Artefakten.](setting-up-project.md#build-artifact-reuse) Die Namen dieser Repositorys wurden geändert, und die Benutzer sehen den berichtigten Namen in der Cloud Manager-API/-Benutzeroberfläche.
* [Beim Hinzufügen oder Bearbeiten einer Code-Qualitäts-Pipeline](configuring-non-production-pipelines.md) die Optionen zur Handhabung von Metrikfehlern werden nicht mehr angezeigt.
* Unerwartete Pipelinevariablenkonfigurationen verursachen keine Fehler mehr im Build-Schritt.
