---
title: Wissenswertes zu Testergebnissen
description: Erfahren Sie, wie das Testen der Codequalität von Pipelines funktioniert und wie es die Qualität Ihrer Implementierungen verbessern kann.
uuid: 93caa01f-0df2-4a6f-81dc-23dfee24dc93
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 83299ed8-4b7a-4b1c-bd56-1bfc7e7318d4
feature: CI-CD Pipeline, Test Results
exl-id: 6a574858-a30e-4768-bafc-8fe79f928294
source-git-commit: 2179314120911cac8a0dd99a8b57974751959871
workflow-type: tm+mt
source-wordcount: '2901'
ht-degree: 29%

---

# Wissenswertes zu Testergebnissen {#understand-your-test-results}

Erfahren Sie, wie das Testen der Codequalität von Pipelines funktioniert und wie es die Qualität Ihrer Implementierungen verbessern kann.

## Einführung {#introduction}

Während der Pipelineausführung werden verschiedene Metriken erfasst und entweder mit den vom Business Owner definierten KPIs (Key Performance Indicators) oder mit den von Adobe Managed Services festgelegten Standards verglichen.

Diese werden mithilfe eines dreistufigen Ratingsystems gemeldet, wie im nächsten Abschnitt definiert

>[!NOTE]
>
>Weitere Informationen zu Tests, die von Cloud Manager für AEM as a Cloud Service unterstützt werden, finden Sie unter [AEM as a Cloud Service Dokumentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/test-results/overview-test-results.html).


## Dreistufige Bewertungen  {#three-tier-gates-while-running-a-pipeline}

Die Pipeline muss drei Akzeptanztests bestehen:

* Code-Qualität
* Leistungstests
* Sicherheitstests

Für jeden dieser Akzeptanztests gibt es eine dreistufige Struktur für vom Test identifizierte Probleme.

