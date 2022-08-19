---
title: Testen der Code-Qualität
description: Erfahren Sie, wie das Testen der Code-Qualität von Pipelines funktioniert und wie damit die Qualität Ihrer Bereitstellungen verbessert werden kann.
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: ht
source-wordcount: '2867'
ht-degree: 100%

---


# Testen der Code-Qualität {#code-quality-testing}

Erfahren Sie, wie das Testen der Code-Qualität von Pipelines funktioniert und wie damit die Qualität Ihrer Bereitstellungen verbessert werden kann.

## Einführung {#introduction}

Während der Pipeline-Ausführung werden verschiedene Metriken erfasst und entweder mit den vom Geschäftsinhaber definierten KPIs (Key Performance Indicators) oder mit den von Adobe Managed Services festgelegten Standards verglichen.

Diese werden über ein dreistufiges Bewertungssystem gemeldet.

## Dreistufige Bewertungen {#three-tiered-ratings}

Die Pipeline muss drei Akzeptanztests bestehen:

* Code-Qualität
* Leistungstests
* Sicherheitstests

Für jeden dieser Akzeptanztests gibt es eine dreistufige Struktur für vom Test identifizierte Probleme.

* **Kritisch**: Hierbei handelt es sich um vom Test identifizierte Probleme, die zu einem sofortigen Pipeline-Fehler führen.
* **Wichtig**: Hierbei handelt es sich um Probleme, durch die die Pipeline angehalten wird. Implementierungs-Manager, Projekt-Manager oder Geschäftsinhaber können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler. Die Außerkraftsetzung wichtiger Fehler unterliegt einem [Timeout](/help/using/code-deployment.md#timeouts).
* **Info**: Hierbei handelt es sich um Probleme, die ausschließlich zu Informationszwecken bereitgestellt werden und keine Auswirkungen auf die Pipeline-Ausführung haben.

>[!NOTE]
>
>In einer Pipeline nur für Code-Qualität können Fehler der Kategorie „Wichtig“ des Code-Qualitätstests nicht überschrieben werden, da dieser Test der letzte Schritt in der Pipeline ist.

## Testen der Code-Qualität {#code-quality-testing-step}

Dieser Schritt bewertet die Qualität des Anwendungs-Codes. Dies ist der Hauptzweck einer reinen Code-Qualitäts-Pipeline und wird unmittelbar nach dem Build-Schritt in allen produktionsfremden und Produktions-Pipelines ausgeführt. Weitere Informationen finden Sie im Dokument [Konfigurieren von produktionsfremden Pipelines](/help/using/non-production-pipelines.md).

Beim Testen der Code-Qualität wird der Quell-Code gescannt, um sicherzustellen, dass er bestimmte Qualitätskriterien erfüllt. Dies wird durch eine Kombination aus SonarQube-Analyse, Prüfung auf Inhaltspaket-Ebene mit OakPAL und Dispatcher-Validierung mit dem Dispatcher-Optimierungs-Tool implementiert.

Es gibt über 100 Regeln, die generische Java-Regeln und AEM-spezifische Regeln kombinieren. Einige der AEM-spezifischen Regeln werden auf der Grundlage der Best Practices von AEM Engineering erstellt und als [benutzerspezifische Code-Qualitätsregeln](/help/using/custom-code-quality-rules.md) bezeichnet.

>[!TIP]
>
>Sie können die vollständige Liste von Regeln [über diesen Link](/help/assets/CodeQuality-rules-latest-AMS.xlsx) herunterladen.

Die Ergebnisse des Code-Qualitätstests werden als Bewertung bereitgestellt, wie in dieser Tabelle zusammengefasst.

| Name | Definition | Kategorie | Fehlerschwellenwert |
|--- |--- |--- |--- |
| Sicherheitsbewertung | A = Keine Schwachstellen <br/>B = mindestens 1 kleinere Schwachstelle <br/>C = mindestens 1 größere Schwachstelle <br/>D = mindestens 1 kritische Schwachstelle <br/>E = mindestens 1 Schwachstelle der Kategorie „Blocker“ | Kritisch | &lt; B |
| Zuverlässigkeitsbewertung | A = Keine Fehler <br/>B = mindestens 1 kleinerer Fehler <br/>C = mindestens 1 größerer Fehler <br/>D = mindestens 1 kritischer Fehler<br/>E = mindestens 1 Fehler der Kategorie „Blocker“ | Wichtig | &lt; C |
| Wartbarkeitsbewertung | Definiert durch die ausstehenden Kosten für die Behebung von Code-Fehlern als Prozentsatz der Zeit, die bereits in das Programm investiert wurde<br/><ul><li>A = &lt;=5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = >50 %</li></ul> | Wichtig | &lt; A |
| Abdeckung | Definiert durch eine Mischung aus Zeilenabdeckung der Einheitstests und Bedingungsabdeckung nach der Formel: <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Bedingungen wurden mindestens einmal während der Ausführung der Einheitentests zu `true` ausgewertet</li><li>`CF` = Bedingungen wurden mindestens einmal während der Ausführung der Einheitentests zu `false` ausgewertet</li><li>`LC` = abgedeckte Zeilen = lines_to_cover - uncovered_lines</li><li>`B` = Gesamtzahl der Bedingungen</li><li>`EL` = Gesamtzahl der ausführbaren Zeilen (lines_to_cover)</li></ul> | Wichtig | &lt; 50 % |
| Übersprungene Einheitentests | Anzahl der übersprungenen Einheitentests | Info | > 1 |
| Offene Probleme | Allgemeine Problemtypen – Schwachstellen (Vulnerability), Fehler (Bug) und Code-Smells (Code Smell) | Info | > 0 |
| Duplizierte Zeilen | Definiert als die Anzahl der Zeilen, die in doppelten Blöcken enthalten sind. Ein Code-Block gilt unter den folgenden Bedingungen als dupliziert.<br>Nicht-Java-Projekte:<ul><li>Es sollten mindestens 100 aufeinanderfolgende und duplizierte Token vorhanden sein.</li><li>Diese Token sollten sich mindestens wie folgt verteilen: </li><li>30 Codezeilen für COBOL </li><li>20 Codezeilen für ABAP </li><li>10 Codezeilen für andere Sprachen</li></ul>Java-Projekte:<ul></li><li> Unabhängig von der Anzahl der Token und Zeilen sollte es mindestens 10 aufeinanderfolgende und duplizierte Anweisungen geben.</li></ul>Unterschiede bei Einzügen sowie Zeichenfolgenliteralen werden beim Erkennen von Duplikaten ignoriert. | Info | > 1 % |
| Kompatibilität mit Cloud Service | Anzahl der festgestellten Kompatibilitätsprobleme mit Cloud Service | Info | > 0 |

>[!NOTE]
>
>Genauere Definitionen finden Sie unter [Metrikdefinitionen von SonarQube](https://docs.sonarqube.org/latest/user-guide/metric-definitions/).

>[!NOTE]
>
>Weitere Informationen zu den benutzerdefinierten Regeln zur Code-Qualität, die von [!UICONTROL Cloud Manager] ausgeführt werden, finden Sie unter [Benutzerspezifische Regeln für Code-Qualität](custom-code-quality-rules.md).

### Umgang mit falsch positiven Treffern {#dealing-with-false-positives}

Das Verfahren zur Qualitätsprüfung ist nicht perfekt. Mitunter werden fälschlicherweise Probleme identifiziert, die eigentlich nicht problematisch sind. Dies wird als falsch positiv bezeichnet.

In diesen Fällen kann der Quell-Code mit der standardmäßigen `@SuppressWarnings`-Java-Anmerkung kommentiert werden. Dabei wird die Regel-ID als Anmerkungsattribut angegeben. Ein häufiges Problem besteht etwa darin, dass die SonarQube-Regel zur Erkennung hartcodierter Kennwörter in Bezug auf die Identifizierung eines hartcodierten Kennworts „aggressiv“ sein kann.

Der folgende Code ist in einem AEM-Projekt, das eine Verbindung zu einem externen Service herstellen soll, relativ häufig.

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

Wenn der Code allerdings tatsächlich so lautete:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dann bestünde die richtige Lösung darin, das hartcodierte Kennwort zu entfernen.

>[!NOTE]
>
>Obwohl sich möglichst spezifische `@SuppressWarnings`-Anmerkungen bewährt haben, also nur eine bestimmte Anweisung oder den Block zu kommentieren, der das Problem verursacht, können Anmerkungen auf Klassenebene hinzugefügt werden.

## Sicherheitstests {#security-testing}

[!UICONTROL Cloud Manager] führt die vorhandenen AEM-Sicherheits-Konsistenzprüfungen in der Staging-Umgebung nach der Bereitstellung aus und meldet den Status über die UI. Die Ergebnisse werden aus allen AEM-Instanzen in der Umgebung aggregiert.

Dieselben Konsistenzprüfungen können jederzeit über die Web-Konsole oder das Vorgangs-Dashboard ausgeführt werden.

Wenn eine der Instanzen einen Fehler bei einer bestimmten Konsistenzprüfung meldet, schlägt die Konsistenzprüfung für die gesamte Umgebung fehl. Wie Code-Qualitäts- und Leistungstests sind diese Konsistenzprüfungen in Kategorien unterteilt und die zugehörigen Berichte werden über das dreistufige Gating-System erstellt. Der einzige Unterschied besteht darin, dass im Falle von Sicherheitstests keine Schwellenwerte vorhanden sind. Alle Konsistenzprüfungen werden entweder bestanden oder schlagen fehl.

In der folgenden Tabelle sind die Konsistenzprüfungen aufgeführt.

| Name | Implementierung der Konsistenzprüfung | Kategorie |
|---|---|---|
| Deserialisierungs-Firewall-Attach-API-Bereitschaft befindet sich in einem akzeptablen Zustand. | [Deserialisierungs-Firewall-Attach-API-Bereitschaft](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=de#security) | Kritisch |
| Deserialisierungs-Firewall ist funktionsfähig. | [Deserialisierungs-Firewall funktionsfähig](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=de#security) | Kritisch |
| Deserialisierungs-Firewall wird geladen. | [Deserialisierungs-Firewall geladen](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html?lang=de#security) | Kritisch |
| `AuthorizableNodeName`-Implementierung des weist keine autorisierbare ID im Knotennamen/Pfad auf. | [Namenserstellung für autorisierbare Knoten](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=de#security) | Kritisch |
| Standardkennwörter wurden geändert. | [Standard-Anmeldekonten](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html?lang=de#users-and-groups-in-aem) | Kritisch |
| Sling-Standard-GET-Servlet ist vor DOS-Angriffen geschützt. | Sling Get Servlet | Kritisch |
| Sling Java Script Handler ist ordnungsgemäß konfiguriert. | Sling Java Script Handler | Kritisch |
| Sling JSP Script Handler ist ordnungsgemäß konfiguriert. | Sling JSP Script Handler | Kritisch |
| SSL ist richtig konfiguriert. | SSL-Konfiguration | Kritisch |
| Es wurden keine offensichtlich unsicheren Benutzerprofil-Richtlinien gefunden. | Standardzugriff auf Benutzerprofil | Kritisch |
| Der Sling Referrer-Filter ist konfiguriert, um CSRF-Angriffe zu verhindern. | [Sling Referrer-Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=de#security) | Wichtig |
| Adobe Granite HTML Library Manager ist ordnungsgemäß konfiguriert. | Konfiguration des CQ-HTML-Bibliotheksmanagers | Wichtig |
| CRXDE-Support-Paket ist deaktiviert. | CRXDE-Support | Wichtig |
| Sling DavEx-Paket und -Servlet sind deaktiviert. | DavEx-Konsistenzprüfung | Wichtig |
| Beispielinhalt ist nicht installiert.. | Pakete mit Beispielinhalt | Wichtig |
| Sowohl der WCM-Anfrage-Filter als auch der WCM-Debug-Filter sind deaktiviert. | [WCM-Filterkonfiguration](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html?lang=de#configuring) | Wichtig |
| Sling WebDAV Bundle und Servlet sind angemessen konfiguriert. | WebDAV-Konsistenzprüfung | Wichtig |
| Der Webserver ist so konfiguriert, dass Clickjacking verhindert wird. | Webserver-Konfiguration | Wichtig |
| Replikation verwendet nicht den Benutzer `admin`. | Benutzerreplikation und -transport | Info |

## Leistungstests {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager führt Leistungstests für AEM Sites-Programme aus. Der Leistungstest wird etwa 30 Minuten lang ausgeführt, indem durch virtuelle Benutzer (Container) der Zugriff tatsächlicher Benutzer auf Seiten in der Staging-Umgebung und Traffic simuliert wird. Diese Seiten werden mit einem Crawler gefunden.

#### Virtuelle Benutzer {#virtual-users}

Die Anzahl der virtuellen Benutzer oder Container, die von Cloud Manager erzeugt werden, hängt von den KPIs (Antwortzeit und Seitenansichten/Min.) ab, die der Benutzer in der Rolle **Geschäftsinhaber** beim [Erstellen oder Bearbeiten des Programms definiert hat.](/help/getting-started/program-setup.md) Je nach definierten KPIs werden bis zu 10 Container generiert, die die tatsächlichen Benutzer simulieren. Die für Tests ausgewählten Seiten werden aufgeteilt und jedem virtuellen Benutzer zugewiesen.

#### Crawler {#crawler}

Vor dem Beginn des 30-minütigen Testzeitraums durchsucht Cloud Manager die Staging-Umgebung anhand einer oder mehrerer vom Customer Success Engineer konfigurierten Seed-URLs. Ausgehend von diesen URLs wird der HTML-Code jeder Seite überprüft und Links werden breitenorientiert durchsucht.

* Dieser Crawling-Vorgang ist standardmäßig auf maximal 5.000 Seiten beschränkt.
* Die maximale Anzahl der zu testenden Seiten kann überschrieben werden, indem Sie die Variable [Umgebungsvariable](/help/getting-started/build-environment.md#environment-variables) `MAX_PAGES` festlegen.
   * Zulässige Werte sind `2000`–`7000`.
* Für Anfragen des Crawlers gilt ein festes Zeitlimit von 10 Sekunden.

#### Seitensätze zum Testen {#page-sets}

Die Seiten werden nach drei Seitensätzen ausgewählt. Cloud Manager verwendet die Zugriffsprotokolle der AEM-Instanzen in der Produktions- und Staging-Umgebung, um die folgenden drei Buckets zu ermitteln.

* **Beliebte Live-Seiten**: Diese Option wird ausgewählt, um sicherzustellen, dass die von Live-Kunden bevorzugt aufgerufenen Seiten getestet werden. Cloud Manager liest das Zugriffsprotokoll und ermittelt die 25 am häufigsten aufgerufenen Seiten von Live-Kunden, um eine Liste von `Popular Live Pages` zu generieren. Die Schnittmenge dieser Seiten, die auch in der Staging-Umgebung vorhanden sind, wird dann in der Staging-Umgebung durchsucht.

* **Andere Live-Seiten**: Diese Option wird ausgewählt, um sicherzustellen, dass Seiten, die nicht zu den 25 beliebtesten Live-Seiten gehören und nicht besonders beliebt sind, aber unbedingt getestet werden sollten, tatsächlich getestet werden. Ähnlich wie „Beliebte Live-Seiten“ werden auch diese aus dem Zugriffsprotokoll extrahiert und müssen auch in der Staging-Umgebung vorhanden sein.

* **Neue Seiten**: Diese Option wird ausgewählt, um neue Seiten zu testen, die möglicherweise nur im Staging bereitgestellt wurden und noch nicht zur Produktion gehören, aber getestet werden müssen.

##### Verteilung des Traffics auf ausgewählte Seitensätze {#distribution-of-traffic}

Sie können auf der Registerkarte **Testen** der [Pipeline-Konfiguration zwischen einem Satz und allen drei Sätzen wählen.](/help/using/production-pipelines.md) Die Verteilung des Traffics basiert auf der Anzahl der ausgewählten Sätze, d. h. wenn alle drei Sätze ausgewählt sind, entfallen je 33 % aller Seitenaufrufe auf jeden Satz, bei zwei Sätzen sind es 50 % und bei einem ausgewählten Satz entfallen 100 % des Traffics auf diesen Satz.

Betrachten wir dieses Beispiel.

* Es gibt eine 50/50-Aufteilung zwischen den Sätzen mit beliebten Live-Seiten und den neuen Seiten.
* Andere Live-Seiten werden nicht verwendet.
* Der Satz mit neuen Seiten umfasst 3.000 Seiten.
* Für den KPI der Seitenansichten pro Minute wird ein Wert von 200 festgelegt.

Für den 30-minütigen Testzeitraum gilt in diesem Fall:

* Jede der 25 Seiten der beliebten Live-Seiten wird 120-mal aufgerufen: `((200 * 0.5) / 25) * 30 = 120`
* Jede der 3.000 Seiten im Satz „Neue Seiten“ wird einmal aufgerufen: `((200 * 0.5) / 3000) * 30 = 1`

#### Tests und Reporting {#testing-reporting}

Cloud Manager führt Leistungstests für AEM Sites-Programme durch, indem Seiten über einen 30-minütigen Testzeitraum hinweg standardmäßig als nicht authentifizierter Benutzer auf dem Staging-Veröffentlichungs-Server angefordert werden. Dabei werden die virtuellen, von den Benutzern generierten Metriken (Antwortzeit, Fehlerrate, Aufrufe pro Minute usw.) für jede Seite sowie verschiedene Metriken auf Systemebene (CPU, Arbeitsspeicher, Netzwerkdaten) für alle Instanzen gemessen.

In der folgenden Tabelle finden Sie eine Zusammenfassung der Leistungstestmatrix unter Verwendung des dreistufigen Gating-Systems.

| Metrik | Kategorie | Fehlerschwellenwert |
|---|---|---|
| Seitenanforderungsfehlerrate | Kritisch | >= 2 % |
| CPU-Auslastungsrate | Kritisch | >= 80% |
| Festplatten-I/O-Wartezeit | Kritisch | >= 50 % |
| 95. Perzentil der Reaktionszeit | Wichtig | >= KPI auf Programmebene |
| Spitzenreaktionszeit | Wichtig | >= 18 Sekunden |
| Seitenaufrufe pro Minute | Wichtig | &lt; KPI auf Programmebene |
| Festplatten-Bandbreitenauslastung | Wichtig | >= 90 % |
| Netzwerk-Bandbreitenauslastung | Wichtig | >= 90 % |
| Anforderungen pro Minute | Info | >= 6.000 |

Weitere Informationen zur Verwendung der einfachen Authentifizierung für Leistungstests zum Testen von Sites und Assets finden Sie im Abschnitt [Authentifizierte Leistungstests](#authenticated-performance-testing).

>[!NOTE]
>
>Sowohl die Autoren- als auch die Veröffentlichungsinstanz werden während der Testdauer überwacht. Wenn für eine Instanz keine Metrik abgerufen wird, wird diese Metrik als unbekannt gemeldet und der entsprechende Schritt schlägt fehl.

#### Authentifizierte Leistungstests {#authenticated-performance-testing}

AMS-Kunden mit authentifizierten Websites können einen Benutzernamen und ein Kennwort angeben, mit denen Cloud Manager während der Sites-Leistungstests auf die Website zugreift.

Benutzername und Kennwort werden als Pipeline-Variablen mit den Namen `CM_PERF_TEST_BASIC_USERNAME` und `CM_PERF_TEST_BASIC_PASSWORD` angegeben.

Der Benutzername sollte in einer `string`-Variablen und das Kennwort einer `secretString`-Variablen gespeichert werden. Wenn beide angegeben sind, enthält jede Anfrage des Leistungstest-Crawlers und der virtuellen Testbenutzer diese Anmeldedaten als einfache HTTP-Standardauthentifizierung.

Um diese Variablen mithilfe der Cloud Manager-Befehlszeilenschnittstelle festzulegen, führen Sie Folgendes aus:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Informationen zur Verwendung der API finden Sie in der API-Dokumentation [Patchen von Benutzer-Pipeline-Variablen](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/patchPipelineVariables).

### AEM Assets {#aem-assets}

Cloud Manager führt Leistungstests für AEM Assets-Programme durch, indem Assets für einen 30-minütigen Testzeitraum wiederholt hochgeladen werden.

#### Onboarding-Anforderungen {#onboarding-requirement}

Bei Assets-Leistungstests erstellt Ihr Customer Success Engineer während des Onboardings des Autors in der Staging-Umgebung einen `cloudmanager`-Benutzer (und ein entsprechendes Kennwort). Für die Leistungstestschritte müssen ein Benutzer namens `cloudmanager` und das zugehörige Kennwort vom CSE eingerichtet werden. Dieser sollte weder aus der Autoreninstanz entfernt noch sollten seine Berechtigungen geändert werden. Dies führt wahrscheinlich zu einem Fehler beim Assets-Leistungstest.

#### Bilder und Assets zum Testen {#assets-for-testing}

Kunden können ihre eigenen Assets zum Testen hochladen. Dies kann bei der **Pipeline-Einrichtung** oder auf dem Bildschirm **Bearbeiten** festgelegt werden. Dabei werden typische Bildformate wie JPEG, PNG, GIF und BMP sowie Photoshop-, Illustrator- und Postscript-Dateien unterstützt.

Wenn keine Bilder hochgeladen werden, verwendet Cloud Manager zum Testen ein Standardbild und PDF-Dokumente.

#### Verteilung von Assets für Tests {#distribution-of-assets}

Die Verteilung der Anzahl von Assets jedes Typs, die pro Minute hochgeladen werden, wird bei der **Pipeline-Einrichtung** oder auf dem Bildschirm **Bearbeiten** festgelegt.

Wenn beispielsweise eine Verteilung von 70/30 verwendet wird und pro Minute 10 Dateien hochgeladen werden, werden pro Minute 7 Bilder und 3 Dokumente hochgeladen.

#### Tests und Reporting {#testing-and-reporting}

Cloud Manager erstellt einen Ordner in der Autoreninstanz und verwendet hierbei den Benutzernamen und das Kennwort, die vom CSE festgelegt wurden. Die Assets werden dann unter Verwendung einer Open-Source-Bibliothek hochgeladen. Die vom Assets-Testschritt ausgeführten Tests werden mit einer [-Open-Source-Bibliothek geschrieben.](https://github.com/adobe/toughday2) Während der 30-minütigen Testdauer werden sowohl die Verarbeitungszeit für jedes Asset als auch verschiedene Metriken auf Systemebene gemessen. Mit dieser Funktion können sowohl Bilder als auch PDF-Dokumente hochgeladen werden.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md). Informationen zum Einrichten des Programms und Definieren der KPIs finden Sie im Dokument [Programm einrichten](/help/getting-started/program-setup.md).

### Diagramme mit Leistungstestergebnissen {#performance-testing-results-graphs}

Im Dialogfeld **Leistungstest** sind eine Reihe von Metriken verfügbar.

![Liste der Metriken](/help/assets/understand_test-results-screen1.png)

Die Bereiche mit Metriken können erweitert werden, um ein Diagramm anzuzeigen oder einen Link zu einem Download bereitzustellen oder beides.

![Als Diagramm erweiterte Metriken](/help/assets/screen_shot_2018-09-05at83933pm.png)

Diese Funktion ist für die folgenden Metriken verfügbar.

* **CPU-Auslastung** : Ein Diagramm zur CPU-Auslastung während des Testzeitraums

* **Festplatten-E/A-Wartezeit**: Ein Diagramm zur Festplatten-E/A-Wartezeit während des Testzeitraums

* **Fehlerrate für die Seite**: Ein Diagramm zu den Seitenfehlern pro Minute während des Testzeitraums
   * Eine CSV-Datei mit den Seiten, die während des Tests einen Fehler verursacht haben

* **Festplatten-Bandbreitenauslastung** : Ein Diagramm zur Festplatten-Bandbreitenauslastung während des Testzeitraums

* **Auslastung der Netzwerkbandbreite**: Ein Diagramm zur Netzwerk-Bandbreitenauslastung während des Testzeitraums

* **Spitzenreaktionszeit**: Ein Diagramm zur Spitzenreaktionszeit pro Minute während des Testzeitraums

* **95. Perzentil der Reaktionszeit**: Ein Diagramm zum 95. Perzentil der Reaktionszeit pro Minute während des Testzeitraums
   * Eine CSV-Datei mit den Seiten, deren 95. Perzentil der Reaktionszeit die definierte KPI überschritten hat

## Optimierung der Inhaltspaketüberprüfung {#content-package-scanning-optimization}

Im Rahmen des Qualitätsanalyseprozesses führt Cloud Manager eine Analyse der vom Maven-Build erzeugten Inhaltspakete durch. Cloud Manager bietet Optimierungen zur Beschleunigung dieses Prozesses an, die wirksam sind, wenn bestimmte Verpackungseinschränkungen beachtet werden. Am wichtigsten ist die Optimierung, die für Projekte durchgeführt wird, die ein einzelnes Inhaltspaket ausgeben, das im Allgemeinen als „all“-Paket bezeichnet wird und eine Reihe andere Inhaltspakete enthält, die durch den Build erzeugt und als übersprungen markiert wurden. Wenn Cloud Manager dieses Szenario erkennt, wird nicht das gesamte Paket entpackt, sondern die einzelnen Inhaltspakete werden direkt gescannt und auf der Grundlage von Abhängigkeiten sortiert. Betrachten Sie zum Beispiel die folgende Build-Ausgabe.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (Inhaltspaket)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (übersprungenes Inhaltspaket)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (übersprungenes Inhaltspaket)

Wenn die beiden übersprungenen Inhaltspakete die einzigen Elemente innerhalb von `myco-all-1.0.0-SNAPSHOT.zip` sind, werden die beiden eingebetteten Pakete anstelle des gesamten Inhaltspakets (all) gescannt.

Bei Projekten, die Dutzende von eingebetteten Paketen produzieren, kann diese Optimierung nachweislich bis zu 10 Minuten pro Pipeline-Ausführung einsparen.

Ein Sonderfall kann eintreten, wenn das Inhaltspaket „all“ eine Kombination aus übersprungenen Inhaltspaketen und OSGi-Bundles enthält. Wenn `myco-all-1.0.0-SNAPSHOT.zip` beispielsweise die beiden zuvor erwähnten eingebetteten Pakete sowie ein oder mehrere OSGi-Bundles enthält, wird ein neues, minimales Inhaltspaket nur mit den OSGi-Bundles erstellt. Dieses Paket hat immer die Bezeichnung `cloudmanager-synthetic-jar-package` und die darin enthaltenen Bundles werden in `/apps/cloudmanager-synthetic-installer/install` abgelegt.

>[!NOTE]
>
>* Diese Optimierung hat keine Auswirkungen auf die Pakete, die in AEM bereitgestellt werden.
>* Da der Abgleich zwischen den eingebetteten Inhaltspaketen und den übersprungenen Inhaltspaketen auf Dateinamen basiert, kann diese Optimierung nicht durchgeführt werden, wenn mehrere übersprungene Inhaltspakete genau denselben Dateinamen haben oder wenn der Dateiname während des Einbettens geändert wird.

