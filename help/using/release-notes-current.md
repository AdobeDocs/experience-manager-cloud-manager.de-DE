---
title: Versionshinweise für 2022.3.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.3.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 4a5ddf3144ec50f1a7a4ac367b5c99bc9b486752
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 28%

---


# Versionshinweise für Cloud Manager Version 2022.3.0 {#release-notes}



>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

 The next release is planned for 7 April 2022.

## Neue Funktionen {#what-is-new}

* Outbounds HTTP requests from asset tests will now come from a Fixed IP range.


## Fehlerbehebungen {#bug-fixes}

* ****
* ********
* A subset of git repositories created manually had an incorrect name value which prevented the build artifact reuse feature from being effective. The names of those repositories have been changed and users will see the corrected name in the Cloud Manager API/UI.
* Build artifacts from non-production pipelines were inappropriately reused on production full stack pipelines.
* When adding or editing a code quality pipeline, the options to handle metric failures is no longer displayed.
* Some unexpected pipeline variable configurations could cause in the build step.
