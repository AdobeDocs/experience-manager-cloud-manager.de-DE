---
title: Versionshinweise für 2021.6.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.6.0.
feature: Versionshinweise
source-git-commit: ee701dd2d0c3921455a0960cbb6ca9a3ec4793e7
workflow-type: ht
source-wordcount: '314'
ht-degree: 100%

---

# Versionshinweise für 2021.6.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2021.6.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.6.0 wurde am 10. Juni 2021 veröffentlicht.
Die nächste Version ist für den 15. Juli 2021 geplant.

## Neue Funktionen {#whats-new}

* Assets- und Sites-Tests werden jetzt parallel ausgeführt (sofern zutreffend), wodurch die gesamte Pipeline-Ausführungszeit verkürzt wird. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Maven-Abhängigkeiten, die während des Build-Schritts heruntergeladen wurden, werden jetzt zwischen Pipeline-Ausführungen zwischengespeichert. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Der standardmäßige Name der Verzweigung, der sowohl bei der Projekterstellung als auch im Standard-Push-Befehl über „Git-Workflows verwalten“ verwendet wird, wurde zu `main` geändert.

* Die Bearbeitung des Programmerlebnisses in der Benutzeroberfläche wurde aktualisiert. Weitere Informationen finden Sie unter [Bearbeiten eines Programms](/help/using/setting-up-program.md#editing-program).

* Die Qualitätsregel `ImmutableMutableMixCheck` wurde aktualisiert, um `/oak:index`-Knoten als unveränderlich zu klassifizieren.

* Die Qualitätsregeln `CQBP-84` und `CQBP-84--dependencies` wurden in einer einzigen Regel zusammengefasst. Im Rahmen dieser Konsolidierung werden beim Überprüfen von Abhängigkeiten Probleme in Abhängigkeiten von Drittanbietern genauer identifiziert, die zur AEM-Laufzeit bereitgestellt werden.

* Ein Fehler bei der Berechnung der Metrik „Übersprungene Tests“ führt nicht mehr dazu, dass Pipeline-Ausführungen fehlschlagen.

## Fehlerbehebungen {#bug-fixes}

* JCR-Knoten-Definitionen, die einen Zeilenumbruch nach dem Namen des Stammelements enthielten, werden jetzt korrekt geparst.

* Die List-Repositorys-API filtert jetzt auch gelöschte Repositorys.

* Wenn für den Zeitplanschritt ein ungültiger Wert angegeben wurde, wird jetzt die richtige Fehlermeldung angezeigt.

* In den Fällen, in denen die Pipeline-Ausführung die Bereitstellung im Produktionsschritt erreichte und der Benutzer die Ausführung stoppte, spiegelt die Bereitstellungsstatusmeldung in der Benutzeroberfläche jetzt korrekt wider, was tatsächlich vor sich ging.
