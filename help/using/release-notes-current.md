---
title: Versionshinweise für 2021.12.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2021.12.0.
feature: Release Information
source-git-commit: 910def6d82c09e0220a50a3cb34a61f2c7284cb9
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 3%

---

# Versionshinweise für Cloud Manager - Version 2021.12.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!UICONTROL Cloud Manager] Version 2021.12.0.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager AEM as a Cloud Service finden Sie unter [Cloud Manager in den aktuellen Versionshinweisen AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] Version 2021.12.0 wurde am 16. Dezember 2021 veröffentlicht. Die nächste Version ist für Januar 2022 geplant.

## Neue Funktionen {#whats-new}

* Der Commit-Hash, der bereits in der Benutzeroberfläche sichtbar ist, wird jetzt auch in der API bereitgestellt.
* Die Seite &quot;Aktivität&quot;enthält jetzt ein Popup für die Ausführung von Pipelines, das eine Zusammenfassung der Pipelinedetails auf einen Blick bietet.
* Es wurden Aktualisierungen hinzugefügt, die zusätzliche Details enthalten, die auf der Seite Aktivitäten beschrieben werden.
* Die Registerkarte &quot;Lernen&quot;in Cloud Manager bietet jetzt schnellen Zugriff auf API-Handbücher und zugehörige Ressourcen.
* Ein Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;kann jetzt den Erstellungsassistenten für ein Projekt/eine Verzweigung für ein Repository ohne Verzweigungen über das Aktionsmenü auf der Seite &quot;Repositorys&quot;starten.
* Der Bereitstellungsmanager, der sich im Workflow zum Hinzufügen oder Bearbeiten von Pipeline befindet, wird jetzt darüber informiert, wie eine Verzweigung oder ein Projekt erstellt werden kann, wenn das ausgewählte Repository keine Verzweigungen aufweist.
* Wenn im Fenster &quot;Produktions-Pipeline bearbeiten&quot;mehr als eine Staging-Umgebung für die Produktion vorhanden ist, ist eine Dropdown-Liste zur Umgebungsauswahl verfügbar.

## Fehlerbehebungen {#bug-fixes}

* Produktions-Pipelines mit vollständigem Stapel erhalten weiterhin den Namen &quot;Produktions-Pipeline&quot;, selbst wenn der Benutzer einen anderen Namen in das Namensfeld eingibt.
