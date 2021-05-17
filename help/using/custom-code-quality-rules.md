---
title: Benutzerspezifische Regeln für Codequalität
seo-title: Benutzerspezifische Regeln für Codequalität
description: Auf dieser Seite erfahren Sie mehr über die benutzerspezifischen Regeln für die Code-Qualität, die von Cloud Manager ausgeführt werden.
seo-description: Auf dieser Seite erfahren Sie mehr über die benutzerspezifischen Regeln für die Code-Qualität, die von Adobe Experience Manager Cloud Manager ausgeführt werden.
uuid: a7feb465-1982-46be-9e57-e67b59849579
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: d2338c74-3278-49e6-a186-6ef62362509f
feature: Codequalitätsregeln
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: df2f598f91201d362f54b17e4092ff6bd6a72cec
workflow-type: tm+mt
source-wordcount: '3654'
ht-degree: 67%

---

# Benutzerspezifische Regeln für Codequalität {#custom-code-quality-rules}

>[!NOTE]
>Weitere Informationen zu benutzerspezifischen Code-Qualitätsregeln für Cloud Manager in AEM als Cloud Service finden Sie unter [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/custom-code-quality-rules.html?lang=en#using-cloud-manager).

Auf dieser Seite werden die benutzerspezifischen Regeln für die Code-Qualität beschrieben, die von Cloud Manager ausgeführt werden und auf bewährten Verfahren des AEM Engineering basieren.

>[!NOTE]
>Die hier bereitgestellten Code-Beispiele dienen nur Veranschaulichungszwecken. Weitere Informationen zu SonarQube-Konzepten und -Qualitätsregeln finden Sie unter [Konzepte](https://docs.sonarqube.org/7.4/user-guide/concepts/).

## SonarQube-Regeln {#sonarqube-rules}

Im folgenden Abschnitt werden die SonarQube-Regeln hervorgehoben:

### Verwenden Sie keine potenziell gefährlichen Funktionen {#do-not-use-potentially-dangerous-functions}

**Schlüssel**: CQRules:CWE-676

**Typ**: Sicherheitslücke

**Schweregrad**: Hoch

**Seit**: Version 2018.4.0

Die Methoden ***Thread.stop()*** und ***Thread.interrupt()*** können schwer reproduzierbare Probleme und in einigen Fällen Sicherheitslücken verursachen. Daher sollte deren Verwendung sorgfältig überwacht und validiert werden. Im Allgemeinen ist die Nachrichtenübergabe eine sicherere Möglichkeit, ähnliche Ziele zu erreichen.

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

**Schlüssel**: CQRules:CWE-134

**Typ**: Sicherheitslücke

**Schweregrad**: Hoch

**Seit**: Version 2018.4.0

Durch die Verwendung einer Formatzeichenfolge aus einer externen Quelle (z. B. einem Anbfrageparameter oder benutzergenerierten Inhalten) kann eine Anwendung für Denial-of-Service-Angriffe anfällig werden. In einigen Situationen wird eine Formatzeichenfolge extern kontrolliert. In diesem Fall darf sie jedoch nur aus vertrauenswürdigen Quellen verwendet werden.

#### Nicht konformer Code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP-Anfragen sollten immer Zeitüberschreitungswerte für Sockets und Verbindungen enthalten {#http-requests-should-always-have-socket-and-connect-timeouts}

**Schlüssel**: CQRules:ConnectionTimeoutMechanism

**Typ**: Fehler

**Schweregrad**: Kritisch

**Seit**: Version 2018.6.0

Beim Ausführen von HTTP-Anfragen aus einer AEM-Anwendung muss unbedingt sichergestellt sein, dass korrekte Zeitüberschreitungswerte konfiguriert werden, um unnötige Thread-Nutzung zu vermeiden. Leider sind im Java-Standard-HTTP-Client (java.net.HttpUrlConnection) und dem häufig verwendeten Client für Apache-HTTP-Komponenten standardmäßig keine Zeitüberschreitungen festgelegt, sodass diese explizit festgelegt werden müssen. Als Best Practice gilt, diese Zeitüberschreitungen bei maximal 60 Sekunden zu definieren.

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

### Produkt-APIs, die mit @ProviderType kommentiert wurden, sollten von Kunden nicht implementiert oder erweitert werden {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

**Schlüssel**: CQBP-84, CQBP-84-dependencies

**Typ**: Fehler

**Schweregrad**: Kritisch

**Seit**: Version 2018.7.0

Die AEM-API enthält Java-Schnittstellen und -Klassen, die durch benutzerdefinierten Code lediglich verwendet, aber nicht implementiert werden sollen. Zum Beispiel ist die Schnittstelle *com.day.cq.wcm.api.Page* nur für die Implementierung durch ***AEM*** ausgelegt.

Wenn zu diesen Schnittstellen neue Methoden hinzugefügt werden, wirken sich diese zusätzlichen Methoden nicht auf den vorhandenen Code aus, der diese Schnittstellen verwendet. Daher wird das Hinzufügen neuer Methoden zu diesen Schnittstellen als abwärtskompatibel betrachtet. Wenn jedoch benutzerdefinierter Code eine dieser Schnittstellen ***implementiert***, führt dieser benutzerspezifische Code ein Abwärtskompatibilitätsrisiko für den Kunden ein.

Schnittstellen (und Klassen), die nur von AEM implementiert werden sollen, werden mit *org.osgi.annotation.versioning.ProviderType* (oder in einigen Fällen mit einer veralteten Anmerkung *aQute.bnd.annotation.ProviderType*) kommentiert. Diese Regel identifiziert die Fälle, in denen eine solche Schnittstelle durch benutzerdefinierten Code implementiert wird (oder eine Klasse erweitert wird).

#### Nicht konformer Code {#non-compliant-code-3}

```java
import com.day.cq.wcm.api.Page;

public class DontDoThis implements Page {
// implementation here
}
```

### ResourceResolver-Objekte sollten immer geschlossen werden {#resourceresolver-objects-should-always-be-closed}

**Schlüssel**: CQRules:CQBP-72

**Typ**: Code Smell

**Schweregrad**: Hoch

**Seit**: Version 2018.4.0

ResourceResolver-Objekte, die aus ResourceResolverFactory abgerufen werden, verbrauchen Systemressourcen. Obwohl es Möglichkeiten gibt, mit denen diese Ressourcen gelöscht werden, wenn ein ResourceResolver nicht mehr verwendet wird, ist es effizienter, alle offenen ResourceResolver-Objekte explizit durch Aufruf der close()-Methode zu schließen.

Ein verbreiteter Irrtum besagt, dass ResourceResolver-Objekte, die mit einer bestehenden JCR-Sitzung erstellt wurden, nicht explizit geschlossen werden sollten, da dies sonst die zugrunde liegende JCR-Sitzung schließt. Das ist nicht der Fall: Unabhängig davon, wie ein ResourceResolver geöffnet wurde, sollte er geschlossen werden, wenn er nicht mehr verwendet wird. Da ResourceResolver die Closeable-Schnittstelle implementiert, kann auch die Syntax „try-with-resources“ verwendet werden, anstatt explizit „close()“ aufzurufen.

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

**Schlüssel**: CQRules:CQBP-75

**Typ**: Code Smell

**Schweregrad**: Hoch

**Seit**: Version 2018.4.0

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

### Ausnahmefehler sollten protokolliert oder ausgegeben werden, aber nicht beides {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

**Schlüssel**: CQRules:CQBP-44---CatchAndEitherLogOrThrow

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2018.4.0

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

### Vermeiden Sie Protokollaussagen, die direkt von einer Throw-Anweisung gefolgt werden {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

**Schlüssel**: CQRules:CQBP-44---ConsecutivelyLogAndThrow

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2018.4.0

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

### Vermeiden Sie beim Verarbeiten von GET- oder HEAD-Anfragen die Protokollierung bei INFO {#avoid-logging-at-info-when-handling-get-or-head-requests}

**Schlüssel**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests

**Typ**: Code Smell

**Schweregrad**: Gering

Im Allgemeinen sollten mit der Protokollierungsstufe INFO wichtige Aktionen abgegrenzt werden. Standardmäßig ist AEM so konfiguriert, dass auf der INFO-Ebene oder höher protokolliert wird. GET- und HEAD-Methoden sollten nur schreibgeschützte Vorgänge sein und stellen daher keine wichtigen Aktionen dar. Die Protokollierung auf INFO-Ebene als Antwort auf GET- oder HEAD-Anfragen füllt das Protokoll wahrscheinlich mit erheblichen Mengen überflüssiger Informationen, sodass es schwieriger wird, nützliche Informationen in Protokolldateien zu finden. Bei der Verarbeitung von GET- oder HEAD-Anfragen sollte die Protokollierung entweder bei einem Fehler auf WARN- oder ERROR-Ebene erfolgen oder auf DEBUG- oder TRACE-Ebene, wenn eine tiefgehendere Fehlerbehebung hilfreich wäre.

>[!CAUTION]
>
>Das gilt nicht für die Protokollierung von access.log-type-Ereignissen für jede Anfrage.

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

### Verwenden Sie nicht Exception.getMessage() als ersten Parameter einer Protokollanweisung {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

**Schlüssel**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2018.4.0

Als Best Practice sollten Protokollmeldungen kontextbezogene Informationen darüber enthalten, wo eine Anwendungsausnahme aufgetreten ist. Während der Kontext auch mit Stacktraces bestimmt werden kann, ist die Protokollmeldung meist besser lesbar und verständlicher. Wenn Sie eine Ausnahme protokollieren, ist es daher nicht empfehlenswert, die Ausnahmemeldung als Protokollmeldung zu verwenden. Die Ausnahmemeldung enthält Informationen dazu, was nicht funktioniert hat, während die Protokollmeldung dem Protokollleser mitteilt, was die Anwendung getan hat, als die Ausnahme auftrat. Die Ausnahmemeldung wird weiterhin protokolliert. Wenn Sie Ihre eigene Meldung festlegen, werden die Protokolle verständlicher.

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

**Schlüssel**: CQRules:CQBP-44---WrongLogLevelInCatchBlock

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2018.4.0

Wie der schon Name sagt, sollten Java-Ausnahmen immer in *außergewöhnlichen* Fällen verwendet werden. Wenn eine Ausnahme erfasst wird, muss daher sichergestellt sein, dass Protokollmeldungen auf der entsprechenden Ebene – WARN oder ERROR – protokolliert werden, damit diese Meldungen in den Protokollen korrekt angezeigt werden.

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

**Schlüssel**: CQRules:CQBP-44---ExceptionPrintStackTrace

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2018.4.0

Wie bereits erwähnt, ist Kontext beim Verständnis von Protokollmeldungen äußerst wichtig. Durch Verwendung von Exception.printStackTrace() wird bei der Ausgabe des Standard-Fehlerstroms **nur** der Stacktrace ausgegeben, sodass der gesamte Kontext verloren geht. Bei einer Multi-Thread-Anwendung wie AEM kann es beim parallelen Drucken mehrerer Ausnahmen mit dieser Methode zu einer Überlappung der Stacktraces kommen, was erhebliche Verwirrung verursacht. Ausnahmen sollten daher nur über das Protokollierungs-Framework protokolliert werden.

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

**Schlüssel**: CQRules:CQBP-44—LogLevelConsolePrinters

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2018.4.0

Die Anmeldung in AEM sollte immer über das Protokollierungs-Framework (SLF4J) erfolgen. Durch die direkte Ausgabe an Standardausgabe- oder Standardfehler-Ströme gehen strukturelle und kontextbezogene Informationen verloren, die vom Protokollings-Framework bereitgestellt werden. Außerdem kann diese Vorgehensweise in einigen Fällen zu Leistungseinbußen führen.

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

**Schlüssel**: CQRules:CQBP-71

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2018.4.0

Im Allgemeinen sollten Pfade, die mit /libs und /apps beginnen, nicht hartcodiert werden, da die Pfade, auf die sie verweisen, am häufigsten als Pfade relativ zum Sling-Suchpfad gespeichert werden (standardmäßig /libs bzw. /apps). Durch den absoluten Pfad können geringfügige Fehler entstehen, die erst später im Projektlebenszyklus deutlich werden.

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

**Schlüssel**: CQRules:AMSCORE-554

**Typ**: Code Smell/Cloud Service-Kompatibilität

**Schweregrad**: Gering

**Seit**: Version 2020.5.0

Die Sling-Planung darf nicht für Aufgaben verwendet werden, die eine garantierte Ausführung erfordern. Über Sling geplante Aufträge garantieren die Ausführung und eignen sich besser für Umgebungen mit und ohne Cluster.

Weitere Informationen zum Umgang mit Sling-Aufträgen in einer Umgebung mit Clustern finden Sie unter [Apache Sling Eventing und Job Handling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html).

### Veraltete AEM-APIs sollten nicht verwendet werden {#sonarqube-aem-deprecated}

**Schlüssel**: AMSCORE-553

**Typ**: Code Smell/Cloud Service-Kompatibilität

**Schweregrad**: Gering

**Seit**: Version 2020.5.0

Die AEM-API-Oberfläche wird ständig überarbeitet, um APIs zu identifizieren, von deren Verwendung abgeraten wird und die daher als veraltet gelten.

In vielen Fällen sind diese APIs unter Verwendung der Standard-Java-Annotation *@Deprecated* abgekündigt und als solche durch `squid:CallToDeprecatedMethod` gekennzeichnet.

Es gibt jedoch Fälle, in denen eine API im Kontext von AEM veraltet ist, in anderen Kontexten jedoch nicht. Diese Regel identifiziert diese zweite Klasse.

## OakPAL-Inhaltsregeln {#oakpal-rules}

Unten finden Sie die OakPAL-Prüfungen, die von Cloud Manager ausgeführt werden.

>[!NOTE]
>
>OakPAL ist ein Framework, das von einem AEM-Partner (und Gewinner der Auszeichnung „AEM Rockstar North America“ von 2019) entwickelt wurde und Inhaltspakete mithilfe eines eigenständigen Oak-Repositorys überprüft.

### Kundenpakete sollten keine Knoten unter /libs erstellen oder ändern {#oakpal-customer-package}

**Schlüssel**: BannedPaths

**Typ**: Fehler

**Schweregrad**: Blocker

**Seit**: Version 2019.6.0

Es ist eine lange bestehende Best Practice, dass die /libs-Inhaltsstruktur im AEM-Inhalts-Repository von Kunden als schreibgeschützt betrachtet werden sollte. Das Ändern von Knoten und Eigenschaften unter */libs* verursacht erhebliche Risiken für umfassende und kleinere Aktualisierungen. Änderungen an */libs* sollten nur durch Adobe über offizielle Kanäle vorgenommen werden.

### Pakete dürfen keine doppelten OSGi-Konfigurationen enthalten {#oakpal-package-osgi}

**Schlüssel**: DuplicateOsgiConfigurations

**Typ**: Fehler

**Schweregrad**: Hoch

**Seit**: Version 2019.6.0

Ein häufig auftretendes Problem bei komplexen Projekten besteht darin, dass dieselbe OSGi-Komponente mehrmals konfiguriert ist. Dadurch ist nicht mehr eindeutig, welche Konfiguration gelten soll. Diese Regel ist „Laufzeitmodus-fokussiert“, da sie nur Probleme erkennt, bei denen dieselbe Komponente mehrmals im gleichen Laufzeitmodus (oder mit der gleichen Kombination aus Laufzeitmodi) konfiguriert ist.

#### Nicht konformer Code {#non-compliant-code-osgi}

```
+ apps
  + projectA
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
  + projectB
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

#### Konformer Code {#compliant-code-osgi}

```
+ apps
  + shared-config
    + config
      + com.day.cq.commons.impl.ExternalizerImpl
```

### Konfigurationen und Installationsordner dürfen nur OSGi-Knoten enthalten {#oakpal-config-install}

**Schlüssel**: ConfigAndInstallShouldOnlyContainOsgiNodes

**Typ**: Fehler

**Schweregrad**: Hoch

**Seit**: Version 2019.6.0

Aus Sicherheitsgründen sind Pfade, die */config/ und /install/* enthalten, nur von Administratoranwendern in AEM lesbar und sollten nur für OSGi-Konfigurationen und OSGi-Bundles verwendet werden. Das Platzieren anderer Inhaltstypen in Pfade mit diesen Segmenten führt dazu, dass sich die Anwendung abhängig davon anders verhält, ob sie von Administratoren- oder Nicht-Administratoren verwendet wird.

Ein häufig auftretendes Problem ist die Verwendung von Knoten mit der Bezeichnung `config` in Komponentendialogfeldern oder beim Angeben der Rich-Text-Editor-Konfiguration für die Inline-Bearbeitung. Um dies zu beheben, sollte der fehlerhafte Knoten in einen kompatiblen Namen umbenannt werden. Nutzen Sie bei der Rich-Text-Editor-Konfiguration die Eigenschaft `configPath` im Knoten `cq:inplaceEditing`, um den neuen Speicherort anzugeben.

#### Nicht konformer Code {#non-compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    + config [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

#### Konformer Code {#compliant-code-config-install}

```
+ cq:editConfig [cq:EditConfig]
  + cq:inplaceEditing [cq:InplaceEditConfig]
    ./configPath = inplaceEditingConfig (String)
    + inplaceEditingConfig [nt:unstructured]
      + rtePlugins [nt:unstructured]
```

### Pakete sollten nicht überlappen {#oakpal-no-overlap}

**Schlüssel**: PackageOverlaps

**Typ**: Fehler

**Schweregrad**: Hoch

**Seit**: Version 2019.6.0

Ähnlich wie bei *Pakete dürfen keine doppelten OSGi-Konfigurationen enthalten* ist dies ein häufiges Problem bei komplexen Projekten, bei denen mehrere separate Inhaltspakete in denselben Knotenpfad schreiben. Mit Inhaltspaketabhängigkeiten kann zwar ein konsistentes Ergebnis sichergestellt werden, Überlappungen sollten aber dennoch von vorneherein vermieden werden.

### Der standardmäßige Authoring-Modus sollte nicht die klassische Benutzeroberfläche sein {#oakpal-default-authoring}

**Schlüssel**: ClassicUIAuthoringMode

**Typ**: Code Smell/Cloud Service-Kompatibilität

**Schweregrad**: Gering

**Seit**: Version 2020.5.0

Die OSGi-Konfiguration `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` definiert den standardmäßigen Authoring-Modus in AEM. Da die klassische Benutzeroberfläche seit AEM 6.4 nicht mehr unterstützt wird, tritt jetzt ein Problem auf, wenn als standardmäßiger Authoring-Modus die klassische Benutzeroberfläche konfiguriert ist.

### Komponenten mit Dialogfeldern sollten Dialogfelder für die Touch-Benutzeroberfläche aufweisen {#oakpal-components-dialogs}

**Schlüssel**: ComponentWithOnlyClassicUIDialog

**Typ**: Code Smell/Cloud Service-Kompatibilität

**Schweregrad**: Gering

**Seit**: Version 2020.5.0

AEM-Komponenten mit einem Dialogfeld für die klassische Benutzeroberfläche sollten immer über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen, um ein optimales Authoring-Erlebnis zu erzielen und mit dem Cloud Service-Implementierungsmodell kompatibel zu sein, bei dem die klassische Benutzeroberfläche nicht unterstützt wird. Diese Regel überprüft die folgenden Szenarien:

* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche (d. h. einem untergeordneten Dialogfeldknoten) muss über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über einen untergeordneten `cq:dialog`-Knoten).
* Eine Komponente mit einem Design-Dialogfeld für die klassische Benutzeroberfläche (d. h. einen Knoten „design_dialog“) muss über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über einen untergeordneten `cq:design_dialog`-Knoten).
* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche und einem Design-Dialogfeld für die klassische Benutzeroberfläche muss sowohl über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche als auch über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen.

Die Dokumentation zu den AEM-Modernisierungs-Tools enthält Dokumentation und Tools zum Konvertieren von Komponenten aus der klassischen Benutzeroberfläche in die Touch-Benutzeroberfläche. Weitere Informationen finden Sie unter [The AEM Modernization Tools](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html).

### Pakete sollten keinen veränderlichen und unveränderlichen Inhalt mischen {#oakpal-packages-immutable}

**Schlüssel**: ImmutableMutableMixedPackage

**Typ**: Code Smell/Cloud Service-Kompatibilität

**Schweregrad**: Gering

**Seit**: Version 2020.5.0

Um mit dem Cloud Service-Implementierungsmodell kompatibel zu sein, müssen die einzelnen Inhaltspakete entweder Inhalte für die unveränderlichen Bereiche des Repositorys (`/apps and /libs, although /libs` sollte also nicht durch Kunden-Code geändert werden und einen separaten Verstoß verursachen) oder den veränderlichen Bereich (d. h. alles andere) enthalten, jedoch nicht beides. Beispielsweise ist ein Paket, das beide `/apps/myco/components/text and /etc/clientlibs/myco` enthält, nicht mit Cloud Service kompatibel und führt dazu, dass ein Problem gemeldet wird.

Weitere Informationen finden Sie unter [AEM-Projektstruktur](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html).

### Rückwärtsreplikations-Agenten sollten nicht verwendet werden {#oakpal-reverse-replication}

**Schlüssel**: ReverseReplication

**Typ**: Code Smell/Cloud Service-Kompatibilität

**Schweregrad**: Gering

**Seit**: Version 2020.5.0

Cloud Service-Implementierungen unterstützen keine Rückwärtsreplikation. Weitere Informationen finden Sie unter [Versionshinweisen: Entfernung von Replikations-Agenten](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/release-notes/aem-cloud-changes.html#replication-agents).

Kunden, die die Rückwärtsreplikation verwenden, sollten sich für alternative Lösungen an Adobe wenden.

### OakPAL - In proxyaktivierten Client-Bibliotheken enthaltene Ressourcen sollten sich in einem Ordner mit dem Namen resources befinden. {#oakpal-resources-proxy}

**Schlüssel**: ClientlibProxyResource

**Typ**: Fehler

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

AEM Client-Bibliotheken können statische Ressourcen wie Bilder und Schriftarten enthalten. Wie unter [Verwenden von Präprozessoren](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html?lang=en#using-preprocessors) beschrieben, müssen diese statischen Ressourcen bei der Verwendung von geteilten Client-Bibliotheken in einem untergeordneten Ordner namens &quot;resources&quot;enthalten sein, damit sie effektiv in den Veröffentlichungsinstanzen referenziert werden können.

#### Nicht konformer Code {#non-compliant-proxy-enabled}

```
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + images
        + myimage.jpg
```

#### Konformer Code {#compliant-proxy-enabled}

```
+ apps
  + projectA
    + clientlib
      - allowProxy=true
      + resources
        + myimage.jpg
```

### OakPAL - Verwendung von nicht kompatiblen Workflow-Prozessen des Cloud Service {#oakpal-usage-cloud-service}

**Schlüssel**: CloudServiceInkompatibleWorkflowProcess

**Typ**: Code Smell

**Schweregrad**: Blocker

**Seit**: Version 2021.2.0

Mit der Umstellung auf Asset-Mikrodienste für die Asset-Verarbeitung auf AEM Cloud Service werden verschiedene Workflow-Prozesse, die in lokalen und AMS-Versionen von AEM verwendet wurden, entweder nicht unterstützt oder nicht mehr erforderlich. Das Migrationswerkzeug unter [aem-cloud-migration](https://github.com/adobe/aem-cloud-migration) kann verwendet werden, um Arbeitsablaufmodelle während der Migration AEM Cloud Service zu aktualisieren.

### OakPAL - Verwendung von statischen Vorlagen wird zugunsten bearbeitbarer Vorlagen {#oakpal-static-template}

**Schlüssel**: StaticTemplateUsage

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

Die Verwendung von statischen Vorlagen ist in AEM Projekten schon immer sehr häufig vorkommen, editierbare Vorlagen werden jedoch dringend empfohlen, da sie die größte Flexibilität bieten und zusätzliche Funktionen unterstützen, die in statischen Vorlagen nicht vorhanden sind. Weitere Informationen finden Sie unter [Seitenvorlagen - Bearbeitbar](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-editable.html?lang=en). Die Migration von statischen zu bearbeitbaren Vorlagen kann weitgehend automatisiert werden, indem die [AEM Moderationstools](https://opensource.adobe.com/aem-modernize-tools/) verwendet werden.

### OakPAL - Verwendung älterer Foundation-Komponenten wird nicht empfohlen{#oakpal-usage-legacy}

**Schlüssel**: LegacyFoundationComponentUsage

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

Die alten Grundkomponenten (d.h. Komponenten unter `/libs/foundation`) wurden für mehrere AEM Versionen zugunsten der WCM-Kernkomponenten veraltet. Die Verwendung der alten Basiskomponenten als Grundlage für benutzerdefinierte Komponenten - sei es durch Überlagerung oder Vererbung - wird nicht empfohlen und sollte in die entsprechende Kernkomponente konvertiert werden. Diese Konvertierung kann durch die [AEM Moderationstools](https://opensource.adobe.com/aem-modernize-tools/) erleichtert werden.

### OakPAL - Nur unterstützte Runmode-Namen und -Reihenfolge sollten verwendet werden {#oakpal-supported-runmodes}

**Schlüssel**: SupportedRunmode

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

AEM Cloud Service erzwingt eine strikte Benennungsrichtlinie für die Namen des Ausführungsmodus und eine strikte Reihenfolge für diese Ausführungsmodi. Die Liste der unterstützten Ausführungsmodi kann unter [Runmodi](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=de#runmodes) gefunden werden und jede Abweichung davon wird als Problem identifiziert.

### OakPAL - Custom Search Index Definition Nodes must be Direct Children of /oak:index {#oakpal-custom-search}

**Schlüssel**: OakIndexLocation

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs oak:QueryIndexDefinition) direkt untergeordnete Knoten von `/oak:index` sind. Indizes an anderen Orten müssen verschoben werden, um mit AEM Cloud Service kompatibel zu sein. Weitere Informationen zu Suchindizes finden Sie unter [Inhaltssuche und Indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=de).

### OakPAL - Custom Search Index Definition Nodes Muss eine compatVersion von 2 {#oakpal-custom-search-compatVersion} haben

**Schlüssel**: IndexCompatVersion

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass die Eigenschaft compatVersion für benutzerdefinierte Suchindexdefinitionen (d. h. Knoten des Typs oak:QueryIndexDefinition) auf 2 gesetzt werden muss. Andere Werte werden von AEM Cloud Service nicht unterstützt. Weitere Informationen zu Suchindizes finden Sie unter [Inhaltssuche und Indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en).

### OakPAL - Absteigende Knoten von benutzerdefinierten Suchindex-Definitionsknoten müssen vom Typ nt:unstructured {#oakpal-descendent-nodes} sein

**Schlüssel**: IndexDescendantNodeType

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

Probleme können schwer zu beheben sein, wenn ein Knoten mit einer benutzerdefinierten Suchindexdefinition ungeordnete untergeordnete Knoten enthält. Um dies zu vermeiden, wird empfohlen, dass alle untergeordneten Knoten eines `oak:QueryIndexDefinition`-Knotens vom Typ nt:unstructured sein sollten.

### OakPAL - Custom Search Index Definition Nodes muss einen untergeordneten Knoten mit dem Namen indexRules enthalten, der untergeordnete Knoten enthält.{#oakpal-custom-search-index}

**Schlüssel**: IndexRulesNode

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

Ein ordnungsgemäß definierter Knoten zur Definition des benutzerdefinierten Suchindex muss einen untergeordneten Knoten mit dem Namen indexRules enthalten, der wiederum mindestens ein untergeordnetes Element aufweisen muss. Weitere Informationen finden Sie unter [Oak Documentation](https://jackrabbit.apache.org/oak/docs/query/lucene.html).

### OakPAL - Custom Search Index Definition Nodes muss Benennungskonventionen folgen {#oakpal-custom-search-definitions}

**Schlüssel**: IndexName

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) nach einem bestimmten Muster benannt werden, das unter [Inhaltssuche und Indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use) beschrieben wird.

### OakPAL - Custom Search Index Definition Nodes muss den Index Type lucene {#oakpal-index-type-lucene} verwenden

**Schlüssel**: IndexType

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindexdefinitionen (d. h. Knoten des Typs oak:QueryIndexDefinition) eine Typeigenschaft mit dem Wert **lucene** aufweisen. Die Indizierung mit älteren Indextypen muss vor der Migration auf AEM Cloud Service aktualisiert werden. Weitere Informationen finden Sie unter [Inhaltssuche und Indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use).

### OakPAL - Custom Search Index Definition Nodes darf keine Eigenschaft namens seed {#oakpal-property-name-seed} enthalten

**Schlüssel**: IndexSeedProperty

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

AEM Cloud Service verbietet, dass benutzerdefinierte Suchindexdefinitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) eine Eigenschaft mit dem Namen Seed enthalten. Die Indizierung mit dieser Eigenschaft muss vor der Migration auf AEM Cloud Service aktualisiert werden. Weitere Informationen finden Sie unter [Inhaltssuche und Indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use).

### OakPAL - Custom Search Index Definition Nodes darf keine Eigenschaft namens reindex enthalten.{#oakpal-reindex-property}

**Schlüssel**: IndexReindexProperty

**Typ**: Code Smell

**Schweregrad**: Gering

**Seit**: Version 2021.2.0

AEM Cloud Service verbietet, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) eine Eigenschaft namens reindex enthalten. Die Indizierung mit dieser Eigenschaft muss vor der Migration auf AEM Cloud Service aktualisiert werden. Weitere Informationen finden Sie unter [Inhaltssuche und Indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/indexing.html?lang=en#how-to-use).

## Dispatcher-Optimierungstool {#dispatcher-optimization-tool-rules}

Im folgenden Abschnitt werden die von Cloud Manager durchgeführten DOT-Prüfungen hervorgehoben:

* [DOT - Parsing Violation - Dispatcher-Konfiguration Unerwartete Tokens](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [DOT - Parsing Violation - Dispatcher-Konfiguration nicht übereinstimmendes Angebot](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [DOT - Parsing Violation - Dispatcher Configuration Missing Brace](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [DOT - Parsing Violation - Dispatcher-Konfiguration Extra Brace](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [DOT - Parsing Violation - Dispatcher-Konfiguration Fehlende obligatorische Eigenschaft](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [DOT - Parsing Violation - Dispatcher-Konfiguration - veraltete Eigenschaft](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [DOT - Parsing Violation - Dispatcher-Konfiguration nicht gefunden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [DOT - Parsing Violation - HTTP Configuration Include-Datei nicht gefunden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [DOT - Parsing Violation - Dispatcher-Konfiguration Allgemein](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [DOT - Der Cache der Dispatcher-Veröffentlichungsfarm sollte serveStaleOnError aktiviert haben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [DOT - Die Filter der Dispatcher-Veröffentlichungsfarm sollten die standardmäßigen Ablehnungsregeln aus der 6.x.x-Version des AEM-Archetyps enthalten](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [DOT - Die Eigenschaft des Dispatcher-Cache im Veröffentlichungsmodus muss >= 2 sein.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [DOT - Die Dispatcher publish farm gracePeriod-Eigenschaft sollte >= 2 sein.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [DOT - Jede Dispatcher-Farm sollte einen eindeutigen Namen haben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [DOT - Der Dispatcher Veröffentlichungsfarm-Cache sollte seine ignoreUrlParams-Regeln auf eine Zulassungsliste konfigurieren](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [DOT - Die Filter der Dispatcher-Veröffentlichungsfarm sollten die zulässigen Sling-Selektoren in Zulassungsliste spezifizieren.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [DOT - Die Filter der Dispatcher-Veröffentlichungsfarm sollten die zulässigen Sling-Suffix-Muster in einer Zulassungsliste angeben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [DOT - Die Direktive &#39;Alles erforderlich&#39; sollte nicht in einem VirtualHost Directory-Abschnitt mit einem Stammverzeichnis-Pfad verwendet werden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
