---
title: Wissenswertes zu Testergebnissen
seo-title: Wissenswertes zu Testergebnissen
description: Erfahren Sie mehr über drei Stufen beim Ausführen einer Pipeline in Cloud Manager
seo-description: Auf dieser Seite erfahren Sie mehr über dreistufige Akzeptanztests beim Ausführen von Pipelines, Codescans sowie Leistungs- und Sicherheitstests zur Validierung Ihres Programms in Cloud Manager.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
feature: CI-CD-Pipeline, Testergebnisse
translation-type: tm+mt
source-git-commit: 12a7d6199983e2d19ef401051f60e3f24bb6d4f8
workflow-type: tm+mt
source-wordcount: '2691'
ht-degree: 68%

---


# Wissenswertes zu Testergebnissen {#understand-your-test-results}

Während der Pipeline-Ausführung werden verschiedene Metriken erfasst und entweder mit den vom Business Owner definierten KPIs (Key Performance Indicators) oder mit den von Adobe Managed Services festgelegten Standards verglichen.

Die entsprechende Berichterstattung erfolgt über ein dreistufiges Gatingsystem, so wie in diesem Abschnitt definiert.

## Dreistufige Akzeptanztests bei der Pipelineausführung {#three-tier-gates-while-running-a-pipeline}

Die Pipeline muss drei Akzeptanztests bestehen:

* Codequalität
* Leistungstests
* Sicherheitstests

Für jeden dieser Akzeptanztests gibt es eine dreistufige Struktur für vom Test identifizierte Probleme.

* **Kritisch**: Hierbei handelt es sich um vom Test identifizierte Probleme, die zu einem sofortigen Pipelinefehler führen.
* **Wichtig**: Hierbei handelt es sich um vom Test identifizierte Probleme, durch die die Pipeline angehalten wird. Bereitstellungsmanager, Projektmanager oder Business Owner können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.
* **Info**: Hierbei handelt es sich um vom Test identifizierte Probleme, die ausschließlich zu Informationszwecken bereitgestellt werden und keine Auswirkungen auf die Pipelineausführung haben.

>[!NOTE]
>
>In einer Pipeline nur für Code-Qualität können Fehler der Kategorie „Wichtig“ des Code-Qualitätstests nicht überschrieben werden, da dieser Test der letzte Schritt in der Pipeline ist.

## Testen der Code-Qualität {#code-quality-testing}

Dieser Schritt bewertet die Qualität Ihres Anwendungs-Codes. Dabei handelt es sich um das Kernziel einer reinen Code-Qualitäts-Pipeline, die unmittelbar nach dem Erstellungsschritt in allen Nichtproduktions- und Produktions-Pipelines ausgeführt wird. Weitere Informationen zu den verschiedenen Pipelines finden Sie unter [Konfigurieren Ihrer CI/CD-Pipeline](/help/using/configuring-pipeline.md).

### Wissenswertes zum Testen der Code-Qualität {#understanding-code-quality-testing}

Beim Testen der Code-Qualität wird der Quellcode gescannt, um sicherzustellen, dass er bestimmte Qualitätskriterien erfüllt. Derzeit wird dies durch eine Kombination aus SonarQube, Prüfung auf Inhaltspaket-Ebene mit OakPAL und Dispatcher-Validierung mit dem Dispatcher Optimization Tool implementiert. Es gibt über 100 Regeln, die generische Java-Regeln und AEM-spezifische Regeln kombinieren. Einige der AEM-spezifischen Regeln werden auf der Grundlage der Best Practices von AEM Engineering erstellt und werden als [benutzerspezifische Code-Qualitätsregeln](/help/using/custom-code-quality-rules.md) bezeichnet.

>[!NOTE]
>Sie können die vollständige Liste der Regeln [hier](/help/using/assets/CodeQuality-rules-AMS.xlsx) herunterladen.

Die Ergebnisse dieses Schritts werden als *Bewertung* bereitgestellt. Die nachstehende Tabelle fasst die Bewertungen für verschiedene Prüfkriterien zusammen:

