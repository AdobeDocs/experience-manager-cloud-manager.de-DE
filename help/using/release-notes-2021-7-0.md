---
title: Versionshinweise für 2021.7.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.7.0.
feature: Versionshinweise
source-git-commit: e490a8f1dd17e63f35ed00d4cdf95b6e7a07b150
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 100%

---

# Versionshinweise für 2021.7.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] Version 2021.7.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.7.0 wurde am 15. Juli 2021 veröffentlicht.
Die nächste Version wird am 12. August 2021 veröffentlicht.

## Neue Funktionen {#whats-new}

* Kunden können jetzt Azul 8- und 11-JDKs für ihre Cloud Manager-Build-Prozesse verwenden und entweder festlegen, eines dieser JDKs für Toolchain-kompatible Maven-Plug-ins *oder* für die gesamte Maven-Prozessausführung zu verwenden.

* Die ausgehende Austritts-IP wird jetzt in der Protokolldatei des Build-Schritts protokolliert.

* Die Schaltfläche **Git verwalten** wurde in **Git-Info öffnen** umbenannt und das Dialogfeld wurde visuell überarbeitet.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 28 aktualisiert.

* Einige unerwartete Topologie-Rekonfigurationen konnten dazu führen, dass detaillierte Testberichte nicht mehr auf der Seite mit den Pipeline-Ausführungsdetails verfügbar waren.

## Fehlerbehebungen {#bug-fixes}

* Beim manuellen Navigieren zur Seite mit den Ausführungsdetails für eine nicht vorhandene Ausführung wird nicht mehr ein Bildschirm mit endlosen Ladevorgängen, sondern ein Fehler angezeigt.

* In einigen Fällen wurde der automatische Neuversuch für fehlgeschlagene Container, die in der Sites-Leistung verwendet werden, 2 Stunden lang nicht wirksam, was zu einem Testfehler führte.

## Bekannte Probleme {#known-issues}

Kunden, die zur Verwendung der Azul-JDKs wechseln, sollten beachten, dass nicht alle vorhandenen Anwendungen ohne Fehler auf Azul-JDK kompiliert werden. Es wird dringend empfohlen, vor dem Wechsel lokal zu testen.