---
title: Benutzerspezifische Regeln für Code-Qualität
description: Diese Seite beschreibt die Qualitätsregeln für benutzerspezifischen Code, die von Cloud Manager im Rahmen der Code-Qualitätstests ausgeführt werden. Sie basieren auf Best Practices von AEM Engineering.
uuid: a7feb465-1982-46be-9e57-e67b59849579
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: d2338c74-3278-49e6-a186-6ef62362509f
feature: Code Quality Rules
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: d4c92a36ca3af123730d68fedf1dbf7ee819c66b
workflow-type: tm+mt
source-wordcount: '3609'
ht-degree: 99%

---


# Qualitätsregeln für benutzerspezifischen Code {#custom-code-quality-rules}

Diese Seite beschreibt die Qualitätsregeln für benutzerspezifischen Code, die von Cloud Manager im Rahmen der [Code-Qualitätstests ausgeführt werden.](understand-your-test-results.md) Sie basieren auf Best Practices von AEM Engineering.

>[!NOTE]
>
>as a Cloud Service Informationen zu benutzerspezifischen Regeln für die Code-Qualität von Cloud Manager finden Sie unter AEM [zu dieser Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/custom-code-quality-rules.html?lang=de#using-cloud-manager).

>[!NOTE]
>
>Die hier bereitgestellten Code-Beispiele dienen nur Veranschaulichungszwecken. In der [Dokumentation zu den Konzepten von SonarQube](https://docs.sonarqube.org/7.4/user-guide/concepts/) finden Sie weitere Informationen zu den betreffenden Konzepten und Qualitätsregeln.

## SonarQube-Regeln {#sonarqube-rules}

Im folgenden Abschnitt werden die SonarQube-Regeln beschrieben, die von Cloud Manager ausgeführt werden.

### Verwenden Sie keine potenziell gefährlichen Funktionen {#do-not-use-potentially-dangerous-functions}

* **Schlüssel**: CQRules:CWE-676
* **Typ**: Sicherheitslücke
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Die Methoden `Thread.stop()` und `Thread.interrupt()` können schwer zu reproduzierende Probleme und in einigen Fällen Sicherheitslücken verursachen. Daher sollte deren Verwendung sorgfältig überwacht und validiert werden. Im Allgemeinen ist die Nachrichtenübergabe eine sicherere Möglichkeit, ähnliche Ziele zu erreichen.

#### Nicht konformer Code {#non-compliant-code}

```java
public class DontDoThis implements Runnable {
  private Thread thread;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    thread.stop();  // UNSAFE!
  }
 
  public void run() {
    while (true) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

#### Konformer Code {#compliant-code}

```java
public class DoThis implements Runnable {
  private Thread thread;
  private boolean keepGoing = true;
 
  public void start() {
    thread = new Thread(this);
    thread.start();
  }
 
  public void stop() {
    keepGoing = false;
  }
 
  public void run() {
    while (this.keepGoing) {
        somethingWhichTakesAWhileToDo();
    }
  }
}
```

### Verwenden Sie keine Formatzeichenfolgen, die extern gesteuert werden können {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Schlüssel**: CQRules:CWE-134
* **Typ**: Sicherheitslücke
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Durch die Verwendung einer Formatzeichenfolge aus einer externen Quelle (z. B. einem Abfrageparameter oder anwendergenerierten Inhalten) kann ein Programm für Denial-of-Service-Angriffe anfällig werden. Es gibt Fälle, in denen eine Formatzeichenfolge von außen gesteuert werden kann, jedoch nur aus vertrauenswürdigen Quellen zulässig ist.

#### Nicht konformer Code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP-Anfragen sollten immer Zeitüberschreitungswerte für Sockets und Verbindungen enthalten. {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Schlüssel**: CQRules:ConnectionTimeoutMechanism
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.6.0

Beim Ausführen von HTTP-Anfragen aus einem AEM-Programm muss unbedingt sichergestellt sein, dass korrekte Zeitüberschreitungswerte konfiguriert werden, um unnötige Thread-Nutzung zu vermeiden. Leider sind im Java-Standard-HTTP-Client `java.net.HttpUrlConnection` und dem häufig verwendeten Client für Apache-HTTP-Komponenten standardmäßig keine Zeitüberschreitungen festgelegt, sodass diese explizit festgelegt werden müssen. Als Best Practice gilt, diese Zeitüberschreitungen bei maximal 60 Sekunden zu definieren.

#### Nicht konformer Code {#non-compliant-code-2}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void dontDoThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  HttpClient httpClient = builder.build();

  // do something with the client
}

public void dontDoThisEither() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

#### Konformer Code {#compliant-code-1}

```java
@Reference
private HttpClientBuilderFactory httpClientBuilderFactory;
 
public void doThis() {
  HttpClientBuilder builder = httpClientBuilderFactory.newBuilder();
  RequestConfig requestConfig = RequestConfig.custom()
    .setConnectTimeout(5000)
    .setSocketTimeout(5000)
    .build();
  builder.setDefaultRequestConfig(requestConfig);
 
  HttpClient httpClient = builder.build();
   
  // do something with the client
}

public void orDoThis() {
  URL url = new URL("http://www.google.com");
  URLConnection urlConnection = url.openConnection();
  urlConnection.setConnectTimeout(5000);
  urlConnection.setReadTimeout(5000);
 
  BufferedReader in = new BufferedReader(new InputStreamReader(
    urlConnection.getInputStream()));
 
  String inputLine;
  while ((inputLine = in.readLine()) != null) {
    logger.info(inputLine);
  }
 
  in.close();
}
```

### ResourceResolver-Objekte sollten immer geschlossen werden {#resourceresolver-objects-should-always-be-closed}

* **Schlüssel**: CQRules:CQBP-72
* **Typ**: Code Smell
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

`ResourceResolver`-Objekte, die aus `ResourceResolverFactory` abgerufen werden, verbrauchen Systemressourcen. Obwohl es Möglichkeiten gibt, diese Ressourcen freizugeben, wenn ein `ResourceResolver` nicht mehr verwendet wird, ist es effizienter, alle offenen `ResourceResolver`-Objekte explizit durch Aufruf der Methode `close()` zu schließen.

Es ist ein verbreiteter Irrtum, dass `ResourceResolver`-Objekte, die mit einer bestehenden JCR-Sitzung erstellt wurden, nicht explizit geschlossen werden sollten, da sonst die zugrunde liegende JCR-Sitzung geschlossen wird. Dies ist nicht der Fall. Gleichgültig, wie ein `ResourceResolver` geöffnet wird, sollte es geschlossen werden, wenn es nicht mehr benötigt wird. Da `ResourceResolver` die `Closeable`-Schnittstelle implementiert, kann auch die Syntax `try-with-resources` statt eines expliziten Aufrufs von `close()` verwendet werden.

#### Nicht konformer Code {#non-compliant-code-4}

```java
public void dontDoThis(Session session) throws Exception {
  ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
  // do some stuff with the resolver
}
```

#### Konformer Code {#compliant-code-2}

```java
public void doThis(Session session) throws Exception {
  ResourceResolver resolver = null;
  try {
    resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object)session));
    // do something with the resolver
  } finally {
    if (resolver != null) {
      resolver.close();
    }
  }
}

