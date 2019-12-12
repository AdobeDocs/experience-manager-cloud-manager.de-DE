---
title: Versionshinweise für 2019.12.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.12.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.12.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.12.0.
translation-type: tm+mt
source-git-commit: 1f31e654272afa60cac3376ce4dc3bc76f0d9dda

---

# Versionshinweise für 2019.12.0 {#release-notes-for}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] Release 2019.12.0 and adds updates to pipeline execution and enhancements to code quality scans.
Weitere Informationen erhalten Sie im Folgenden.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.12.0 is December 12, 2019.

## Neuerungen {#whats-new}

* Schritte in der Pipeline-Ausführung zeigen jetzt den Zeitstempel für die Fertigstellung für jeden Schritt an.
* Code-Qualitätsscans für Projekte, die keinen Java-Code enthalten, melden jetzt eine Coverage-Rate von 100 %.
* Der CQ Dispatcher Configuration Health Check wurde entfernt.


## Fehlerbehebungen {#bug-fixes}

* Datumsangaben wurden in bestimmten Browsern nicht korrekt angezeigt.
* In seltenen Fällen würde die Produktionsleitung zum Genehmigungsschritt wechseln, während die Leistungsprüfung noch läuft.
* Bei bestimmten Zuständen wurden die Schaltflächen im oberen Bereich der Übersichtsseite nicht korrekt ausgerichtet.
* Unter bestimmten Umständen sahen unbefugte Benutzer eine Schaltfläche zum Starten der Pipeline, obwohl die Schaltfläche selbst nicht angeklickt werden konnte.
* Die Aktionsschaltflächen für Nicht-Produktionsleitungen werden manchmal am falschen Ort angezeigt.
* Pakete mit dem Knotentyp "granite:Ranking"konnten nicht auf bestimmte Verstöße gegen Qualitätsregeln überprüft werden.
* Bestimmte Fehler im Codequalitätsprozess wurden fälschlicherweise als Fehler gezählt.
* Überwachungsdaten konnten für bestimmte Topologien nicht geladen werden.
