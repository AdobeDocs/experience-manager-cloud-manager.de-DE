---
title: Versionshinweise für Cloud Manager 2025.1.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.1.0 in Adobe Managed Services.
feature: Release Information
source-git-commit: c25508b24f00b8f8cfa7bae3cc4b0d6ecf684db3
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 40%

---

# Versionshinweise für Cloud Manager 2025.1.0 in Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2025.1.0 in Adobe Managed Services.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2025.1.0 ist der Dienstag, 22. Januar 2024.

Die Veröffentlichung der nächsten Version ist für den Freitag, 13. Februar 2025 geplant.

## Neue Funktionen {#what-is-new}

**Regeln zur Code-Qualität:** Der Schritt &quot;Cloud Manager-Code-Qualität“ beginnt mit der Verwendung von SonarQube Server 9.9 mit Cloud Manager Version 2025.2.0, geplant für Donnerstag, 13. Februar 2025.

Zur Vorbereitung sind aktualisierte SonarQube-Regeln jetzt verfügbar unter [Code-Qualitätsregeln](/help/using/code-quality-testing.md#code-quality-testing-step).

Sie können die neuen Regeln frühzeitig überprüfen, indem Sie die folgende Pipeline-Textvariable festlegen (siehe Screenshot unten):

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

Legen Sie außerdem die folgende Variable fest, um sicherzustellen, dass der Code-Qualitätsschritt für denselben Commit ausgeführt wird (normalerweise für denselben `commitId` übersprungen):

`CM_DISABLE_BUILD_REUSE` = `true`

![Seite Variablenkonfiguration](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe empfiehlt die Erstellung einer neuen CI/CD-Code-Qualitäts-Pipeline, die auf derselben Verzweigung wie die Haupt-Produktions-Pipeline konfiguriert ist. Legen Sie die entsprechenden Variablen *vor* der Version vom 13. Februar 2025 fest, um zu überprüfen, ob die neuen erzwungenen Regeln keine Blocker einführen.

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