public void orDoThis(Session session) throws Exception {
  try (ResourceResolver resolver = factory.getResourceResolver(Collections.singletonMap("user.jcr.session", (Object) session))){
    // do something with the resolver
  }
}
```

### Verwenden Sie keine Sling-Servlet-Pfade zum Registrieren von Servlets {#do-not-use-sling-servlet-paths-to-register-servlets}

* **Schlüssel**: CQRules:CQBP-75
* **Typ**: Code Smell
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Wie in der [Sling-Dokumentation](http://sling.apache.org/documentation/the-sling-engine/servlets.html) beschrieben, sollten Servlets nicht über Pfade verknüpft werden. Pfadgebundene Servlets können keine standardmäßigen JCR-Zugriffssteuerungselemente verwenden, sodass besonders strenge Sicherheitsmaßnahmen erforderlich sind. Statt pfadgebundene Servlets zu verwenden, wird empfohlen, Knoten im Repository zu erstellen und Servlets nach Ressourcentyp zu registrieren.

#### Nicht konformer Code {#non-compliant-code-5}

```java
@Component(property = {
  "sling.servlet.paths=/apps/myco/endpoint"
})
public class DontDoThis extends SlingAllMethodsServlet {
 // implementation
}
```

### Ausnahmefehler sollten entweder protokolliert oder ausgegeben werden, aber nicht beides {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

* **Schlüssel**: CQRules:CQBP-44---CatchAndEitherLogOrThrow
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Im Allgemeinen sollte eine Ausnahme genau einmal protokolliert werden. Die mehrfache Protokollierung von Ausnahmen kann verwirren, da unklar ist, wie oft eine Ausnahme aufgetreten ist. Dies wird vor allem dadurch verursacht, dass eine erfasste Ausnahme sowohl protokolliert als auch ausgegeben wird.

#### Nicht konformer Code {#non-compliant-code-6}

```java
public void dontDoThis() throws Exception {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
    throw e;
  }
}
```

#### Konformer Code {#compliant-code-3}

```java
public void doThis() {
  try {
    someOperation();
  } catch (Exception e) {
    logger.error("something went wrong", e);
  }
}

