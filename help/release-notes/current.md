---
title: Versionshinweise für 2023.9.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2023.9.0.
feature: Release Information
source-git-commit: f15a4b739150ee40b6dc48de0fbc20859093c79c
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 57%

---


# Versionshinweise für Cloud Manager Version 2023.9.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2023.9.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2023.9.0 ist der 14. September 2023. Die Veröffentlichung der nächsten Version ist für den 5. Oktober 2023 geplant.

## Fehlerbehebungen {#bug-fixes}

* Wenn ein Programm gelöscht wird, werden alle verknüpften, laufenden Pipelines nun ebenfalls gelöscht.
* Es wurde ein gelegentlicher Fehler behoben, durch den alle Schritte einer Pipelineausführung als abgeschlossen markiert wurden, der Status der Pipeline jedoch weiterhin ausgeführt wurde, was das Erscheinungsbild eines blockierten Status verursachte.
* Ein Fehler wurde behoben, wenn CI/CD-Pipelines für Repository-Verzweigungen, die den Archetyp generierten, fehlschlugen.
