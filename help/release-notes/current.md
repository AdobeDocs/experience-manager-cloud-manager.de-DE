---
title: Versionshinweise für 2024.1.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2024.1.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b235e398b42e9da3dd2efacdc0ef38b6803bd213
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 68%

---


# Versionshinweise für Cloud Manager Version 2024.1.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2024.1.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] Version 2024.1.0 wurde am 17. Januar 2024 veröffentlicht. Die nächste Version ist für den 16. Februar 2024 geplant.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie an unserem Early-Adopter-Programm teil und nutzen Sie die Möglichkeit, einige zukünftige Funktionen zu testen

### Bringen Sie Ihren eigenen GitHub mit {#byo-github}

Wenn Sie Ihre Repositorys mit GitHub verwalten, [können Sie jetzt Code direkt in Ihren GitHub-Repositorys über Cloud Manager validieren.](/help/managing-code/byo-github.md) Durch diese Integration entfällt die Notwendigkeit, Code ständig mit dem Adobe-Repository zu synchronisieren, und Sie können Pull-Anfragen überprüfen, bevor Sie sie in den Hauptverzweigungen zusammenführen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-CloudManager_BYOG@adobe.com`.

## Fehlerbehebungen {#bug-fixes}

* Ein Fehler wurde für einige Fälle korrigiert, in denen Downloads aufgrund der Interpretation von Daten durch die Testanwendung fehlschlugen, wodurch der Gesamt-Fehlerprozentsatz für den Test fehlschlug.
* Wenn ein Build-Schritt mit dem Status abgeschlossen wird `FAILED` aufgrund einer `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR`, wird sie nun aufgrund von Zusammenführungskonflikten mit der Zielverzweigung ordnungsgemäß als Fehler beschrieben.
