---
title: Versionshinweise für 2022.3.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 7611667d8c617d501f9b69cbc7c854c195a5ebbe
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 28%

---


# Versionshinweise für Cloud Manager Version 2022.3.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für [!UICONTROL Cloud Manager] Version 2022.3.0.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] Version 2022.3.0 wurde am 10. März 2022 veröffentlicht. Die nächste Version ist für den 7. April 2022 geplant.

## Neue Funktionen {#what-is-new}

* Outbounds von HTTP-Anforderungen aus Asset-Tests stammen jetzt aus einem festen IP-Bereich.


## Fehlerbehebungen {#bug-fixes}

* Die **Änderungen am Lastenausgleich überspringen** -Option konnte nicht deaktiviert werden.
*Die **Änderungen am Lastenausgleich überspringen** wurde in der AMS-Entwicklungsimplementierung nicht angezeigt **Pipeline-Workflow bearbeiten**.
* Eine Untergruppe von manuell erstellten Git-Repositorys hatte einen falschen Namenswert, was verhindert hat, dass die Funktion zur Wiederverwendung von Build-Artefakten effektiv ist. Die Namen dieser Repositorys wurden geändert, und die Benutzer sehen den berichtigten Namen in der Cloud Manager-API/-Benutzeroberfläche.
* Build-Artefakte aus produktionsfremden Pipelines wurden in Produktions-Vollstapelpipelines unangemessen wiederverwendet.
* Beim Hinzufügen oder Bearbeiten einer Code-Qualitäts-Pipeline werden die Optionen zum Verarbeiten von Metrikfehlern nicht mehr angezeigt.
* Einige unerwartete Pipelinevariablenkonfigurationen konnten im Build-Schritt verursacht werden.
