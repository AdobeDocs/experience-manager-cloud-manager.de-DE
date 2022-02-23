---
title: Versionshinweise für 2021.3.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.3.0.
feature: Release Information
exl-id: e05b22fe-f071-4b69-9db1-e3d7ee4cfbcc
source-git-commit: 71d44c7e3673ca62fcd2203ecc0bc4ed9fa22002
workflow-type: ht
source-wordcount: '235'
ht-degree: 100%

---

# Versionshinweise für 2021.3.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2021.3.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.3.0 wurde am 11. März 2021 veröffentlicht.
Die nächste Version ist für den 8. April 2021 geplant.

## Neue Funktionen {#whats-new}

* Zur Validierung der Dispatcher-Konfiguration beim Kunden wurde das neue [Dispatcher-Optimierungs-Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/custom-code-quality-rules.html?lang=de#dispatcher-optimization-tool-rules) zur Überprüfung der Code-Qualität eingeführt.

* Benutzer können nun ihre Cloud Manager-Rolle(n) anzeigen, indem sie in der Unified Shell das Symbol „Benutzerprofil“ und dann die Option **Cloud Manager-Rolle(n) anzeigen** auswählen.

* Die Beschriftung **Antrag auf Genehmigung** wurde zur besseren Klarheit in **Produktionsgenehmigung** umbenannt.

* Die Beschriftung **Version** wurde im Bildschirm zur Ausführung der Produktions-Pipeline in **Git-Tag** umbenannt.

* Die Beschriftungen, die das Verhalten definieren, wenn wichtige Metriken den definierten Schwellenwert nicht erreichen, wurden umbenannt, um ihr wahres Verhalten widerzuspiegeln: **Sofort abbrechen** und **Sofort genehmigen**. Weitere Informationen finden Sie unter [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md).

* Die Listen zum Entfernen von Klassen und Methoden wurden auf der Grundlage der Version `2021.3.4997.20210303T022849Z-210225` des AEM Cloud Service SDK aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Einige Qualitätsprobleme wurden nicht richtig erkannt, wenn Pakete in andere Pakete eingebettet waren.

* Wenn der Benutzer unmittelbar nach dem Start einer Pipeline von der Seite zur Pipeline-Ausführung weg navigiert, wird gelegentlich eine Fehlermeldung angezeigt, die besagt, dass die Aktion fehlgeschlagen ist, obwohl die Ausführung tatsächlich startet.