| Name | Definition | Kategorie | Fehlerschwellenwert |
|--- |--- |--- |--- |
| Sicherheitsbewertung | A = 0 Schwachstellen <br/>B = mindestens 1 kleinere Schwachstelle<br/> C = mindestens 1 größere Schwachstelle <br/>D = mindestens 1 kritische Schwachstelle <br/>E = mindestens 1 Schwachstelle der Kategorie „Blocker“ | Kritisch | &lt; B |
| Zuverlässigkeitsbewertung | A = 0 Fehler <br/>B = mindestens 1 kleinerer Fehler <br/>C = mindestens 1 größerer Fehler <br/>D = mindestens 1 kritischer Fehler E = mindestens 1 Fehler der Kategorie „Blocker“<br/> | Wichtig | &lt; C |
| Wartbarkeitsbewertung | Wenn die ausstehenden Kosten zur Code-Smell-Behebung …<br/><ul><li>&lt;= 5 % der Zeit ausmachen, die bereits in die Anwendung investiert wurde, lautet die Bewertung A. </li><li>zwischen 6 und 10 % dieser Zeit ausmachen, lautet die Bewertung B. </li><li>zwischen 11 und 20 % dieser Zeit ausmachen, lautet die Bewertung C. </li><li>zwischen 21 und 50 % dieser Zeit ausmachen, lautet die Bewertung D.</li><li>mehr als 50 % dieser Zeit ausmachen, lautet die Bewertung E.</li></ul> | Wichtig | &lt; A |
| Abdeckung | Mix aus Zeilen- und Bedingungsabdeckung mit dieser Formel: <br/>`Coverage = (CT + CF + LC)/(2*B + EL)`<br/> Dabei gilt Folgendes: CT = Bedingungen, bei denen die Auswertung während der Durchführung von Unit-Tests mindestens einmal „true“ ergeben hat <br/>CF = Bedingungen, bei denen die Auswertung während der Durchführung von Unit-Tests mindestens einmal „false“ ergeben hat <br/>LC = abgedeckte Zeilen = abzudeckende_Zeilen - nicht_abgedeckte_Zeilen <br/><br/> B = Gesamtanzahl der Bedingungen <br/>EL = Gesamtzahl ausführbarer Zeilen (abzudeckende_Zeilen) | Wichtig | &lt; 50% |
| Übersprungene Unit-Tests | Zahl der übersprungenen Unit-Tests | Info | > 1 |
| Offene Probleme | Allgemeine Problemtypen – Schwachstellen (Vulnerability), Fehler (Bug) und Code-Smells (Code Smell) | Info | > 0 |
| Duplizierte Zeilen | Anzahl der Zeilen, die an duplizierten Blöcken beteiligt sind. <br/>Voraussetzungen, damit ein Codeblock als dupliziert gilt: <br/><ul><li>**Nicht-Java-Projekte:**</li><li>Es sollte mindestens 100 aufeinanderfolgende und duplizierte Token geben.</li><li>Diese Token sollten sich mindestens wie folgt verteilen: </li><li>30 Codezeilen für COBOL </li><li>20 Codezeilen für ABAP </li><li>10 Codezeilen für andere Sprachen</li><li>**Java-Projekte:**</li><li> Unabhängig von der Anzahl der Token und Zeilen sollte es mindestens 10 aufeinanderfolgende und duplizierte Anweisungen geben.</li></ul> <br/>Unterschiede bei Einzügen sowie Zeichenfolgenliteralen werden beim Erkennen von Duplizierungen ignoriert. | Info | > 1% |
| Kompatibilität mit Cloud Service | Anzahl der festgestellten Kompatibilitätsprobleme mit Cloud Service. | Info | > 0 |


