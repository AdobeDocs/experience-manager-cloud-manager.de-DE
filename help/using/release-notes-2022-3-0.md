---
title: Versionshinweise für 2022.3.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.3.0.
feature: Release Information
source-git-commit: f1d359921a11ab8a6117a15cd5eb72362bbb8360
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2022.3.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für [!UICONTROL Cloud Manager] Version 2022.3.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2022.3.0 ist der 10. März 2022. Die nächste Version ist für den 7. April 2022 geplant.

## Neue Funktionen {#what-is-new}

* Outbounds von HTTP-Anforderungen aus Asset-Tests stammen jetzt aus einem festen IP-Bereich.


## Fehlerbehebungen {#bug-fixes}

* Die Option **Änderungen am Lastenausgleich überspringen** konnte nicht deaktiviert werden.
* Die Option **Änderungen am Lastenausgleich überspringen** wurde in der AMS-Entwicklungsimplementierung **Pipeline-Workflow bearbeiten** nicht angezeigt.
* Eine Untergruppe von manuell erstellten Git-Repositorys hatte einen falschen Namenswert, was verhindert hat, dass die Funktion zur Wiederverwendung von Build-Artefakten effektiv war. Die Namen dieser Repositorys wurden geändert, und die Benutzer sehen den berichtigten Namen in der Cloud Manager-API/-Benutzeroberfläche.
* Build-Artefakte aus produktionsfremden Pipelines wurden in Vollstapel-Pipelines der Produktion unangemessen wiederverwendet.
* Beim Hinzufügen oder Bearbeiten einer Code-Qualitäts-Pipeline werden die Optionen zum Verarbeiten von Metrikfehlern nicht mehr angezeigt.
* Im Build-Schritt konnten einige unerwartete Konfigurationen von Pipeline-Variablen auftreten.
