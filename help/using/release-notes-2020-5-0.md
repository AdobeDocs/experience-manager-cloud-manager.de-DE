---
title: Versionshinweise für 2020.5.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.5.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.5.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.5.0.
translation-type: tm+mt
source-git-commit: 0652436ec0c1c95d270a06a600424dbfd0140b27
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 100%

---

# Versionshinweise für 2020.5.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.5.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2020.5.0 wurde am 07. Mai 2020 veröffentlicht.

## Neuerungen {#whats-new}

* Sechs zusätzliche Regeln zur Code-Qualität wurden hinzugefügt, die Kunden bei der Planung einer Migration auf Cloud Service bei der Ermittlung potenzieller Probleme unterstützen.

* Die neue Metrik *Cloud Service-Kompatibilität* wurde hinzugefügt, um die Zahl der Kompatibilitätsprobleme zusammenzufassen.

* Die Leistung der Seite „Aktivität“ und der Pipeline Execution List-API wurde verbessert.

* Das Code-Qualitätsprotokoll enthält jetzt vollständige Stacktraces für Ausnahmen.

## Fehlerbehebungen {#bug-fixes}

* Während der Ausführung der Produktions-Pipeline wurde eine irreführende Karte auf der Übersichtsseite angezeigt.

* Die Code-Qualitätsregel *DontImplementOrExtendProviderTypesPomCheck* rief manchmal eine Nullzeiger-Ausnahme hervor.

* Einige Dokumentations-Links auf der Übersichtsseite funktionierten nicht ordnungsgemäß.

* Auf bestimmten Karten auf der Übersichtsseite wurden die Entitätsnamen nicht korrekt angezeigt.

* Bestimmte Topologiekonfigurationen führten dazu, dass im Performance-Testschritt ein Fehler erzeugt wurde, anstatt die fehlenden Metriken zu melden.
