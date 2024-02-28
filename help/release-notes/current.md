---
title: Versionshinweise für 2024.2.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2024.2.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: cc87246503ab63d6dd60c691f15fc4759fcf6939
workflow-type: ht
source-wordcount: '299'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2024.2.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2024.2.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2024.2.0 ist der 15. Februar 2024. Die Veröffentlichung der nächsten Version ist für den 16. März 2024 geplant.

## Neue Funktionen {#what-is-new}

* Im Rahmen der [Bereitstellung](/help/using/code-deployment.md) des Dispatcher-Cache wurde der Schritt **Dispatcher anhängen** entfernt. Um Änderungen an jedem Knoten testen zu können, bevor dieser an den Anwendungs-Lastenausgleich angehängt wird, können Sie nach der Bereitstellung von Code für einen bestimmten Publisher Änderungen direkt über den zugehörigen Dispatcher testen, bevor Sie diesen Dispatcher an den Lastenausgleich anhängen.
* [Die Build-Umgebung](/help/getting-started/build-environment.md) wurde auf die Maven-Version 3.9.4 und die JDK-Versionen jdk-11.0.22 und jdk1.8.0_401 aktualisiert.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie an unserem Early-Adopter-Programm teil und nutzen Sie die Möglichkeit, einige zukünftige Funktionen zu testen

### Bringen Sie Ihren eigenen GitHub mit {#byo-github}

Wenn Sie Ihre Repositorys mit GitHub verwalten, [können Sie jetzt Code direkt in Ihren GitHub-Repositorys über Cloud Manager validieren.](/help/managing-code/byo-github.md) Durch diese Integration entfällt die Notwendigkeit, Code ständig mit dem Adobe-Repository zu synchronisieren, und Sie können Pull-Anfragen überprüfen, bevor Sie sie in den Hauptverzweigungen zusammenführen. Diese Funktion ist nur für öffentliche GitHub-Repositorys verfügbar. Unterstützung für selbstgehostetes GitHub-Repositorys ist nicht verfügbar.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-CloudManager_BYOG@adobe.com`.

## Fehlerbehebungen {#bug-fixes}

* Das JDK der Build-Container wurde auf eine Version aktualisiert, die [JDK-8313765](https://bugs.openjdk.org/browse/JDK-8313765) auflöst.
§