---
title: Versionshinweise für 2020.11.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.11.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.11.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.11.0.
translation-type: tm+mt
source-git-commit: 30d782f5a095b1b07ec4f2039def9ba30a559325
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 31%

---

# Versionshinweise für 2020.11.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.11.0.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.11.0 is November 12, 2020.

## Neue Funktionen {#whats-new}

* Die Registerkarte &quot; **Lernen** &quot;in Cloud Manager wird mit neuen Bildern in der Benutzeroberfläche aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Bestimmte kundenbedingte Bereitstellungsfehler werden nun explizit in den Bereitstellungsprotokollen angezeigt.

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plugins.

* Über den Link in der Fußzeile von Cloud Manager zur Auswahl einer Sprache navigieren Sie jetzt zum richtigen Speicherort.

* Während der Codeprüfung wird der SonarQube-Vorgang manchmal nicht Beginn. Dies wird nun automatisch erkannt und ein Neustart wird versucht.

* Während des Site-Crawling-Prozesses, der bei Leistungstests verwendet wird, werden Anforderungen, bei denen die Zeitüberschreitung in den ersten drei Stufen der Tiefendurchfahrt erfolgt, automatisch erneut versucht.