* **Kritisch** - Hierbei handelt es sich um Probleme, die zu einem sofortigen Pipelinefehler führen.
* **Wichtig** - Hierbei handelt es sich um Probleme, durch die die Pipeline angehalten wird. Implementierungs-Manager, Projekt-Manager oder Geschäftsinhaber können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler. Die Außerkraftsetzung wichtiger Fehler unterliegt einer [Zeitüberschreitung.](deploying-code.md#timeouts)
* **Info** - Hierbei handelt es sich um Probleme, die ausschließlich zu Informationszwecken bereitgestellt werden und keine Auswirkungen auf die Pipelineausführung haben.

>[!NOTE]
>
>In einer reinen Codequalitäts-Pipeline können wichtige Fehler im Code-Qualitäts-Gate nicht überschrieben werden, da der Schritt zum Testen der Codequalität der letzte Schritt in der Pipeline ist.

## Testen der Code-Qualität {#code-quality-testing}

Dieser Schritt bewertet die Qualität Ihres Anwendungs-Codes, den Hauptzweck einer reinen Codequalitäts-Pipeline, und wird unmittelbar nach dem Build-Schritt in allen Nicht-Produktions- und Produktions-Pipelines ausgeführt. Weitere Informationen finden Sie im Dokument . [Konfigurieren von Nicht-Produktions-Pipelines](configuring-non-production-pipelines.md) , um mehr zu erfahren.

### Wissenswertes zum Testen der Code-Qualität {#understanding-code-quality-testing}

Codequalitätstests scannen den Quellcode, um sicherzustellen, dass er bestimmte Qualitätskriterien erfüllt. Dies wird durch eine Kombination aus SonarQube-Analyse, Prüfung auf Inhaltspaketebene mit OakPAL und Dispatcher-Validierung mithilfe des Dispatcher Optimization-Tools implementiert.

Es gibt über 100 Regeln, die generische Java-Regeln und AEM-spezifische Regeln kombinieren. Einige der AEM-spezifischen Regeln werden auf der Grundlage der Best Practices von AEM Engineering erstellt und werden als [Benutzerdefinierte Regeln für die Code-Qualität.](/help/using/custom-code-quality-rules.md)

>[!NOTE]
>
>Sie können die vollständige Liste der Regeln herunterladen [diesen Link verwenden.](/help/using/assets/CodeQuality-rules-latest-AMS.xlsx)

Die Ergebnisse von Code-Qualitätstests werden als **Bewertungen**. Die folgende Tabelle fasst die Bewertungen für verschiedene Testkriterien zusammen.

| Name | Definition | Kategorie | Fehlerschwellenwert |
|--- |--- |--- |--- |
| Sicherheitsbewertung | A = Keine Schwachstellen<br/>B = Mindestens 1 kleinere Schwachstelle<br/>C = Mindestens 1 größere Schwachstelle<br/>D = Mindestens 1 kritische Schwachstelle<br/>E = Mindestens 1 Blocker-Schwachstelle | Kritisch | &lt; B |
| Zuverlässigkeitsbewertung | A = Keine Fehler<br/>B = Mindestens 1 kleinerer Fehler <br/>C = Mindestens 1 größerer Fehler<br/>D = Mindestens 1 kritischer Fehler<br/>E = Mindestens 1 Blockerfehler | Wichtig | &lt; C |
| Wartbarkeitsbewertung | Definiert durch die ausstehenden Sanierungskosten für Code-Smell als Prozentsatz der Zeit, die bereits in die Anwendung gegangen ist<br/><ul><li>A = &lt; = 5 %</li><li>B = 6-10 %</li><li>C = 11-20 %</li><li>D = 21-50 %</li><li>E = > 50 %</li></ul> | Wichtig | &lt; A |
| Abdeckung | Definiert durch eine Mischung aus Unit-Test-Line-Abdeckung und Bedingungsabdeckung anhand der Formel: <br/>`Coverage = (CT + CF + LC) / (2 * B + EL)`  <ul><li>`CT` = Bedingungen, die als `true` mindestens einmal während der Durchführung von Komponententests</li><li>`CF` = Bedingungen, die als `false` mindestens einmal während der Durchführung von Komponententests</li><li>`LC` = Überdeckte Zeilen = lines_to_cover - uncover_lines</li><li>`B` = Gesamtzahl der Bedingungen</li><li>`EL` = Gesamtzahl ausführbarer Zeilen (lines_to_cover)</li></ul> | Wichtig | &lt; 50 % |
| Übersprungene Unit-Tests | Anzahl der übersprungenen Komponententests | Info | > 1 |
| Offene Probleme | Allgemeine Problemtypen – Schwachstellen (Vulnerability), Fehler (Bug) und Code-Smells (Code Smell) | Info | > 0 |
| Duplizierte Zeilen | Definiert als Anzahl der Zeilen, die an duplizierten Blöcken beteiligt sind. Ein Codeblock wird unter den folgenden Bedingungen als dupliziert betrachtet.<br>Nicht-Java-Projekte:<ul><li>Es sollte mindestens 100 aufeinanderfolgende und duplizierte Token geben.</li><li>Diese Token sollten sich mindestens auf Folgendes erstrecken: </li><li>30 Codezeilen für COBOL </li><li>20 Codezeilen für ABAP </li><li>10 Codezeilen für andere Sprachen</li></ul>Java-Projekte:<ul></li><li> Unabhängig von der Anzahl der Token und Zeilen sollten mindestens 10 aufeinander folgende und duplizierte Anweisungen vorhanden sein.</li></ul>Unterschiede bei Einzügen sowie Zeichenfolgenliteralen werden beim Erkennen von Duplikaten ignoriert. | Info | > 1 % |
| Kompatibilität mit Cloud Service | Anzahl der festgestellten Kompatibilitätsprobleme mit Cloud Service | Info | > 0 |

>[!NOTE]
>
>Siehe [Metrikdefinitionen von SonarQube](https://docs.sonarqube.org/display/SONAR/Metric+Definitions) für detailliertere Informationen.

>[!NOTE]
>
>Weitere Informationen zu benutzerspezifischen Regeln für die Code-Qualität, die von [!UICONTROL Cloud Manager], siehe Dokument [Benutzerdefinierte Regeln für die Code-Qualität.](custom-code-quality-rules.md)

### Umgang mit falsch positiven Treffern {#dealing-with-false-positives}

Das Verfahren zur Qualitätsprüfung ist nicht perfekt. Mitunter werden fälschlicherweise Probleme identifiziert, die eigentlich nicht problematisch sind. Dies wird als **falsch positiv** bezeichnet.

In diesen Fällen kann der Quell-Code mit der standardmäßigen `@SuppressWarnings`-Java-Anmerkung kommentiert werden. Dabei wird die Regel-ID als Anmerkungsattribut angegeben. Ein gängiges Falsch-Positiv-Ergebnis besteht beispielsweise darin, dass die SonarQube-Regel zur Erkennung hartcodierter Kennwörter in Bezug auf die Identifizierung eines hartcodierten Kennworts aggressiv sein kann.

Der folgende Code ist recht häufig in einem AEM Projekt enthalten, das über Code verfügt, um eine Verbindung zu einem externen Dienst herzustellen.

```java
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

SonarQube weist dann eine Blocker-Schwachstelle auf. Nach der Überprüfung des Codes erkennen Sie jedoch, dass dies keine Schwachstelle ist, und können den Code mit der entsprechenden Regel-ID kommentieren.

```java
@SuppressWarnings("squid:S2068")
@Property(label = "Service Password")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Wenn der Code jedoch tatsächlich Folgendes war:

```java
@Property(label = "Service Password", value = "mysecretpassword")
private static final String PROP_SERVICE_PASSWORD = "password";
```

Dann bestünde die richtige Lösung darin, das hartcodierte Kennwort zu entfernen.

>[!NOTE]
>
>Obwohl sich möglichst spezifische `@SuppressWarnings`-Anmerkungen bewährt haben, also nur eine bestimmte Anweisung oder den Block zu kommentieren, der das Problem verursacht, können Anmerkungen auf Klassenebene hinzugefügt werden.

## Sicherheitstests {#security-testing}

[!UICONTROL Cloud Manager] führt die vorhandene **AEM Sicherheits-Konsistenzprüfungen** in der Staging-Umgebung nach der Bereitstellung angezeigt werden und den Status über die Benutzeroberfläche melden. Die Ergebnisse werden aus allen AEM-Instanzen in der Umgebung aggregiert.

Dieselben Konsistenzprüfungen können jederzeit über die Web-Konsole oder das Vorgangs-Dashboard ausgeführt werden.

Wenn eine der Instanzen einen Fehler für eine bestimmte Konsistenzprüfung meldet, schlägt die Konsistenzprüfung für die gesamte Umgebung fehl. Wie bei Code-Qualitäts- und Leistungstests werden diese Konsistenzprüfungen in Kategorien unterteilt und über das dreistufige Gatingsystem gemeldet. Der einzige Unterschied besteht darin, dass im Falle von Sicherheitstests keine Schwellenwerte vorhanden sind. Alle Konsistenzprüfungen werden bestanden oder sind fehlgeschlagen.

In der folgenden Tabelle sind die Konsistenzprüfungen aufgeführt.

| Name | Implementierung der Konsistenzprüfung | Kategorie |
|---|---|---|
| Deserialisierungs-Firewall-Attach-API-Bereitschaft befindet sich in einem akzeptablen Zustand. | [Deserialisierungs-Firewall-Attach-API-Bereitschaft](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Kritisch |
| Deserialisierungs-Firewall ist funktionsfähig. | [Deserialisierungs-Firewall funktionsfähig](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Kritisch |
| Deserialisierungs-Firewall wird geladen. | [Deserialisierungs-Firewall geladen](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/mitigating-serialization-issues.html#security) | Kritisch |
| `AuthorizableNodeName` -Implementierung zeigt keine autorisierbare ID im Knotennamen/Pfad an. | [Namenserstellung für autorisierbare Knoten](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | Kritisch |
| Standardkennwörter wurden geändert. | [Standard-Anmeldekonten](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#users-and-groups-in-aem) | Kritisch |
| Sling-Standard-GET-Servlet ist vor DOS-Angriffen geschützt. | Sling Get Servlet | Kritisch |
| Der Sling Java Script-Handler ist entsprechend konfiguriert. | Sling Java Script Handler | Kritisch |
| Der Sling JSP Script-Handler ist entsprechend konfiguriert. | Sling JSP Script Handler | Kritisch |
| SSL ist richtig konfiguriert. | SSL-Konfiguration | Kritisch |
| Es werden keine offensichtlich unsicheren Benutzerprofilrichtlinien gefunden. | Standardzugriff auf Benutzerprofil | Kritisch |
| Der Sling Referrer-Filter ist konfiguriert, um CSRF-Angriffe zu verhindern. | [Sling Referrer-Filter](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#security) | Wichtig |
| Adobe Granite HTML Library Manager ist ordnungsgemäß konfiguriert. | Konfiguration des CQ-HTML-Bibliotheksmanagers | Wichtig |
| CRXDE-Support-Bundle ist deaktiviert. | CRXDE-Support | Wichtig |
| Sling DavEx Bundle und Servlet sind deaktiviert. | DavEx-Konsistenzprüfung | Wichtig |
| Beispielinhalt ist nicht installiert.. | Pakete mit Beispielinhalt | Wichtig |
| Sowohl der WCM-Anfrage-Filter als auch der WCM-Debug-Filter sind deaktiviert. | [WCM-Filterkonfiguration](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/osgi-configuration-settings.html#configuring) | Wichtig |
| Sling WebDAV Bundle und Servlet sind angemessen konfiguriert. | WebDAV-Konsistenzprüfung | Wichtig |
| Der Webserver ist so konfiguriert, dass Clickjacking verhindert wird. | Webserver-Konfiguration | Wichtig |
| Die Replikation verwendet nicht die `admin` Benutzer. | Benutzerreplikation und -transport | Info |

## Leistungstests {#performance-testing}

### AEM Sites {#aem-sites}

Cloud Manager führt Leistungstests für AEM Sites-Programme aus. Der Leistungstest wird ca. 30 Minuten lang ausgeführt, indem virtuelle Benutzer (Container) nach oben geschleudert werden, um tatsächliche Benutzer für den Zugriff auf Seiten in Staging-Umgebungen zu simulieren, um Traffic zu simulieren. Diese Seiten werden mit einem Crawler gefunden.

#### Virtuelle Benutzer {#virtual-users}

Die Anzahl der virtuellen Benutzer oder Container, die von Cloud Manager gespeist werden, wird durch die KPIs (Antwortzeit und Seitenansichten/min) gesteuert, die vom Benutzer mit der **Business Owner** Rolle während [Erstellen oder Bearbeiten des Programms.](setting-up-program.md) Basierend auf den definierten KPIs werden bis zu 10 Container ausgespült, die tatsächliche Benutzer simulieren. Die zum Testen ausgewählten Seiten werden aufgeteilt und jedem virtuellen Benutzer zugewiesen.

#### Crawler {#crawler}

Vor Beginn des 30-minütigen Testzeitraums durchsucht Cloud Manager die Staging-Umgebung anhand eines Satzes von einer oder mehreren vom Customer Success Engineer konfigurierten Seed-URLs. Ausgehend von diesen URLs wird der HTML-Code jeder Seite überprüft und Links werden breitenorientiert durchsucht. Dieser Crawling-Vorgang ist auf maximal 5.000 Seiten beschränkt. Für Anfragen des Crawlers gilt ein festes Zeitlimit von 10 Sekunden.

#### Seitensätze zum Testen {#page-sets}

Die Seiten werden nach drei Seitensätzen ausgewählt. Cloud Manager verwendet die Zugriffsprotokolle der AEM-Instanzen in Produktions- und Staging-Umgebungen, um die folgenden Behälter zu ermitteln.

* **Beliebte Live-Seiten** - Diese Option ist ausgewählt, um sicherzustellen, dass die beliebtesten Seiten getestet werden, auf die Live-Kunden zugreifen. Cloud Manager liest das Zugriffsprotokoll und ermittelt die 25 am häufigsten aufgerufenen Seiten von Live-Kunden, um eine Liste von `Popular Live Pages` zu generieren. Die Schnittmenge dieser Komponenten, die auch in der Staging-Umgebung vorhanden sind, wird dann in der Staging-Umgebung durchsucht.

* **Andere Live-Seiten** - Diese Option ist ausgewählt, um sicherzustellen, dass die Seiten getestet werden, die nicht zu den 25 beliebtesten Live-Seiten gehören, die möglicherweise nicht beliebt, aber zum Testen wichtig sind. Ähnlich wie bei gängigen Live-Seiten werden diese aus dem Zugriffsprotokoll extrahiert und müssen auch in der Staging-Umgebung vorhanden sein.

* **Neue Seiten** - Diese Option ist ausgewählt, um neue Seiten zu testen, die möglicherweise nur für die Staging-Umgebung und noch nicht für die Produktion bereitgestellt wurden, aber getestet werden müssen.

##### Verteilung des Traffics auf die ausgewählten Seitensätze {#distribution-of-traffic}

Sie können zwischen einem und allen drei Sets auf der **Test** Registerkarte Ihres [Pipeline-Konfiguration.](configuring-production-pipelines.md) Die Verteilung des Traffics basiert auf der Anzahl der ausgewählten Sets. Das heißt, wenn alle drei ausgewählt sind, werden 33 % der gesamten Seitenansichten auf jeden Satz verteilt. Wenn zwei ausgewählt sind, werden 50 % zu jedem Satz hinzugefügt. Wenn eine ausgewählt ist, werden 100 % des Traffics auf diese Gruppe geleitet.

Betrachten wir dieses Beispiel.

* Es gibt eine 50/50-Aufteilung zwischen den beliebten Live-Seiten und den neuen Seiten-Sets.
* Andere Live-Seiten werden nicht verwendet.
* Der neue Seitensatz enthält 3000 Seiten.
* wird für den KPI der Seitenansichten pro Minute ein Wert von 200 festgelegt.

Für den 30-minütigen Testzeitraum gilt in diesem Fall:

* Jede der 25 Seiten im beliebten Live-Seitensatz wird 120-mal aufgerufen: `((200 * 0.5) / 25) * 30 = 120`
* Jede der 3000 Seiten im neuen Seitensatz wird einmal aufgerufen: `((200 * 0.5) / 3000) * 30 = 1`

#### Tests und Reporting {#testing-reporting}

Cloud Manager führt Leistungstests für AEM Sites-Programme durch, indem für einen 30-minütigen Testzeitraum Seiten standardmäßig als nicht authentifizierter Benutzer auf dem Staging-Veröffentlichungsserver abgerufen werden. Sie misst die von virtuellen Benutzern generierten Metriken (Antwortzeit, Fehlerrate, Ansichten pro Minute usw.) für jede Seite sowie verschiedene Metriken auf Systemebene (CPU, Arbeitsspeicher, Netzwerkdaten) für alle Instanzen gemessen werden.

Die folgende Tabelle fasst die Leistungstestmatrix mit dem dreistufigen Gatingsystem zusammen.

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

Siehe Abschnitt . [Authentifizierte Leistungstests](#authenticated-performance-testing) Weitere Informationen zur Verwendung der grundlegenden Authentifizierung für Leistungstests für Sites und Assets.

>[!NOTE]
>
>Sowohl Autoren- als auch Veröffentlichungsinstanzen werden während des Testzeitraums überwacht. Wenn keine Metrik für eine Instanz abgerufen wird, wird diese Metrik als unbekannt gemeldet und der entsprechende Schritt schlägt fehl.

#### Optional - Authentifizierte Leistungstests {#authenticated-performance-testing}

Bei Bedarf können AMS-Kunden mit authentifizierten Sites einen Benutzernamen und ein Kennwort angeben, mit denen Cloud Manager während der Sites-Leistungstests auf die Website zugreift.

Benutzername und Kennwort werden als Pipeline-Variablen mit den Namen angegeben `CM_PERF_TEST_BASIC_USERNAME` und `CM_PERF_TEST_BASIC_PASSWORD`.

Der Benutzername sollte in einer `string` und das Kennwort in einer `secretString` -Variable. Wenn beide angegeben sind, enthält jede Anfrage des Leistungstest-Crawlers und der virtuellen Testbenutzer diese Anmeldedaten als einfache HTTP-Standardauthentifizierung.

Um diese Variablen mithilfe der Cloud Manager-Befehlszeilenschnittstelle festzulegen, führen Sie Folgendes aus:

```shell
$ aio cloudmanager:set-pipeline-variables <pipeline id> --variable CM_PERF_TEST_BASIC_USERNAME <username> --secret CM_PERF_TEST_BASIC_PASSWORD <password>
```

Weitere Informationen finden Sie im Dokument . [Patch User Pipeline-Variablen](https://www.adobe.io/apis/experiencecloud/cloud-manager/api-reference.html#/Variables/patchPipelineVariables) , um zu erfahren, wie Sie die API verwenden.

### AEM Assets {#aem-assets}

Cloud Manager führt Leistungstests für AEM Assets-Programme durch, indem Assets für einen 30-minütigen Testzeitraum wiederholt hochgeladen werden.

#### Onboarding-Anforderungen {#onboarding-requirement}

Für Assets-Leistungstests erstellt Ihr Customer Success Engineer einen `cloudmanager` Benutzer und Kennwort beim Einstieg des Autors in die Staging-Umgebung. Für die Leistungstestschritte ist ein Benutzer erforderlich, der `cloudmanager` und das dazugehörige Kennwort, das von Ihrem CSE eingerichtet wurde. Diese sollte weder aus der Autoreninstanz entfernt noch ihre Berechtigungen geändert werden. Dies führt wahrscheinlich zu einem Fehler beim Assets-Leistungstest.

#### Bilder und Assets zum Testen {#assets-for-testing}

Kunden können ihre eigenen Assets zum Testen hochladen. Dies kann über die **Pipeline-Einrichtung** oder **Bearbeiten** angezeigt. Dabei werden typische Bildformate wie JPEG, PNG, GIF und BMP sowie Photoshop-, Illustrator- und Postscript-Dateien unterstützt.

Wenn keine Bilder hochgeladen werden, verwendet Cloud Manager zum Testen ein Standardbild und PDF-Dokumente.

#### Verteilung von Assets für Tests {#distribution-of-assets}

Die Verteilung der Anzahl der Assets jedes Typs, die pro Minute hochgeladen werden, wird im **Pipeline-Einrichtung** oder **Bearbeiten** angezeigt.

Wenn beispielsweise eine Aufteilung von 70/30 verwendet wird und pro Minute 10 Assets hochgeladen werden, werden pro Minute 7 Bilder und 3 Dokumente hochgeladen.

#### Tests und Reporting {#testing-and-reporting}

Cloud Manager erstellt in der Autoreninstanz einen Ordner mit dem Benutzernamen und dem Kennwort, die vom CSE im [Onboarding-Anforderungen](#onboaring-requirements) Abschnitt. Assets werden dann mithilfe einer Open-Source-Bibliothek in den Ordner hochgeladen. Die vom Assets-Testschritt ausgeführten Tests werden mithilfe eines [Open-Source-Bibliothek.](https://github.com/adobe/toughday2) Während der 30-minütigen Testdauer werden sowohl die Verarbeitungszeit für jedes Asset als auch verschiedene Metriken auf Systemebene gemessen. Diese Funktion kann sowohl PDF- als auch Bilddokumente hochladen.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument . [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md) , um mehr zu erfahren. Siehe Dokument . [Einrichten des Programms](setting-up-program.md) , um zu erfahren, wie Sie Ihr Programm einrichten und Ihre KPIs definieren.

### Diagramme mit Leistungstestergebnissen {#performance-testing-results-graphs}

Eine Reihe von Metriken ist im **Dialogfeld &quot;Leistungstest&quot;**

![Liste der Metriken](assets/understand_test-results-screen1.png)

Die Metrikbedienfelder können erweitert werden, um ein Diagramm anzuzeigen, einen Link zu einem Download bereitzustellen oder beides.

![Metriken als Diagramm erweitert](assets/screen_shot_2018-09-05at83933pm.png)

Diese Funktion ist für die folgenden Metriken verfügbar.

* **CPU-Auslastung**
   * Ein Diagramm zur CPU-Auslastung während des Testzeitraums

* **Festplatten-I/O-Wartezeit**
   * Ein Diagramm zur Festplatten-I/O-Wartezeit während des Testzeitraums

* **Seitenfehlerrate**
   * Ein Diagramm zu den Seitenfehlern pro Minute während des Testzeitraums
   * Eine CSV-Datei mit den Seiten, die während des Tests einen Fehler verursacht haben

* **Festplatten-Bandbreitenauslastung**
   * Ein Diagramm zur Bandbreitenauslastung während des Testzeitraums

* **Netzwerk-Bandbreitenauslastung**
   * Ein Diagramm zur Auslastung der Netzwerkbandbreite während des Testzeitraums

* **Spitzenreaktionszeit**
   * Ein Diagramm zur Spitzenreaktionszeit pro Minute während des Testzeitraums

* **95. Perzentil der Reaktionszeit**
   * Ein Diagramm zum 95. Perzentil der Reaktionszeit pro Minute während des Testzeitraums
   * Eine CSV-Datei mit den Seiten, deren 95. Perzentil der Reaktionszeit die definierte KPI überschritten hat

## Optimierung der Inhaltspaketsuche {#content-package-scanning-optimization}

Im Rahmen des Qualitätsanalyseprozesses führt Cloud Manager die Analyse der Inhaltspakete durch, die vom Maven-Build erstellt wurden. Cloud Manager bietet Optimierungen, um diesen Prozess zu beschleunigen, der bei der Einhaltung bestimmter Paketbeschränkungen wirksam ist. Am wichtigsten ist die Optimierung, die für Projekte durchgeführt wird, die ein einzelnes Inhaltspaket ausgeben, das allgemein als &quot;all&quot;-Paket bezeichnet wird und eine Reihe anderer Inhaltspakete enthält, die vom Build erstellt wurden und als übersprungen markiert sind. Wenn Cloud Manager dieses Szenario erkennt, anstatt das Paket &quot;all&quot;zu entpacken, werden die einzelnen Inhaltspakete direkt gescannt und basierend auf Abhängigkeiten sortiert. Betrachten Sie beispielsweise die folgende Build-Ausgabe.

* `all/myco-all-1.0.0-SNAPSHOT.zip` (content-package)
* `ui.apps/myco-ui.apps-1.0.0-SNAPSHOT.zip` (skipped-content-package)
* `ui.content/myco-ui.content-1.0.0-SNAPSHOT.zip` (skipped-content-package)

Wenn die einzigen Elemente in `myco-all-1.0.0-SNAPSHOT.zip` die beiden übersprungenen Inhaltspakete sind, werden die beiden eingebetteten Pakete anstelle des Inhaltspakets &quot;all&quot;gescannt.

Bei Projekten, die Dutzende von eingebetteten Paketen produzieren, wird diese Optimierung nachweislich pro Pipeline-Ausführung um bis zu 10 Minuten reduziert.

Ein spezieller Fall kann auftreten, wenn das Inhaltspaket &quot;all&quot;eine Kombination aus übersprungenen Inhaltspaketen und OSGi-Bundles enthält. Wenn beispielsweise `myco-all-1.0.0-SNAPSHOT.zip` die beiden zuvor erwähnten eingebetteten Pakete sowie eines oder mehrere OSGi-Pakete enthielt, wird ein neues, minimales Inhaltspaket nur mit den OSGi-Bundles erstellt. Dieses Paket erhält immer den Namen `cloudmanager-synthetic-jar-package` und die enthaltenen Bundles in `/apps/cloudmanager-synthetic-installer/install`.

>[!NOTE]
>
>* Diese Optimierung wirkt sich nicht auf die Pakete aus, die in AEM bereitgestellt werden.
>* Da die Übereinstimmung zwischen den eingebetteten Inhaltspaketen und den übersprungenen Inhaltspaketen auf Dateinamen basiert, kann diese Optimierung nicht durchgeführt werden, wenn mehrere übersprungene Inhaltspakete genau denselben Dateinamen haben oder wenn der Dateiname beim Einbetten geändert wird.