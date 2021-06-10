---
title: Versionshinweise für 2021.6.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.6.0.
feature: Versionshinweise
source-git-commit: 5111a918b8063ab576ef587dc3c8d66ad976fc1a
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 27%

---

# Versionshinweise für 2021.6.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2021.6.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.6.0 wurde am Donnerstag, 10. Juni 2021 veröffentlicht.
Die nächste Version ist für den 15. Juli 2021 geplant.

## Neuigkeiten {#whats-new}

* Assets- und Sites-Tests werden jetzt parallel ausgeführt (sofern zutreffend), wodurch die gesamte Pipeline-Ausführungszeit verkürzt wird. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Maven-Abhängigkeiten, die während des Build-Schritts heruntergeladen wurden, werden jetzt zwischen Pipeline-Ausführungen zwischengespeichert. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Der standardmäßige Zweigname, der sowohl bei der Projekterstellung als auch im Standard-Push-Befehl über Git-Workflows verwalten verwendet wird, wurde in `main` geändert.

* Die Bearbeitung des Programmerlebnisses in der Benutzeroberfläche wurde aktualisiert.

* Die Qualitätsregel `ImmutableMutableMixCheck` wurde aktualisiert, um `/oak:index` -Knoten als unveränderlich zu klassifizieren.

* Die Qualitätsregeln `CQBP-84` und `CQBP-84--dependencies` wurden in einer einzigen Regel zusammengefasst.

* In einigen Situationen würde ein Fehler bei der Berechnung der Metrik &quot;Übersprungene Tests&quot;dazu führen, dass Pipeline-Ausführungen fehlschlagen.

## Fehlerbehebungen {#bug-fixes}

* JCR-Knotendefinitionen, die einen Zeilenumbruch enthalten, nachdem der Stammelementname nicht korrekt analysiert wurde.

* Die List-Repositorys-API filtert keine gelöschten Repositorys.

* Eine falsche Fehlermeldung wurde angezeigt, wenn für den Zeitplanschritt ein ungültiger Wert angegeben wurde.

* In einigen Fällen, in denen die Pipeline-Ausführung die Bereitstellung im Produktionsschritt erreichte und der Benutzer die Ausführung stoppte, spiegelte die Bereitstellungsstatusmeldung in der Benutzeroberfläche nicht richtig wider, was tatsächlich vor sich ging.
