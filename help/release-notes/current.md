---
title: Versionshinweise für Cloud Manager 2025.2.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.2.0 in Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 51dd060ec9b922ace9ce537cac669c61154284e8
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 26%

---

# Versionshinweise für Cloud Manager 2025.2.0 in Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.02.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2025.2.0 in Adobe Managed Services.

Siehe auch die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2025.2.0 ist Mittwoch, der Freitag, 13. Februar 2025.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 13. März 2025 geplant.

## Neue Funktionen {#what-is-new}

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

* **Upgrade von SonarQube**

  Ab Donnerstag, dem 13. Februar 2025, verwendet der Cloud Manager-Code-Qualitätsschritt jetzt SonarQube-9.9.5.90363.

  Die aktualisierten Regeln, die für AMS unter [diesem Link](/help/using/code-quality-testing.md#code-quality-testing-step) verfügbar sind, bestimmen die Sicherheitsbewertungen und die Code-Qualität für Cloud Manager-Pipelines.

* SonarQube 9.9 ist jetzt die Standard-Engine zur Überprüfung der Code-Qualität für alle Kunden.

* Unterstützung für **Java 17- und Java 21-Build-Umgebungen**

  Kunden können jetzt optional mit Java 17 oder Java 21 erstellen und von Leistungsverbesserungen und neuen Sprachfunktionen profitieren. Unter [Build-Umgebung](/help/getting-started/build-environment.md) finden Sie Konfigurationsschritte, einschließlich der Aktualisierung Ihrer Maven-Projektbeschreibung und bestimmter Bibliotheksversionen.

  >[!NOTE]
  >Wenn für Cloud Service-Umgebungen die Build-Version Java 17 oder Java 21 ist, wird für die Laufzeit standardmäßig Java 21 verwendet.

* **Inhaltskopie-Validierungen erweitert**

  Die Validierungsregeln für Inhaltskopien wurden aktualisiert. Mit dieser Version können Benutzende keine Inhaltskopie mehr in Trigger nehmen, wenn es aktive Pipeline-Ausführungen in der Quell- oder Zielumgebung gibt. Benutzer müssen warten, bis alle laufenden Pipeline-Ausführungen abgeschlossen sind, bevor sie eine Inhaltskopie starten.

<!-- 
## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features.

### Bring Your Own Git - now with support for GitLab and Bitbucket {#gitlab-bitbucket}

The **Bring Your Own Git** feature has been expanded to include support for external repositories, such as GitLab and Bitbucket. This new support is in addition to the already existing support for private and enterprise GitHub repositories. When you add these new repos, you can also link them directly to your pipelines. You can host these repositories on public cloud platforms or within your private cloud or infrastructure. This integration also removes the need for constant code synchronization with the Adobe repository and provides the ability to validate pull requests before merging them into a main branch.

Pipelines using external repositories (excluding GitHub-hosted ones) and the **Deployment Trigger** set to **On Git Changes** now start automatically.

See [Add external repositories in Cloud Manager](/help/managing-code/external-repositories.md).

![Add Repository dialog box](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Currently, the out-of-the-box pull request code quality checks are exclusive to GitHub-hosted repositories, but an update to extend this functionality to other Git vendors is in the works.

If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
