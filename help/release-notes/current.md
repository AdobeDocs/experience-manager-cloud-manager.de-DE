---
title: Versionshinweise für 2024.3.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2024.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 22730ba281f7c1c4720158a3a813c56b815a0af1
workflow-type: ht
source-wordcount: '268'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2024.3.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2024.3.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2024.3.0 ist der 14. März 2024. Die nächste Version ist für den 11. April 2024 geplant.

## Neue Funktionen {#what-is-new}

* Details wie IP/DNS-Informationen (FQDN) der grünen Server werden jetzt in der Cloud Manager-Benutzeroberfläche angezeigt.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie an unserem Early-Adopter-Programm teil und nutzen Sie die Möglichkeit, einige zukünftige Funktionen zu testen

### Bringen Sie Ihren eigenen GitHub mit {#byo-github}

Wenn Sie Ihre Repositorys mit GitHub verwalten, [können Sie jetzt Code direkt in Ihren GitHub-Repositorys über Cloud Manager validieren.](/help/managing-code/byo-github.md) Durch diese Integration entfällt die Notwendigkeit, Code ständig mit dem Adobe-Repository zu synchronisieren, und Sie können Pull-Anfragen überprüfen, bevor Sie sie in den Hauptverzweigungen zusammenführen. Diese Funktion ist nur für öffentliche GitHub-Repositorys verfügbar. Unterstützung für selbstgehostetes GitHub-Repositorys ist nicht verfügbar.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-CloudManager_BYOG@adobe.com`.

## Fehlerbehebungen {#bug-fixes}

* Es wurde ein Fehler behoben, bei dem die entsprechenden Protokolle beim Leistungstest nicht generiert wurden, wenn die Fehlerratenmetrik fehlschlug.
* Eine verbesserte Logik innerhalb des Leistungstestdienstes, der fehlende Seiten auf der Site (404) erkennen soll, sorgt jetzt für eine reibungslosere und unterbrechungsfreie Bereitstellung.
