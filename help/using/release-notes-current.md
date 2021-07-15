---
title: Versionshinweise für 2021.7.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.7.0.
feature: Versionshinweise
source-git-commit: 1da4ceef0d89223580800d9018c46aaec51f8927
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 29%

---

# Versionshinweise für 2021.7.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2021.7.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.7.0 wurde am 15. Juli 2021 veröffentlicht.
Die nächste Version ist für den 12. August 2021 geplant.

## Neue Funktionen {#whats-new}

* Kunden können jetzt Azul 8- und 11-JDKs für ihre Cloud Manager-Build-Prozesse verwenden und entweder festlegen, eines dieser JDKs für toolchain-kompatible Maven-Plug-ins *oder* für die gesamte Maven-Prozessausführung zu verwenden.

* Die ausgehende Ausgangs-IP wird jetzt in der Protokolldatei des Buildschritts protokolliert.

* Die Schaltflächen **Git** verwalten wurden umbenannt in **Git-Informationen öffnen** und das Dialogfeld wurde visuell aktualisiert.

* Die Version des AEM Projektarchetyps, der von Cloud Manager verwendet wird, wurde auf Version 28 aktualisiert.

* Einige unerwartete Topologiekonfigurationen konnten dazu führen, dass detaillierte Testberichte nicht mehr auf der Seite mit den Pipelineausführungsdetails verfügbar sind.

## Fehlerbehebungen {#bug-fixes}

* Beim manuellen Navigieren zur Seite mit den Ausführungsdetails für eine nicht vorhandene Ausführung wurde kein Fehler angezeigt, sondern nur ein Bildschirm mit endlosen Ladevorgängen.

* In einigen Fällen würde der automatische Neuversuch für fehlgeschlagene Container, die in der Sites-Leistung verwendet werden, 2 Stunden lang nicht wirksam, was zu einem Testfehler führte.

## Bekannte Probleme {#known-issues}

Kunden, die zur Verwendung der Azul JDKs wechseln, sollten beachten, dass nicht alle vorhandenen Anwendungen ohne Fehler auf Azul JDK kompiliert werden. Es wird dringend empfohlen, vor dem Wechsel lokal zu testen.