---
title: Versionshinweise für 2024.1.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2024.1.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: b235e398b42e9da3dd2efacdc0ef38b6803bd213
workflow-type: ht
source-wordcount: '243'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2024.1.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2024.1.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2024.1.0 ist der 17. Januar 2024. Die nächste Version wird voraussichtlich am 16. Februar 2024 veröffentlicht.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie an unserem Early-Adopter-Programm teil und nutzen Sie die Möglichkeit, einige zukünftige Funktionen zu testen

### Bringen Sie Ihren eigenen GitHub mit {#byo-github}

Wenn Sie Ihre Repositorys mit GitHub verwalten, [können Sie jetzt Code direkt in Ihren GitHub-Repositorys über Cloud Manager validieren.](/help/managing-code/byo-github.md) Durch diese Integration entfällt die Notwendigkeit, Code ständig mit dem Adobe-Repository zu synchronisieren, und Sie können Pull-Anfragen überprüfen, bevor Sie sie in den Hauptverzweigungen zusammenführen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-CloudManager_BYOG@adobe.com`.

## Fehlerbehebungen {#bug-fixes}

* Es wurde ein Fehler für einige Fälle korrigiert, in denen Downloads aufgrund der Interpretation von Daten durch die Testanwendung fehlschlugen, wodurch der gesamte Fehlerprozentsatz den Test fehlschlagen ließ.
* Wenn ein Build-Schritt aufgrund eines `BUILD_MAVEN_TRANSFER_ARTIFACT_ERROR` mit dem Status `FAILED` abgeschlossen wird, wird dies nun ordnungsgemäß als Fehler aufgrund von Zusammenführungskonflikten mit der Zielverzweigung beschrieben.
