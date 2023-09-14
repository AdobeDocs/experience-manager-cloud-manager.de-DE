---
title: Versionshinweise für 2023.9.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2023.9.0.
feature: Release Information
source-git-commit: a3e926fa13d54da1322f3a5219519fae07ddb273
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 52%

---


# Versionshinweise für Cloud Manager Version 2023.9.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2023.9.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2023.9.0 ist der 14. September 2023. Die Veröffentlichung der nächsten Version ist für den 5. Oktober 2023 geplant.

## Neue Funktionen {#what-is-new}

* Diese Version besteht aus Fehlerbehebungen, die nur für Cloud Manager verfügbar sind.

## Fehlerbehebungen {#bug-fixes}

* Wenn ein Programm gelöscht wird, werden auch alle verknüpften, laufenden Pipelines gelöscht, um sicherzustellen, dass die Pipeline nicht fälschlicherweise als fehlgeschlagen gekennzeichnet ist.
* Wenn alle Schritte einer Pipeline-Ausführung &quot;abgeschlossen&quot;sind, wird der Status der Pipeline gelegentlich als &quot;ausgeführt&quot;betrachtet, sodass sie sich in einem blockierten Zustand zu befinden scheint. Es wird nun als &quot;vollständig&quot;bezeichnet.
* Bei Repository-Verzweigungen, die mit dem Code-Generator-Archetyp generiert wurden, schlägt die CI/CD-Pipeline fehl.