public void orDoThis() throws MyCustomException {
  try {
    someOperation();
  } catch (Exception e) {
    throw new MyCustomException(e);
  }
}
```

### Geben Sie Throw-Anweisungen möglichst nicht unmittelbar nach Log-Anweisungen an {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

* **Schlüssel**: CQRules:CQBP-44---ConsecutivelyLogAndThrow
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Ein weiteres gängiges Muster, das vermieden werden sollte, ist die Protokollierung einer Nachricht, direkt gefolgt von der Auslösung einer Ausnahme. Dadurch erscheint die Ausnahmemeldung in Protokolldateien meist doppelt.

#### Nicht konformer Code {#non-compliant-code-7}

```java
public void dontDoThis() throws Exception {
  logger.error("something went wrong");
  throw new RuntimeException("something went wrong");
}
```

#### Konformer Code {#compliant-code-4}

```java
public void doThis() throws Exception {
  throw new RuntimeException("something went wrong");
}
```

### Vermeiden Sie beim Verarbeiten von GET- oder HEAD-Anforderungen die Protokollierung bei INFO {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Schlüssel**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Typ**: Code Smell
* **Schweregrad**: Gering

Im Allgemeinen sollten mit der Protokollierungsstufe INFO wichtige Aktionen abgegrenzt werden. Standardmäßig ist AEM so konfiguriert, dass auf der INFO-Ebene oder höher protokolliert wird. GET- und HEAD-Methoden sollten nur schreibgeschützte Vorgänge sein und stellen daher keine wichtigen Aktionen dar. Die Protokollierung auf INFO-Ebene als Antwort auf GET- oder HEAD-Anfragen füllt das Protokoll wahrscheinlich mit erheblichen Mengen überflüssiger Informationen, sodass es schwieriger wird, nützliche Informationen in Protokolldateien zu finden. Bei der Verarbeitung von GET- oder HEAD-Anfragen sollte die Protokollierung entweder bei einem Fehler auf WARN- oder ERROR-Ebene erfolgen oder auf DEBUG- oder TRACE-Ebene, wenn eine tiefgehendere Fehlerbehebung hilfreich wäre.

>[!NOTE]
>
>Dies gilt nicht für die Protokollierung von access.log-type für jede Anfrage.

#### Nicht konformer Code {#non-compliant-code-8}

```java
public void doGet() throws Exception {
  logger.info("handling a request from the user");
}
```

#### Konformer Code {#compliant-code-5}

```java
public void doGet() throws Exception {
  logger.debug("handling a request from the user.");
}
```

### Verwenden Sie Exception.getMessage() nicht als ersten Parameter einer Protokollierungsanweisung {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Schlüssel**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Als Best Practice sollten Protokollmeldungen kontextbezogene Informationen darüber enthalten, wo eine Programmausnahme aufgetreten ist. Während der Kontext auch mit Stacktraces bestimmt werden kann, ist die Protokollmeldung meist besser lesbar und verständlicher. Wenn Sie eine Ausnahme protokollieren, ist es daher nicht empfehlenswert, die Ausnahmemeldung als Protokollmeldung zu verwenden. Die Ausnahmemeldung enthält Informationen dazu, was nicht funktioniert hat, während die Protokollmeldung dem Protokollleser mitteilt, was das Programm getan hat, als die Ausnahme auftrat. Die Ausnahmemeldung wird weiterhin protokolliert. Wenn Sie Ihre eigene Meldung festlegen, werden die Protokolle verständlicher.

#### Nicht konformer Code {#non-compliant-code-9}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error(e.getMessage(), e);
  }
}
```

#### Konformer Code {#compliant-code-6}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Die Protokollierung in Catch-Blöcken sollte auf WARN- oder ERROR-Ebene erfolgen {#logging-in-catch-blocks-should-be-at-the-warn-or-error-level}

* **Schlüssel**: CQRules:CQBP-44---WrongLogLevelInCatchBlock
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Wie der schon Name sagt, sollten Java-Ausnahmen immer unter Ausnahmebedingungen verwendet werden. Wenn eine Ausnahme erfasst wird, muss daher sichergestellt sein, dass Protokollmeldungen auf der entsprechenden Ebene – WARN oder ERROR – protokolliert werden. damit diese Meldungen in den Protokollen korrekt angezeigt werden.

