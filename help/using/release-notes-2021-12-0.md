---
title: Versionshinweise für 2021.12.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2021.12.0.
feature: Release Information
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: ht
source-wordcount: '269'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager Version 2021.12.0 {#release-notes}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] Version 2021.12.0.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de)

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2021.12.0 ist der 16. Dezember 2021. Die nächste Version soll im Januar 2022 veröffentlicht werden.

## Neue Funktionen {#whats-new}

* Der Commit-Hash, der bereits in der Benutzeroberfläche sichtbar ist, wird jetzt auch in der API bereitgestellt.
* Die Seite „Aktivitäten“ enthält jetzt ein Popup für die Ausführung von Pipelines, das eine Zusammenfassung der Pipelinedetails auf einen Blick bietet.
* Es wurden Aktualisierungen hinzugefügt, die zusätzliche Details enthalten, die auf der Seite „Aktivitäten“ beschrieben werden.
* Die Registerkarte „Lernen“ in Cloud Manager bietet jetzt schnellen Zugriff auf API-Handbücher und zugehörige Ressourcen.
* Ein Benutzer mit der Rolle „Implementierungs-Manager“ kann jetzt den Erstellungsassistenten für ein Projekt/eine Verzweigung für ein Repository ohne Verzweigungen über das Aktionsmenü auf der Seite „Repositorys“ starten.
* Der Implementierungs-Manager, der sich im Workflow zum Hinzufügen oder Bearbeiten einer Pipeline befindet, wird jetzt darüber informiert, wie eine Verzweigung oder ein Projekt erstellt werden kann, wenn das ausgewählte Repository keine Verzweigungen aufweist.
* Wenn im Fenster „Produktions-Pipeline bearbeiten“ mehr als eine Staging-Umgebung für die Produktion vorhanden ist, ist eine Dropdown-Liste zur Umgebungsauswahl verfügbar.
* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 32 aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Full-Stack-Produktions-Pipelines erhalten weiterhin den Namen „Produktions-Pipeline“, selbst wenn der Benutzer einen anderen Namen in das Namensfeld eingibt.