>[!NOTE]
>
>Genauere Definitionen finden Sie unter [Metrikdefinitionen](https://docs.sonarqube.org/display/SONAR/Metric+Definitions).

>[!NOTE]
>
>Weitere Informationen zu den benutzerdefinierten Regeln zur Code-Qualität, die von [!UICONTROL Cloud Manager] ausgeführt werden, finden Sie unter [Benutzerspezifische Regeln für Code-Qualität](custom-code-quality-rules.md).

### Umgang mit falsch positiven Werten {#dealing-with-false-positives}

Das Verfahren zur Qualitätsprüfung ist nicht perfekt. Mitunter werden fälschlicherweise Probleme identifiziert, die eigentlich nicht problematisch sind. Dies wird als „falsch positiv“ bezeichnet.

In diesen Fällen kann der Quellcode mit der standardmäßigen `@SuppressWarnings`-Java-Anmerkung kommentiert werden. Dabei wird die Regel-ID als Anmerkungsattribut angegeben. Ein häufiges Problem besteht etwa darin, dass die SonarQube-Regel zur Erkennung hartcodierter Kennwörter in Bezug auf die Identifizierung eines hartcodierten Kennworts „aggressiv“ sein kann.

Sehen wir uns ein konkretes Beispiel mit Code an, der in AEM-Projekten relativ häufig vorkommt, wenn eine Verbindung zu einem externen Service hergestellt werden soll:

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube weist dann auf eine Schwachstelle der Kategorie „Blocker“ hin. Nach Prüfung des Codes erkennen Sie, dass es sich nicht um eine Schwachstelle handelt, und kommentieren dies mit der entsprechenden Regel-ID.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Aber was wäre bei diesem Code?

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dann bestünde die richtige Lösung darin, das hartcodierte Kennwort zu entfernen.

>[!NOTE]
>
>Obwohl sich möglichst spezifische `@SuppressWarnings`-Anmerkungen bewährt haben, also nur eine bestimmte Anweisung oder den Block zu kommentieren, der das Problem verursacht, können Anmerkungen auf Klassenebene hinzugefügt werden.

## Sicherheitstests {#security-testing}

[!UICONTROL Cloud Manager] führt die vorhandenen ***AEM-Sicherheits-Konsistenzprüfungen*** beim Staging nach der Bereitstellung aus und meldet den Status über die UI. Die Ergebnisse werden aus allen AEM-Instanzen in der Umgebung aggregiert.

Diese gleichen Health Checks können jederzeit über die Web-Konsole oder das Operations-Dashboard ausgeführt werden.

Wenn eine der **Instanzen** einen Fehler bei einer bestimmten Konsistenzprüfung meldet, schlägt die Konsistenzprüfung für die gesamte **Umgebung** fehl. Wie Codequalitäts- und Leistungstests sind diese Konsistenzprüfungen in Kategorien unterteilt und die zugehörigen Berichte werden über das dreistufige Gatingsystem erstellt. Der einzige Unterschied besteht darin, dass im Falle von Sicherheitstests keine Schwellenwerte vorhanden sind. Alle Konsistenzprüfungen werden entweder bestanden oder schlagen fehl.

In der folgenden Tabelle finden Sie die derzeit verfügbaren Prüfungen:

| **Name** | **Implementierung der Konsistenzprüfung** | **Kategorie** |
|---|---|---|
| Deserialisierungs-Firewall-Attach-API-Bereitschaft befindet sich in einem akzeptablen Zustand | [Deserialisierungs-Firewall-Attach-API-Bereitschaft](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | Kritisch |
| Deserialisierungs-Firewall ist funktionsfähig | [Deserialisierungs-Firewall funktionsfähig](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | Kritisch |
| Deserialisierungs-Firewall wird geladen | [Deserialisierungs-Firewall geladen](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=en#security) | Kritisch |
| Die AuthorizableNodeName-Implementierung stellt keine autorisierbare ID im Knotennamen/Pfad offen. | [Namenserstellung für autorisierbare Knoten](https://experienceleague.adobe.com/docs/experience-manager-64/administering/security/security-checklist.html?lang=en#security) | Kritisch |
| Standardkennwörter wurden geändert | [Standard-Anmeldekonten](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=en#users-and-groups-in-aem) | Kritisch |
| Sling-Standard-GET-Servlet ist vor DOS-Angriffen geschützt. | Sling Get Servlet | Kritisch |
| Der Sling Java Script Handler ist angemessen konfiguriert. | Sling Java Script Handler | Kritisch |
| Der Sling JSP Script Handler ist angemessen konfiguriert. | Sling JSP Script Handler | Kritisch |
| SSL ist richtig konfiguriert | SSL-Konfiguration | Kritisch |
| Keine offensichtlich unsicheren Benutzerprofil-Richtlinien gefunden | Standardzugriff auf Benutzerprofil | Kritisch |
| Der Sling Referrer-Filter ist konfiguriert, um CSRF-Angriffe zu verhindern. | [Sling Referrer-Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=en#security) | Wichtig |
| Der Adobe Granite HTML Library Manager ist angemessen konfiguriert. | Konfiguration des CQ-HTML-Bibliotheksmanagers | Wichtig |
| CRXDE-Support-Bundle ist deaktiviert | CRXDE-Support | Wichtig |
| Sling DavEx Bundle und Servlet sind deaktiviert | DavEx-Konsistenzprüfung | Wichtig |
| Beispielinhalt ist nicht installiert. | Pakete mit Beispielinhalt | Wichtig |
| Sowohl der WCM-Anfrage-Filter als auch der WCM-Debug-Filter sind deaktiviert | [WCM-Filterkonfiguration](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html?lang=en#configuring) | Wichtig |
| Sling WebDAV Bundle und Servlet sind angemessen konfiguriert | WebDAV-Konsistenzprüfung | Wichtig |
| Der Webserver ist so konfiguriert, dass Clickjacking verhindert wird | Webserver-Konfiguration | Wichtig |
| Die Replikation verwendet nicht den Benutzer „admin“ | Benutzerreplikation und -transport | Info |

## Leistungstests {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager führt Leistungstests für AEM Sites-Programm aus. Der Leistungstest wird für ca. 30 Minuten ausgeführt, indem virtuelle Benutzer (Container) hochgeklappt werden, die den tatsächlichen Benutzern den Zugriff auf Seiten auf der Stage-Umgebung simulieren und Traffic simulieren. Diese Seiten werden mit einem Crawler gefunden.

1. **Virtuelle Benutzer**

   Die Anzahl der virtuellen Benutzer oder Container, die von Cloud Manager hochgeladen werden, wird von den KPIs (Antwortzeit und Seitenansichten/min) gesteuert, die der Benutzer in der Rolle &quot;Geschäftsinhaber&quot;beim Erstellen oder Bearbeiten des Programms [definiert. ](setting-up-program.md) Je nach definierten KPIs werden bis zu 10 Container, die die tatsächlichen Benutzer simulieren, hochgespielt. Die für Tests ausgewählten Seiten werden aufgeteilt und jeder virtuellen Seite zugewiesen.

1. **Crawler**

   Vor dem Beginn des 30-minütigen Testzeitraums durchsucht Cloud Manager die Staging-Umgebung anhand einer oder mehrerer vom Customer Success Engineer konfigurierten Seed-URLs. Ausgehend von diesen URLs wird der HTML-Code jeder Seite überprüft und Links werden breitenorientiert durchsucht. Dieser Crawling-Vorgang ist auf maximal 5.000 Seiten beschränkt. Für Anfragen des Crawlers gilt ein festes Zeitlimit von 10 Sekunden.

1. **Seitensätze zum Testen**

   Die Seiten werden nach drei Seitensätzen ausgewählt. Cloud Manager verwendet die Zugriffsprotokolle der AEM Instanzen in Produktion und Phase, um die folgenden drei Behälter zu ermitteln:

   * *Beliebte Live-Seiten*: Diese Option wird ausgewählt, um sicherzustellen, dass die bevorzugten Seiten, auf die Live-Kunden zugreifen, getestet werden. Cloud Manager liest das Zugriffsprotokoll und ermittelt die 25 am häufigsten aufgerufenen Seiten von Live-Kunden, um eine Liste von top `Popular Live Pages` zu generieren. Die Schnittmenge dieser ebenfalls in Stage vorhandenen Elemente wird dann auf der Umgebung der Bühne durchsucht.

   * *Andere Live-Seiten*: Diese Option wird ausgewählt, um sicherzustellen, dass die Seiten, die nicht zu den 25 beliebtesten Live-Seiten gehören, die möglicherweise nicht bevorzugt, aber zum Testen wichtig sind, getestet werden. Ähnlich wie populäre Live-Seiten werden diese aus dem Zugriffsprotokoll extrahiert und müssen auch auf der Bühne vorhanden sein.

   * *Neue Seiten*: Diese Option ist aktiviert, um neue Seiten zu testen, die möglicherweise nur auf der Bühne bereitgestellt wurden und noch nicht zur Produktion gehören, aber getestet werden müssen.

      **Verteilung des Traffics auf die ausgewählten Seitensätze**

      Sie können zwischen einem und allen drei Sätzen auf der Registerkarte &quot;Testen&quot;Ihrer Pipeline-Konfiguration wählen (Link &quot;Einfügen&quot;). Die Verteilung des Traffics basiert auf der Anzahl der ausgewählten Sätze, d. h. wenn alle drei Sätze ausgewählt sind, entfallen je 33 % aller Seitenansichten auf jeden Satz, bei zwei Sätzen sind es 50 % und bei einem ausgewählten Satz entfallen 100 % des Traffics auf diesen Satz.

      Nehmen wir beispielsweise an, es gibt eine Aufteilung von 50 % - 50 % zwischen dem Satz &quot;Beliebte Live-Seiten&quot;und &quot;Neue Seiten&quot;(in diesem Beispiel werden keine anderen Live-Seiten verwendet) und der Satz &quot;Neue Seiten&quot;enthält 3000 Seiten. ist für die KPI der Seitenansichten pro Minute ein Wert von 200 festgelegt. Für den 30-minütigen Testzeitraum gilt in diesem Fall:

      * Jede der 25 Seiten der beliebten Live-Seiten wird 120-mal aufgerufen: ((200 * 0,5) / 25) * 30 = 120

      * Jede der 3000 Seiten der neuen Seiten wird einmal aufgerufen: ((200 * 0,5) / 3000) * 30 = 1

#### Test und Berichte {#testing-reporting}

Cloud Manager führt Leistungstests für AEM Sites-Programm durch, indem Seiten (standardmäßig als nicht authentifizierter Benutzer) für einen 30-minütigen Testzeitraum auf dem Bereitstellungsserver angefordert und die (virtuellen) benutzergenerierten Metriken (Antwortzeit, Fehlerrate, Ansichten pro Minute usw.) gemessen werden. für jede Seite sowie verschiedene Metriken auf Systemebene (CPU, Arbeitsspeicher, Netzwerkdaten) für alle Instanzen.\
Die folgende Tabelle fasst die Leistungstestmetriken mit dem dreistufigen Messsystem in Bezug auf a vis zusammen:

In der folgenden Tabelle finden Sie eine Zusammenfassung der Leistungstestmatrix anhand des dreistufigen Gatingsystems:

| **Metrik** | **Kategorie** | **Fehlerschwellenwert** |
|---|---|---|
| Seitenanforderungsfehlerrate % | Kritisch | >= 2% |
| CPU-Auslastungsrate | Kritisch | >= 80% |
| Festplatten-I/O-Wartezeit | Kritisch | >= 50% |
| 95. Perzentil der Reaktionszeit | Wichtig | >= KPI auf Programmebene |
| Spitzenreaktionszeit | Wichtig | >= 18 Sekunden |
| Seitenaufrufe pro Minute | Wichtig | &lt; KPI auf Programmebene |
| Festplatten-Bandbreitenauslastung | Wichtig | >= 90% |
| Netzwerk-Bandbreitenauslastung | Wichtig | >= 90% |
| Anforderungen pro Minute | Info | >= 6.000 |

Weitere Informationen zur Verwendung der einfachen Authentifizierung für Leistungstests für Sites und Assets finden Sie im folgenden Abschnitt **Authentifizierte Leistungstests**.

>[!NOTE]
>Jede Instanz wird während des Testzeitraums sowohl für die Veröffentlichung als auch für den Autor überwacht. Wenn keine Metrik für eine Instanz abgerufen wird, wird diese Metrik als unbekannt gemeldet und der entsprechende Schritt schlägt fehl.

#### Authentifizierte Leistungstests {#authenticated-performance-testing}

Diese Funktion ist optional.
AMS-Kunden mit authentifizierten Websites können einen Benutzernamen und ein Kennwort angeben, mit denen Cloud Manager während des Sites-Leistungstests auf die Website zugreift.
Benutzername und Kennwort werden als Pipeline-Variablen mit den Namen `CM_PERF_TEST_BASIC_USERNAME` und `CM_PERF_TEST_BASIC_PASSWORD` angegeben.
Obwohl dies nicht unbedingt erforderlich ist, wird empfohlen, den Variablentyp String für den Benutzernamen und den Variablentyp secretString für das Kennwort zu verwenden. Wenn beide angegeben sind, enthält jede Anfrage des Leistungstest-Crawlers und der virtuellen Testbenutzer diese Anmeldedaten als einfache HTTP-Standardauthentifizierung.

Um diese Variablen mithilfe der Cloud Manager-Befehlszeilenschnittstelle festzulegen, führen Sie Folgendes aus:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Informationen zur Verwendung der API finden Sie unter [Variablen](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables).

### AEM Assets {#aem-assets}

Cloud Manager führt Leistungstests für AEM Assets-Programm durch, indem Assets für einen 30-minütigen Testzeitraum wiederholt hochgeladen werden.

1. **Onboarding-Anforderung**

   Bei Assets-Leistungstests erstellt Ihr Customer Success Engineer während des Einstiegs der Author to Stage-Umgebung einen `cloudmanager`-Benutzer (und -Kennwort). Für die Leistungstestschritte muss der Benutzer `cloudmanager` und das zugehörige Kennwort von Ihrer CSE eingerichtet werden. Dies sollte weder aus dem Autor entfernt noch in Berechtigungen geändert werden. Dies führt wahrscheinlich zu einem Fehler beim Assets-Leistungstest.

1. **Bilder und Assets zum Testen**

   Kunden können ihre eigenen Assets zum Testen hochladen. Dies kann bei der Pipeline-Einrichtung oder auf dem Bildschirm „Bearbeiten“ festgelegt werden. Dabei werden typische Bildformate wie JPEG, PNG, GIF und BMP sowie Photoshop-, Illustrator- und Postscript-Dateien unterstützt. Wenn jedoch keine Bilder hochgeladen werden, verwendet Cloud Manager zum Testen ein Standardbild und ein PDF-Dokument.

1. **Verteilung von Assets für Tests**

   Die Verteilung der Anzahl der Assets jedes Typs, die pro Minute hochgeladen werden, wird bei der Pipeline-Einrichtung oder auf dem Bildschirm „Bearbeiten“ festgelegt.
Die unten stehende Abbildung zeigt beispielsweise eine Aufteilung von 70:30. Pro Minute werden 10 Assets hochgeladen, davon 7 Bilder und 3 Dokumente.

1. **Tests und Berichte**

   Cloud Manager erstellt einen Ordner auf der Autoreninstanz, wobei der Benutzername und das Kennwort vom CSE aus Schritt 1 (Onboarding Requirements) wie oben erwähnt festgelegt werden, und lädt Assets mithilfe einer Open-Source-Bibliothek in den Ordner hoch. Die vom Testschritt Assets ausgeführten Tests werden mit dieser [Open Source Library](https://github.com/adobe/toughday2) geschrieben. Sowohl die Verarbeitungszeit für jedes Asset als auch verschiedene Metriken auf Systemebene werden über die 30-Minuten-Testdauer hinweg gemessen. Mit dieser Funktion können sowohl Bilder als auch PDF-Dokumente hochgeladen werden.

   >[!NOTE]
   >Weitere Informationen zum Konfigurieren von Leistungstests finden Sie unter [Konfigurieren der CI/CD-Pipeline](configuring-pipeline.md). Informationen zum Einrichten des Programms und Definieren der KPIs finden Sie unter [Einrichten des Programms](setting-up-program.md).

### Diagramme mit Leistungstestergebnissen {#performance-testing-results-graphs}

Dem Dialogfeld „Leistungstestergebnisse“ wurden neue Diagramme und Downloadoptionen hinzugefügt.

Wenn Sie das Dialogfeld „Leistungstest“ öffnen, können die Metrikbedienfelder erweitert werden, um ein Diagramm anzuzeigen, einen Downloadlink bereitzustellen oder beides.

In der [!UICONTROL Cloud Manager]-Version 2018.7.0 ist diese Funktion für die folgenden Metriken verfügbar:

* **CPU-Auslastung**
   * Ein Diagramm zur CPU-Auslastung während des Testzeitraums.

* **Festplatten-I/O-Wartezeit**
   * Ein Diagramm zur Festplatten-I/O-Wartezeit während des Testzeitraums.

* **Seitenfehlerrate**
   * Ein Diagramm zu den Seitenfehlern pro Minute während des Testzeitraums.
   * Eine CSV-Datei mit den Seiten, die während des Tests einen Fehler verursacht haben.

* **Festplatten-Bandbreitenauslastung**
   * Ein Diagramm zur Festplatten-Bandbreitenauslastung während des Testzeitraums.

* **Netzwerk-Bandbreitenauslastung**
   * Ein Diagramm zur Netzwerk-Bandbreitenauslastung während des Testzeitraums.

* **Spitzenreaktionszeit**
   * Ein Diagramm zur Spitzenreaktionszeit pro Minute während des Testzeitraums.

* **95. Perzentil der Reaktionszeit**
   * Ein Diagramm zum 95. Perzentil der Reaktionszeit pro Minute während des Testzeitraums.
   * Eine CSV-Datei mit den Seiten, deren 95. Perzentil der Reaktionszeit die definierte KPI überschritten hat.

Die folgenden Abbildungen zeigen Leistungstestdiagramme:

![](assets/understand_test-results-screen1.png)

![](assets/screen_shot_2018-09-05at83933pm.png)

