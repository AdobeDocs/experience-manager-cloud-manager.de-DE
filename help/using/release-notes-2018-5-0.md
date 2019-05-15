---
title: Versionshinweise für 2018.5.0
seo-title: Versionshinweise für AEM Cloud Manager 2018.5.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2018.5.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2018.5.0.
uuid: 37f8b155-6984-454d-83a8-3f5fb081be97
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: Versionshinweise
discoiquuid: 6d1e7098-b56e-4172-8373-486f186f3d53
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Versionshinweise für 2018.5.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2018.5.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2018.5.0 wurde am 12. Juli 2018 veröffentlicht.

## Neuigkeiten {#what-s-new}

* **CI/CD-Pipelinebenachrichtigungen**: Anwender sehen nun [!UICONTROL Experience Cloud]-Benachrichtigungen für Pipelineereignisse. Weitere Informationen finden Sie unter [Benachrichtigungen](notifications.md).

* **Geplante Produktionsbereitstellungen**: Anwender können nun ein Datum oder eine Uhrzeit für Produktionsbereitstellungen festlegen. Weitere Informationen finden Sie unter [Bereitstellen von Code](deploying-code.md).

* Die Seite **Status** wurde in **Aktivität** umbenannt.

* Wenn Probleme bei der Pipelineausführung auftreten, werden nun genauere Informationen auf der Startseite angezeigt.
* Die Infrastruktur für Leistungstests wurde verbessert.

## Fehlerbehebungen {#bug-fixes}

* Unter bestimmten Umständen wurde das falsche SonarQube-Profil verwendet, was zu fehlerhaften Metriken bei der Codequalität führte.
* Bei der SonarQube-Prüfung CQBP-75 wurden bestimmte OSGi-Anmerkungen ignoriert.
* Beim Abbruch der CI/CD-Pipeline wurde der Status nicht konsistent angezeigt.

## Bekannte Probleme {#known-issues}

* Die Links zu **AEM** und **Überwachung** auf dem Bildschirm „Programmliste“ ersetzen die aktuelle Browserregisterkarte und rufen eine neue Registerkarte auf.

