---
title: Versionshinweise für 2019.8.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.8.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.8.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur Version 2019.8.0 von AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 365cd6dfe65059c0c529f774bbcda946d47b0db5

---

# Versionshinweise für 2019.8.0 {#release-notes-for}

Die [!UICONTROL Cloud Manager] 2019.8.0-Version unterstützt die Unterstützung von strukturierten Inhalten, verbessert die Leistung und behebt eine Vielzahl von kleineren Fehlern.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.8.0 wurde am 19. August 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Neue Befehlszeilenschnittstelle zur Cloud Manager-API, powered by [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Bestimmte durch den Build erzeugte Inhaltspakete können als übersprungen deklariert werden und werden nicht bereitgestellt. Weitere Informationen finden Sie unter ***Überspringen von Inhaltspaketen*** in AEM [-Anwendungsprojekt](create-an-application-project.md) erstellen.
* Der Satz vorab geladener Abhängigkeiten im Build-Container wurde überarbeitet, um einige unbenötigte Netzwerkanforderungen zu vermeiden.
* Die Meldung auf der Übersichtsseite für bestimmte falsch konfigurierte Programme wurde verbessert.

## Fehlerbehebungen {#bug-fixes}

* Beim Zugriff auf SLA-Berichte war das Standardjahr 2018, nicht 2019.
* Bei langen Umgebungen wurde die Umgebungsauswahl im Bildschirm "Berichte" nicht ordnungsgemäß vergrößert.
* Die Codequalitätsregel ***configandinstallshouldonlycontainosginodes*** wurde falsch erzeugt, wenn die Sling-Rewriter-Komponente verwendet wurde.
* Die Codequalitätsregel ***configandinstallshouldonlycontainosginodes*** wurde falsch für bestimmte ungewöhnliche Pfadstrukturen erzeugt.
* Nur Assets konnten nicht ständig in ihre AEM-Umgebungen navigieren.
* Das [!UICONTROL Dialogfeld Verzweigung und Projekt] erstellen wird in verschiedenen Browsern unterschiedlich dargestellt.