#### Nicht konformer Code {#non-compliant-code-10}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.debug(e.getMessage(), e);
  }
}
```

#### Konformer Code {#compliant-code-7}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Drucken Sie keine Stacktraces in der Konsole {#do-not-print-stack-traces-to-the-console}

* **Schlüssel**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Kontext ist zum Verständnis von Protokollmeldungen äußerst wichtig. Durch Verwendung von `Exception.printStackTrace()` wird bei der Ausgabe des Standardfehler-Streams nur der Stacktrace ausgegeben, sodass der gesamte Kontext verloren geht. Bei einem Multi-Thread-Programm wie AEM kann es beim parallelen Drucken mehrerer Ausnahmen mit dieser Methode zu einer Überlappung der Stacktraces kommen, was erhebliche Verwirrung verursacht. Ausnahmen sollten daher nur über das Protokollierungs-Framework protokolliert werden.

#### Nicht konformer Code {#non-compliant-code-11}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

#### Konformer Code {#compliant-code-8}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Verzichten Sie auf Ausgaben als Standardausgabe oder Standardfehler {#do-not-output-to-standard-output-or-standard-error}

* **Schlüssel**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Die Protokollierung in AEM sollte immer über das Protokollierungs-Framework (SLF4J) erfolgen. Durch die direkte Ausgabe an Standardausgabe- oder Standardfehler-Streams gehen strukturelle und kontextbezogene Informationen verloren, die vom Protokollierungs-Framework bereitgestellt werden. Außerdem kann diese Vorgehensweise in einigen Fällen zu Leistungseinbußen führen.

#### Nicht konformer Code {#non-compliant-code-12}

```java
public void dontDoThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    System.err.println("Unable to do something");
  }
}
```

#### Konformer Code {#compliant-code-9}

```java
public void doThis() {
  try {
    someMethodThrowingAnException();
  } catch (Exception e) {
    logger.error("Unable to do something", e);
  }
}
```

### Vermeiden Sie hartcodierte /apps- und /libs-Pfade {#avoid-hardcoded-apps-and-libs-paths}

* **Schlüssel**: CQRules:CQBP-71
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Im Allgemeinen sollten Pfade, die mit `/libs` und `/apps` beginnen, nicht hartcodiert werden, da die Pfade, auf die sie verweisen, meist als Pfade relativ zum Sling-Suchpfad (der standardmäßig auf `/libs,/apps` festgelegt ist) gespeichert werden. Durch die Angabe des absoluten Pfads können geringfügige Fehler entstehen, die erst später im Projektlebenszyklus deutlich werden.

#### Nicht konformer Code {#non-compliant-code-13}

```java
public boolean dontDoThis(Resource resource) {
  return resource.isResourceType("/libs/foundation/components/text");
}
```

#### Konformer Code {#compliant-code-10}

```java
public void doThis(Resource resource) {
  return resource.isResourceType("foundation/components/text");
}
```

### Sling-Planung sollte nicht verwendet werden {#sonarqube-sling-scheduler}

* **Schlüssel**: CQRules:AMSCORE-554
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die Sling-Planung darf nicht für Aufgaben verwendet werden, die eine garantierte Ausführung erfordern. Über Sling geplante Aufträge garantieren die Ausführung und eignen sich besser für Umgebungen mit und ohne Cluster.

Weitere Informationen zum Umgang mit Sling-Aufträgen in einer Umgebung mit Clustern finden Sie unter [Apache Sling Eventing und Job Handling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html).

### Veraltete AEM-APIs sollten nicht verwendet werden {#sonarqube-aem-deprecated}

* **Schlüssel**: AMSCORE-553
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die AEM-API-Oberfläche wird ständig überarbeitet, um APIs zu identifizieren, von deren Verwendung abgeraten wird und die daher als veraltet gelten.

In vielen Fällen sind diese APIs unter Verwendung der Standard-Java-Annotation *@Deprecated* abgekündigt und als solche durch `squid:CallToDeprecatedMethod` gekennzeichnet.

Es gibt jedoch Fälle, in denen eine API im Kontext von AEM veraltet ist, in anderen Kontexten jedoch nicht. Diese Regel identifiziert diese zweite Klasse.

## OakPAL-Inhaltsregeln {#oakpal-rules}

Im folgenden Abschnitt werden die von Cloud Manager durchgeführten OakPAL-Prüfungen vorgestellt.

>[!NOTE]
>
>OakPAL ist ein Framework, das Inhaltspakete mit einem eigenständigen Oak-Repository validiert. Es wurde von einem AEM Partner entwickelt, der mit dem 2019 AEM Rockstar North America Award ausgezeichnet wurde.

### Produkt-APIs, die mit @ProviderType kommentiert wurden, sollten von Kunden nicht implementiert oder erweitert werden {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Schlüssel**: CQBP-84
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.7.0

Die AEM-API enthält Java-Schnittstellen und -Klassen, die durch benutzerdefinierten Code lediglich verwendet, aber nicht implementiert werden sollen. Zum Beispiel ist die Schnittstelle `com.day.cq.wcm.api.Page` nur für die Implementierung durch AEM vorgesehen.

Wenn zu diesen Schnittstellen neue Methoden hinzugefügt werden, wirken sich diese zusätzlichen Methoden nicht auf den vorhandenen Code aus, der diese Schnittstellen verwendet. Daher wird das Hinzufügen neuer Methoden zu diesen Schnittstellen als abwärtskompatibel betrachtet. Wenn jedoch benutzerdefinierter Code eine dieser Schnittstellen implementiert, führt dieser benutzerspezifische Code ein Abwärtskompatibilitätsrisiko für den Kunden ein.

Schnittstellen (und Klassen), die nur von AEM implementiert werden sollen, werden mit `org.osgi.annotation.versioning.ProviderType` (oder in einigen Fällen mit einer veralteten Anmerkung `aQute.bnd.annotation.ProviderType`) kommentiert. Diese Regel identifiziert die Fälle, in denen eine solche Schnittstelle durch benutzerdefinierten Code implementiert wird (oder eine Klasse erweitert wird).

#### Nicht konformer Code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### Kundenpakete sollten keine Knoten unter /libs erstellen oder ändern {#oakpal-customer-package}

* **Schlüssel**: BannedPath
* **Typ**: Fehler
* **Schweregrad**: Blocker
* **Seit**: Version 2019.6.0

Es ist eine lange bestehende Best Practice, dass die Inhaltsstruktur `/libs` im AEM-Inhalts-Repository von Kunden als schreibgeschützt betrachtet werden sollte. Das Ändern von Knoten und Eigenschaften unter `/libs` ist mit erheblichen Risiken für umfassende und kleinere Aktualisierungen verbunden. Änderungen an `/libs` sollten nur durch Adobe über offizielle Kanäle vorgenommen werden.

### Pakete dürfen keine doppelten OSGi-Konfigurationen enthalten {#oakpal-package-osgi}

* **Schlüssel**: DuplicateOsgiConfigurations
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ein häufig auftretendes Problem bei komplexen Projekten besteht darin, dass dieselbe OSGi-Komponente mehrmals konfiguriert ist. Dadurch ist nicht mehr eindeutig, welche Konfiguration gelten soll. Diese Regel ist „Laufzeitmodus-fokussiert“, da sie nur Probleme erkennt, bei denen dieselbe Komponente mehrmals im gleichen Laufzeitmodus (oder mit der gleichen Kombination aus Laufzeitmodi) konfiguriert ist.

#### Nicht konformer Code {#non-compliant-code-osgi}

```text
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Konformer Code {#compliant-code-osgi}

```text
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Konfigurationen und Installationsordner dürfen nur OSGi-Knoten enthalten {#oakpal-config-install}

* **Schlüssel**: ConfigAndInstallShouldOnlyContainOsgiNodes
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Aus Sicherheitsgründen sind Pfade, die `/config/` und `/install/` enthalten, nur von Administratoranwendern in AEM lesbar und sollten nur für OSGi-Konfigurationen und OSGi-Bundles verwendet werden. Das Platzieren anderer Inhaltstypen in Pfade mit diesen Segmenten führt dazu, dass sich das Programm abhängig davon anders verhält, ob sie von Administratoren- oder Nicht-Administratoren verwendet wird.

Ein häufig auftretendes Problem ist die Verwendung von Knoten mit der Bezeichnung `config` in Komponentendialogfeldern oder beim Angeben der Rich-Text-Editor-Konfiguration für die Inline-Bearbeitung. Um dies zu beheben, sollte der fehlerhafte Knoten in einen kompatiblen Namen umbenannt werden. Nutzen Sie bei der Rich-Text-Editor-Konfiguration die Eigenschaft `configPath` im Knoten `cq:inplaceEditing`, um den neuen Speicherort anzugeben.

#### Nicht konformer Code {#non-compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Konformer Code {#compliant-code-config-install}

```text
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Pakete sollten nicht überlappen {#oakpal-no-overlap}

* **Schlüssel**: PackageOverlaps
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ähnlich wie bei der Regel [Pakete dürfen keine doppelten OSGi-Konfigurationen enthalten](#oakpal-package-osgi) ist dies ein häufiges Problem bei komplexen Projekten, bei denen mehrere separate Inhaltspakete in denselben Knotenpfad schreiben. Mit Inhaltspaketabhängigkeiten kann zwar ein konsistentes Ergebnis sichergestellt werden, Überlappungen sollten aber dennoch von vorneherein vermieden werden.

### Der standardmäßige Authoring-Modus sollte nicht die klassische Benutzeroberfläche sein {#oakpal-default-authoring}

* **Schlüssel**: ClassicUIAuthoringMode
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die OSGi-Konfiguration `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` definiert den standardmäßigen Authoring-Modus in AEM. Da die [klassische Benutzeroberfläche seit AEM 6.4 nicht mehr unterstützt wird](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html?lang=de), tritt jetzt ein Problem auf, wenn als standardmäßiger Authoring-Modus die klassische Benutzeroberfläche konfiguriert ist.

### Komponenten mit Dialogfeldern sollten Dialogfelder für die Touch-Benutzeroberfläche aufweisen {#oakpal-components-dialogs}

* **Schlüssel**: ComponentWithOnlyClassicUIDialog
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

AEM-Komponenten mit einem Dialogfeld für die klassische Benutzeroberfläche sollten immer über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen, um ein optimales Authoring-Erlebnis zu erzielen und mit dem Cloud Service-Implementierungsmodell kompatibel zu sein, bei dem die klassische Benutzeroberfläche nicht unterstützt wird. Diese Regel überprüft die folgenden Szenarien:

* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche (d. h. einem untergeordneten `dialog`-Knoten) muss über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über einen untergeordneten `cq:dialog`-Knoten).
* Eine Komponente mit einem Design-Dialogfeld für die klassische Benutzeroberfläche (d. h. einem `design_dialog`-Knoten) muss über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über einen untergeordneten `cq:design_dialog`-Knoten).
* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche und einem Design-Dialogfeld für die klassische Benutzeroberfläche muss sowohl über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche als auch über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen.

Die Dokumentation zu den AEM-Modernisierungs-Tools enthält Details zum Konvertieren von Komponenten aus der klassischen Benutzeroberfläche in die Touch-Benutzeroberfläche. Weitere Informationen finden Sie in der Dokumentation zu den [AEM-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/).

### Pakete sollten keinen veränderlichen und unveränderlichen Inhalt mischen {#oakpal-packages-immutable}

* **Schlüssel**: ImmutableMutableMixedPackage
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Um mit dem Cloud Service-Bereitstellungsmodell kompatibel zu sein, müssen einzelne Inhaltspakete entweder Inhalte für die unveränderlichen Bereiche des Repositorys (d. h. `/apps` und `/libs`) oder den veränderlichen Bereich (d. h. alles, was nicht in `/apps` oder `/libs` ist) enthalten, aber nicht beides. Beispielsweise ist ein Paket, das beide `/apps/myco/components/text and /etc/clientlibs/myco` enthält, nicht mit Cloud Service kompatibel und führt dazu, dass ein Problem gemeldet wird.

Weitere Informationen finden Sie in der Dokumentation zur [AEM-Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de).

>[!NOTE]
>
>Die Regel [Kundenpakete sollten Knoten unter /libs nicht erstellen oder ändern](#oakpal-customer-package) ist immer gültig.

### Rückwärtsreplikations-Agenten sollten nicht verwendet werden {#oakpal-reverse-replication}

* **Schlüssel**: ReverseReplication
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Cloud Service-Implementierungen unterstützen keine Rückwärtsreplikation. Weitere Informationen finden Sie unter [Versionshinweise: Entfernung von Replikations-Agenten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html?lang=de#replication-agents).

Kunden, die die Rückwärtsreplikation verwenden, sollten sich für alternative Lösungen an Adobe wenden.

### In Proxy-fähigen Client-Bibliotheken enthaltene Ressourcen sollten sich in einem Ordner mit dem Namen „resources“ befinden {#oakpal-resources-proxy}

* **Schlüssel**: ClientlibProxyResource
* **Typ**: Fehler
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Client-Bibliotheken können statische Ressourcen wie Bilder und Schriftarten enthalten. Wie unter [Verwenden von Client-seitigen Bibliotheken](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=de#using-preprocessors) beschrieben, müssen diese statischen Ressourcen bei der Verwendung von Proxy-fähigen Client-Bibliotheken in einem untergeordneten Ordner namens `resources` enthalten sein, damit sie in den Veröffentlichungsinstanzen effektiv referenziert werden können.

#### Nicht konformer Code {#non-compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Konformer Code {#compliant-proxy-enabled}

```text
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### Verwenden von nicht mit Cloud Service kompatiblen Workflow-Prozessen {#oakpal-usage-cloud-service}

* **Schlüssel**: CloudServiceIncompatibleWorkflowProcess
* **Typ**: Code Smell
* **Schweregrad**: Blocker
* **Seit**: Version 2021.2.0

Mit der Umstellung auf Asset-Microservices für die Asset-Verarbeitung in AEM Cloud Service werden verschiedene Workflow-Prozesse, die in lokalen und AMS-Versionen von AEM verwendet wurden, entweder nicht mehr unterstützt oder sind nicht mehr erforderlich.

Mit dem Migrations-Tool im [GitHub-Repository für AEM Assets as a Cloud Service](https://github.com/adobe/aem-cloud-migration) können Workflow-Modelle während der Migration in AEM as a Cloud Service aktualisiert werden.

### Von der Verwendung von statischen Vorlagen wird zugunsten von bearbeitbaren Vorlagen abgeraten {#oakpal-static-template}

* **Schlüssel**: StaticTemplateUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die Verwendung von statischen Vorlagen war in AEM-Projekten stets weit verbreitet. Editierbare Vorlagen werden jedoch dringend empfohlen, da sie die größte Flexibilität bieten und zusätzliche Funktionen unterstützen, die in statischen Vorlagen nicht vorhanden sind. Weitere Informationen finden Sie in der Dokumentation [Seitenvorlagen – Bearbeitbar](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-editable.html?lang=de).

Die Migration von statischen zu bearbeitbaren Vorlagen kann mithilfe der [AEM-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/) weitgehend automatisiert werden.

### Die Verwendung älterer Foundation-Komponenten wird nicht empfohlen {#oakpal-usage-legacy}

* **Schlüssel**: LegacyFoundationComponentUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die alten Foundation-Komponenten (d. h. Komponenten unter `/libs/foundation`) werden seit mehreren AEM-Versionen nicht mehr verwendet und wurden durch die [-Kernkomponenten ersetzt.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) Von der Verwendung der älteren Foundation-Komponenten als Basis für benutzerdefinierte Komponenten – sei es durch Überlagerung oder Vererbung – wird abgeraten und sie sollten in die entsprechende Kernkomponente konvertiert werden.

Diese Konvertierung kann durch die [AEM-Modernisierungs-Tools](https://opensource.adobe.com/aem-modernize-tools/) erleichtert werden.

### Es sollten nur unterstützte Ausführungsmodus-Namen und -Reihenfolgen verwendet werden {#oakpal-supported-runmodes}

* **Schlüssel**: SupportedRunmode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erzwingt eine strikte Benennungsrichtlinie für Runmode-Namen und eine strikte Reihenfolge für diese Laufzeitmodi. Die Liste der unterstützten Ausführungsmodi finden Sie in der Dokumentation unter [Bereitstellung für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=de#runmodes) und jede Abweichung davon wird als Problem identifiziert.

### Knoten für benutzerdefinierte Suchindex-Definitionen müssen direkt untergeordnete Knoten von /oak:index sein {#oakpal-custom-search}

* **Schlüssel**: OakIndexLocation
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`) direkt untergeordnete Knoten von `/oak:index` sind. Indizes an anderen Speicherorten müssen verschoben werden, um mit AEM Cloud Service kompatibel zu sein. Weitere Informationen zu Suchindizes finden Sie unter [Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=de).

### Knoten einer benutzerdefinierten Suchindex-Definition müssen die compatVersion 2 haben {#oakpal-custom-search-compatVersion}

* **Schlüssel**: IndexCompatVersion
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass die Eigenschaft `compatVersion` für benutzerdefinierte Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`) auf `2` festgelegt wird. Andere Werte werden von AEM Cloud Service nicht unterstützt. Weitere Informationen zu Suchindizes finden Sie unter [Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html).

### Absteigende Knoten einer benutzerdefinierten Suchindex-Definition müssen vom Typ nt:unstructured sein {#oakpal-descendent-nodes}

* **Schlüssel**: IndexDescendantNodeType
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Schwer behebbare Probleme können auftreten, wenn ein Knoten mit einer benutzerdefinierten Suchindex-Definition ungeordnete untergeordnete Knoten enthält. Um dies zu vermeiden, wird empfohlen, dass alle untergeordneten Knoten eines `oak:QueryIndexDefinition`-Knotens vom Typ `nt:unstructured` sein sollten.

### Benutzerdefinierte Knoten einer Suchindex-Definition müssen einen untergeordneten Knoten mit dem Namen „indexRules“ enthalten, der wiederum untergeordnete Knoten enthält {#oakpal-custom-search-index}

* **Schlüssel**: IndexRulesNode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Ein korrekt definierter benutzerdefinierter Suchindex-Definitionsknoten muss einen untergeordneten Knoten namens `indexRules` enthalten, der wiederum mindestens einen untergeordneten Knoten haben muss. Weitere Informationen finden Sie in der [Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### Knoten für benutzerdefinierte Suchindex-Definitionen müssen Namenskonventionen folgen {#oakpal-custom-search-definitions}

* **Schlüssel**: IndexName
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) nach einem bestimmten Muster benannt werden, das unter [Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html?lang=de#how-to-use) beschrieben wird.

### Knoten für benutzerdefinierte Suchindex-Definitionen müssen den Indextyp „lucene“ verwenden  {#oakpal-index-type-lucene}

* **Schlüssel**: IndexType
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`) eine `type`-Eigenschaft mit dem Wert `lucene` aufweisen. Die Indizierung mit älteren Indextypen muss vor der Migration auf AEM Cloud Service aktualisiert werden. Weitere Informationen finden Sie unter [Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use).

### Knoten einer benutzerdefinierten Suchindex-Definition dürfen keine Eigenschaft namens „seed“ enthalten {#oakpal-property-name-seed}

* **Schlüssel**: IndexSeedProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service verbietet, benutzerdefinierten Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`), eine Eigenschaft mit dem Namen `seed` zu enthalten. Die Indizierung mit dieser Eigenschaft muss vor der Migration zu AEM Cloud Service aktualisiert werden. Weitere Informationen finden Sie unter [Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use).

### Knoten einer benutzerdefinierten Suchindex-Definition dürfen keine Eigenschaft namens „reindex“ enthalten {#oakpal-reindex-property}

* **Schlüssel**: IndexReindexProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service verbietet, benutzerdefinierten Suchindex-Definitionen (d. h. Knoten vom Typ `oak:QueryIndexDefinition`), eine Eigenschaft mit dem Namen `reindex` zu enthalten. Die Indizierung mit dieser Eigenschaft muss vor der Migration zu AEM Cloud Service aktualisiert werden. Weitere Informationen finden Sie unter [Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use).

## Dispatcher-Optimierungs-Tool {#dispatcher-optimization-tool-rules}

Im folgenden Abschnitt werden die von Cloud Manager durchgeführten Prüfungen des Dispatcher Optimization Tools (DOT) aufgeführt. Folgen Sie den Links für jede Prüfung, um die GitHub-Definition und Details einzusehen.

* [Unerwartete Token in Dispatcher-Konfiguration](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Nicht zugeordnetes Zitat in Dispatcher-Konfiguration](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Fehlende Klammer in Dispatcher-Konfiguration](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Zusätzliche Klammer in Dispatcher-Konfiguration](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Fehlende erforderliche Eigenschaft in Dispatcher-Konfiguration](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Veraltete Eigenschaft in Dispatcher-Konfiguration](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Dispatcher-Konfiguration nicht gefunden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [Httpd Configuration Include file not found](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Dispatcher Configuration General](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [Für den Cache der Dispatcher-Veröffentlichungs-Farm sollte serveStaleOnError aktiviert sein](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Die Filter der Dispatcher-Veröffentlichungs-Farm sollten die standardmäßigen Ablehnungsregeln aus Version 6.x.x des AEM-Archetyps enthalten](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [Die statfileslevel-Eigenschaft des Cache der Dispatcher-Veröffentlichungs-Farm muss >= 2 sein](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [Die gracePeriod-Eigenschaft der Dispatcher-Veröffentlichungs-Farm muss >= 2 sein](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Jede Dispatcher-Farm muss einen eindeutigen Namen haben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [Die ignoreUrlParams-Regeln für den Cache der Dispatcher-Veröffentlichungs-Farm sollten als Zulassungsliste konfiguriert werden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Die Filter der Dispatcher-Veröffentlichungs-Farm sollten die zulässigen Sling-Selektoren als Zulassungsliste angeben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Die Filter der Dispatcher-Veröffentlichungs-Farm sollten die zulässigen Sling-Suffix-Muster als Zulassungsliste angeben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [Die Anweisung „Require all granted“ sollte nicht in einem VirtualHost Directory-Abschnitt mit einem Stammverzeichnis-Pfad verwendet werden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
