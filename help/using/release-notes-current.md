---
title: Versionshinweise für 2022.01.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.01.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: ebbbbdca2bfd834bc3dc0ff06ffb318df42713ee
workflow-type: ht
source-wordcount: '149'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager Version 2021.12.0 {#release-notes}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] Version 2022.01.0.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2022.01.0 ist der 20. Januar 2022. Die nächste Version soll am 10. Februar 2022 veröffentlicht werden.

## Neue Funktionen {#whats-new}

* Cloud Manager wird [den Neuaufbau der Code-Basis vermeiden, wenn festgestellt wird, dass ein und derselbe Git-Commit](/help/using/setting-up-project.md#build-artifact-reuse) in mehreren Pipeline-Ausführungen mit vollem Stapel verwendet wird.
* Beim Generieren eines Git-Kennworts wird das Ablaufdatum angezeigt.

## Fehlerbehebungen {#bug-fixes}

* Das gelegentliche Auftreten von falsch-positiven Pipeline-Fehlern wurde behoben.
* Bei Programmen mit nur einem Repository zeigt der Bildschirm zur Pipeline-Ausführung jetzt den Namen des Repositorys an.
