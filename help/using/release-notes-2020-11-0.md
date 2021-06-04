---
title: Versionshinweise für 2020.11.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.11.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.11.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.11.0.
feature: Versionshinweise
exl-id: c283c55d-156f-4540-9353-e6337d185842
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2020.11.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2020.11.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2020.11.0 wurde am 12. November 2020 veröffentlicht.

## Neuigkeiten {#whats-new}

* Die Registerkarte **Lernen** in Cloud Manager wurde mit neuen Bildern in der Benutzeroberfläche aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Bestimmte vom Kunden verursachte Implementierungsfehler werden nun explizit in den Implementierungsprotokollen angezeigt.

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plug-ins.

* Über den Link in der Fußzeile von Cloud Manager zur Sprachauswahl wird jetzt an die richtige Stelle navigiert.

* Manchmal startete der SonarQube-Prozess während des Code-Scannens nicht. Dies wird nun automatisch erkannt und ein Neustart wird versucht.

* Während des Site-Crawling-Prozesses, der beim Leistungstest verwendet wird, werden Anfragen, bei denen in den ersten drei Ebenen der Tiefensuche eine Zeitüberschreitung auftritt, automatisch wiederholt.
