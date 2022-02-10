---
title: Benutzerspezifische Regeln für Code-Qualität
description: Auf dieser Seite werden die benutzerspezifischen Code-Qualitätsregeln beschrieben, die von Cloud Manager im Rahmen von Code-Qualitätstests ausgeführt werden. Sie basieren auf Best Practices von AEM Engineering.
uuid: a7feb465-1982-46be-9e57-e67b59849579
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: d2338c74-3278-49e6-a186-6ef62362509f
feature: Code Quality Rules
exl-id: 7d118225-5826-434e-8869-01ee186e0754
source-git-commit: 834508109e34eb1e052abac482e981735c72d43d
workflow-type: tm+mt
source-wordcount: '3611'
ht-degree: 48%

---


# Benutzerspezifische Regeln für Code-Qualität {#custom-code-quality-rules}

Auf dieser Seite werden die benutzerspezifischen Code-Qualitätsregeln beschrieben, die von Cloud Manager im Rahmen von [Codequalitätstests.](understand-your-test-results.md) Sie basieren auf Best Practices von AEM Engineering.

>[!NOTE]
>
>as a Cloud Service Informationen zu benutzerspezifischen Regeln für die Code-Qualität von Cloud Manager finden Sie unter AEM [zu dieser Dokumentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/custom-code-quality-rules.html#using-cloud-manager).

>[!NOTE]
>
>Die hier bereitgestellten Codebeispiele dienen nur zu Veranschaulichungszwecken. Siehe [Dokumentation zu SonarQube-Konzepten](https://docs.sonarqube.org/7.4/user-guide/concepts/) , um mehr über die Konzepte und Qualitätsregeln zu erfahren.

## SonarQube-Regeln {#sonarqube-rules}

Im folgenden Abschnitt werden die von Cloud Manager ausgeführten SonarQube-Regeln beschrieben.

### Verwenden Sie keine potenziell gefährlichen Funktionen {#do-not-use-potentially-dangerous-functions}

* **Schlüssel**: CQRules:CWE-676
* **Typ**: Sicherheitslücke
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Die Methoden `Thread.stop()` und `Thread.interrupt()` kann schwer reproduzierbare Probleme und in einigen Fällen Sicherheitslücken verursachen. Daher sollte deren Verwendung sorgfältig überwacht und validiert werden. Im Allgemeinen ist die Nachrichtenübergabe eine sicherere Möglichkeit, ähnliche Ziele zu erreichen.

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

### Verwenden Sie keine Formatzeichenfolgen, die möglicherweise extern kontrolliert werden {#do-not-use-format-strings-which-may-be-externally-controlled}

* **Schlüssel**: CQRules:CWE-134
* **Typ**: Sicherheitslücke
* **Schweregrad**: Hoch
* **Seit**: Version 2018.4.0

Die Verwendung einer Formatzeichenfolge aus einer externen Quelle (z. B. einem Anforderungsparameter oder benutzergenerierten Inhalten) kann eine Anwendung für Denial-of-Service-Angriffe verfügbar machen. In einigen Situationen wird eine Formatzeichenfolge extern kontrolliert. In diesem Fall darf sie jedoch nur aus vertrauenswürdigen Quellen verwendet werden.

#### Nicht konformer Code {#non-compliant-code-1}

```java
protected void doPost(SlingHttpServletRequest request, SlingHttpServletResponse response) {
  String messageFormat = request.getParameter("messageFormat");
  request.getResource().getValueMap().put("some property", String.format(messageFormat, "some text"));
  response.sendStatus(HttpServletResponse.SC_OK);
}
```

### HTTP-Anforderungen sollten immer Socket- und Verbindungs-Timeouts aufweisen {#http-requests-should-always-have-socket-and-connect-timeouts}

* **Schlüssel**: CQRules:ConnectionTimeoutMechanism
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.6.0

Beim Ausführen von HTTP-Anfragen aus einem AEM-Programm muss unbedingt sichergestellt sein, dass korrekte Zeitüberschreitungswerte konfiguriert werden, um unnötige Thread-Nutzung zu vermeiden. Leider ist das Standardverhalten des standardmäßigen HTTP-Clients von Java `java.net.HttpUrlConnection`, und der häufig verwendete Apache HTTP Components-Client darf nie zu einem Timeout führen. Daher müssen Timeouts explizit festgelegt werden. Als Best Practice sollten diese Timeouts maximal 60 Sekunden betragen.

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

`ResourceResolver` Objekte, die von der `ResourceResolverFactory` Systemressourcen verbrauchen. Obwohl es Maßnahmen gibt, um diese Ressourcen zurückzufordern, wenn ein `ResourceResolver` nicht mehr verwendet wird, ist es effizienter, alle geöffneten `ResourceResolver` -Objekte durch Aufruf der `close()` -Methode.

Ein relativ häufiges Missverständnis ist, dass `ResourceResolver` -Objekte, die mit einer vorhandenen JCR-Sitzung erstellt wurden, sollten nicht explizit geschlossen werden. Andernfalls wird die zugrunde liegende JCR-Sitzung geschlossen. Das ist nicht der Fall. Unabhängig davon, wie eine `ResourceResolver` geöffnet ist, sollte sie geschlossen werden, wenn sie nicht mehr verwendet wird. Seit `ResourceResolver` implementiert die `Closeable` -Schnittstelle, ist es auch möglich, die `try-with-resources` -Syntax anstatt explizit aufzurufen `close()`.

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

### Verwenden Sie keine Sling Servlet-Pfade, um Servlets zu registrieren {#do-not-use-sling-servlet-paths-to-register-servlets}

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

### Ausnahmefehler sollten entweder protokolliert oder ausgegeben werden, nicht beide {#caught-exceptions-should-be-logged-or-thrown-but-not-both}

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

### Vermeiden Sie Protokollanweisungen, die unmittelbar von Throw-Anweisungen gefolgt werden {#avoid-having-a-log-statement-immediately-followed-by-a-throw-statement}

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

### Vermeiden Sie die Protokollierung bei INFO bei der Verarbeitung von GET- oder HEAD-Anfragen {#avoid-logging-at-info-when-handling-get-or-head-requests}

* **Schlüssel**: CQRules:CQBP-44---LogInfoInGetOrHeadRequests
* **Typ**: Code Smell
* **Schweregrad**: Gering

Im Allgemeinen sollten mit der Protokollierungsstufe INFO wichtige Aktionen abgegrenzt werden. Standardmäßig ist AEM so konfiguriert, dass auf der INFO-Ebene oder höher protokolliert wird. GET- und HEAD-Methoden sollten nur schreibgeschützte Vorgänge sein und stellen daher keine wichtigen Aktionen dar. Die Protokollierung auf INFO-Ebene als Antwort auf GET- oder HEAD-Anfragen füllt das Protokoll wahrscheinlich mit erheblichen Mengen überflüssiger Informationen, sodass es schwieriger wird, nützliche Informationen in Protokolldateien zu finden. Bei der Verarbeitung von GET- oder HEAD-Anfragen sollte die Protokollierung entweder bei einem Fehler auf WARN- oder ERROR-Ebene erfolgen oder auf DEBUG- oder TRACE-Ebene, wenn eine tiefgehendere Fehlerbehebung hilfreich wäre.

>[!NOTE]
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

### Verwenden Sie nicht Exception.getMessage() als ersten Parameter einer Protokollierungsanweisung {#do-not-use-exception-getmessage-as-the-first-parameter-of-a-logging-statement}

* **Schlüssel**: CQRules:CQBP-44---ExceptionGetMessageIsFirstLogParam
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Als Best Practice sollten Protokollmeldungen kontextbezogene Informationen darüber enthalten, wo eine Programmausnahme aufgetreten ist. Während der Kontext auch mit Stacktraces bestimmt werden kann, ist die Protokollmeldung meist besser lesbar und verständlicher. Daher ist es bei der Protokollierung einer Ausnahme nicht empfehlenswert, die Ausnahmemeldung als Protokollmeldung zu verwenden. Die Ausnahmemeldung enthält Informationen zu Fehlern, während die Protokollmeldung verwendet werden sollte, um einem Protokollleser mitzuteilen, was die Anwendung gerade tat, als die Ausnahme auftrat. Die Ausnahmemeldung wird weiterhin protokolliert. Durch die Angabe Ihrer eigenen Nachricht werden die Protokolle einfach verständlicher.

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

Wie der schon Name sagt, sollten Java-Ausnahmen immer in außergewöhnlichen Fällen verwendet werden. Wenn eine Ausnahme erfasst wird, muss daher sichergestellt werden, dass Protokollmeldungen auf der entsprechenden Ebene protokolliert werden: WARN oder FEHLER. damit diese Meldungen in den Protokollen korrekt angezeigt werden.

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

### Drucken Sie keine Stack-Traces in der Konsole {#do-not-print-stack-traces-to-the-console}

* **Schlüssel**: CQRules:CQBP-44---ExceptionPrintStackTrace
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Beim Verständnis von Protokollmeldungen ist der Kontext von entscheidender Bedeutung. Verwenden `Exception.printStackTrace()` führt dazu, dass nur die Stacktrace an den Standard-Fehlerstream ausgegeben wird, wodurch der gesamte Kontext verloren geht. Bei einem Multi-Thread-Programm wie AEM kann es beim parallelen Drucken mehrerer Ausnahmen mit dieser Methode zu einer Überlappung der Stacktraces kommen, was erhebliche Verwirrung verursacht. Ausnahmen sollten daher nur über das Protokollierungs-Framework protokolliert werden.

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

### Ausgabe nicht in Standardausgabe oder Standardfehler {#do-not-output-to-standard-output-or-standard-error}

* **Schlüssel**: CQRules:CQBP-44—LogLevelConsolePrinters
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2018.4.0

Die Anmeldung AEM sollte immer über das Protokollierungs-Framework, SLF4J, erfolgen. Durch die direkte Ausgabe an Standardausgabe- oder Standardfehler-Ströme gehen strukturelle und kontextbezogene Informationen verloren, die vom Protokollings-Framework bereitgestellt werden. Außerdem kann diese Vorgehensweise in einigen Fällen zu Leistungseinbußen führen.

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

Im Allgemeinen beginnen Pfade mit `/libs` und `/apps` sollte nicht fest codiert werden, da die Pfade, auf die sie verweisen, am häufigsten als Pfade relativ zum Sling-Suchpfad gespeichert werden (der auf `/libs,/apps` Standard). Durch den absoluten Pfad können geringfügige Fehler entstehen, die erst später im Projektlebenszyklus deutlich werden.

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

Siehe [Dokumentation zu Apache Sling Eventing und Job Handling](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html) , um mehr darüber zu erfahren, wie Sling-Aufträge in einer Clusterumgebung verarbeitet werden.

### Veraltete AEM-APIs sollten nicht verwendet werden {#sonarqube-aem-deprecated}

* **Schlüssel**: AMSCORE-553
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die AEM-API-Oberfläche wird ständig überarbeitet, um APIs zu identifizieren, von deren Verwendung abgeraten wird und die daher als veraltet gelten.

In vielen Fällen sind diese APIs unter Verwendung der Standard-Java-Annotation *@Deprecated* abgekündigt und als solche durch `squid:CallToDeprecatedMethod` gekennzeichnet.

Es gibt jedoch Fälle, in denen eine API im Kontext von AEM veraltet ist, in anderen Kontexten jedoch nicht. Diese Regel identifiziert diese zweite Klasse.

## OakPAL-Inhaltsregeln {#oakpal-rules}

Im folgenden Abschnitt werden die von Cloud Manager ausgeführten OakPAL-Prüfungen beschrieben.

>[!NOTE]
>
>OakPAL ist ein Framework, das Inhaltspakete mithilfe eines eigenständigen Oak-Repositorys validiert. Es wurde von einem AEM Partner und Gewinner des AEM Rockstar North America Awards 2019 entwickelt.

### Produkt-APIs, die mit @ProviderType kommentiert sind, sollten von Kunden nicht implementiert oder erweitert werden {#product-apis-annotated-with-providertype-should-not-be-implemented-or-extended-by-customers}

* **Schlüssel**: CQBP-84
* **Typ**: Fehler
* **Schweregrad**: Kritisch
* **Seit**: Version 2018.7.0

Die AEM-API enthält Java-Schnittstellen und -Klassen, die durch benutzerdefinierten Code lediglich verwendet, aber nicht implementiert werden sollen. Zum Beispiel ist die Schnittstelle `com.day.cq.wcm.api.Page` nur für die Implementierung durch AEM ausgelegt.

Wenn zu diesen Schnittstellen neue Methoden hinzugefügt werden, wirken sich diese zusätzlichen Methoden nicht auf den vorhandenen Code aus, der diese Schnittstellen verwendet. Daher wird das Hinzufügen neuer Methoden zu diesen Schnittstellen als abwärtskompatibel betrachtet. Wenn jedoch benutzerdefinierter Code eine dieser Schnittstellen implementiert, führt dieser benutzerspezifische Code ein Abwärtskompatibilitätsrisiko für den Kunden ein.

Schnittstellen und Klassen, die nur von AEM implementiert werden sollen, werden mit kommentiert. `org.osgi.annotation.versioning.ProviderType` oder in einigen Fällen eine ähnliche Legacy-Anmerkung `aQute.bnd.annotation.ProviderType`. Diese Regel identifiziert die Fälle, in denen eine solche Schnittstelle implementiert oder eine Klasse durch benutzerdefinierten Code erweitert wird.

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

Es ist seit langem eine bewährte Methode, dass die `/libs` Die Inhaltsstruktur im AEM Content Repository sollte von Kunden als schreibgeschützt betrachtet werden. Ändern von Knoten und Eigenschaften unter `/libs` verursacht ein erhebliches Risiko für größere und kleinere Aktualisierungen. Änderungen an `/libs` sollten nur durch Adobe über offizielle Kanäle erfolgen.

### Pakete dürfen keine doppelten OSGi-Konfigurationen enthalten {#oakpal-package-osgi}

* **Schlüssel**: DuplicateOsgiConfigurations
* **Typ**: Fehler
* **Schweregrad**: Hoch
* **Seit**: Version 2019.6.0

Ein häufig auftretendes Problem bei komplexen Projekten besteht darin, dass dieselbe OSGi-Komponente mehrmals konfiguriert ist. Dadurch ist nicht mehr eindeutig, welche Konfiguration gelten soll. Diese Regel ist &quot;runmode-basiert&quot;, da sie nur Probleme erkennt, bei denen dieselbe Komponente mehrmals im selben Ausführungsmodus oder in einer Kombination von Ausführungsmodi konfiguriert ist.

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

Aus Sicherheitsgründen enthalten Pfade, die `/config/` und `/install/` sind nur von Administratoren in AEM lesbar und sollten nur für OSGi-Konfigurationen und OSGi-Bundles verwendet werden. Das Platzieren anderer Inhaltstypen in Pfade mit diesen Segmenten führt dazu, dass sich das Programm abhängig davon anders verhält, ob sie von Administratoren- oder Nicht-Administratoren verwendet wird.

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

Ähnlich wie bei [Pakete sollten keine doppelte OSGi-Konfigurationsregel enthalten.](#oakpal-package-osgi)  Dies ist ein häufiges Problem bei komplexen Projekten, bei denen der gleiche Knotenpfad von mehreren separaten Inhaltspaketen in geschrieben wird. Mit Inhaltspaketabhängigkeiten kann zwar ein konsistentes Ergebnis sichergestellt werden, Überlappungen sollten aber dennoch von vorneherein vermieden werden.

### Der standardmäßige Authoring-Modus sollte nicht die klassische Benutzeroberfläche sein {#oakpal-default-authoring}

* **Schlüssel**: ClassicUIAuthoringMode
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Die OSGi-Konfiguration `com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl` definiert den standardmäßigen Authoring-Modus in AEM. weil [Die klassische Benutzeroberfläche wird seit AEM 6.4 nicht mehr unterstützt.](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/deprecated-removed-features.html) Es tritt jetzt ein Problem auf, wenn der standardmäßige Authoring-Modus für die klassische Benutzeroberfläche konfiguriert ist.

### Komponenten mit Dialogfeldern sollten Dialogfelder für die Touch-Benutzeroberfläche aufweisen {#oakpal-components-dialogs}

* **Schlüssel**: ComponentWithOnlyClassicUIDialog
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

AEM-Komponenten mit einem Dialogfeld für die klassische Benutzeroberfläche sollten immer über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen, um ein optimales Authoring-Erlebnis zu erzielen und mit dem Cloud Service-Implementierungsmodell kompatibel zu sein, bei dem die klassische Benutzeroberfläche nicht unterstützt wird. Diese Regel überprüft die folgenden Szenarien:

* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche (d. h. eine `dialog` untergeordneter Knoten) muss über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über eine `cq:dialog` untergeordneten Knoten).
* Eine Komponente mit einem Design-Dialogfeld für die klassische Benutzeroberfläche (d. h. eine `design_dialog` -Knoten) muss über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen (d. h. über eine `cq:design_dialog` untergeordneten Knoten).
* Eine Komponente mit einem Dialogfeld für die klassische Benutzeroberfläche und einem Design-Dialogfeld für die klassische Benutzeroberfläche muss sowohl über ein entsprechendes Dialogfeld für die Touch-Benutzeroberfläche als auch über ein entsprechendes Design-Dialogfeld für die Touch-Benutzeroberfläche verfügen.

Die Dokumentation zu den AEM-Modernisierungs-Tools enthält Details und Tools zum Konvertieren von Komponenten aus der klassischen Benutzeroberfläche in die Touch-Benutzeroberfläche. Siehe [Die Dokumentation AEM Modernisierungs-Tools ](https://opensource.adobe.com/aem-modernize-tools/pages/tools.html) für weitere Details.

### Pakete sollten keinen veränderlichen und unveränderlichen Inhalt mischen {#oakpal-packages-immutable}

* **Schlüssel**: ImmutableMutableMixedPackage
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

Um mit dem Cloud Service-Bereitstellungsmodell kompatibel zu sein, müssen einzelne Inhaltspakete entweder Inhalte für die unveränderlichen Bereiche des Repositorys enthalten (d. h. `/apps` und `/libs`) oder den veränderlichen Bereich (d. h. alles, was nicht in `/apps` oder `/libs`), aber nicht beides. Beispielsweise ist ein Paket, das beide `/apps/myco/components/text and /etc/clientlibs/myco` enthält, nicht mit Cloud Service kompatibel und führt dazu, dass ein Problem gemeldet wird.

Siehe [AEM Dokumentation zur Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html) für weitere Details.

>[!NOTE]
>
>Die Regel [Kundenpakete sollten keine Knoten unter /libs erstellen oder ändern](#oakpal-customer-package) gilt immer.

### Rückwärtsreplikations-Agenten sollten nicht verwendet werden {#oakpal-reverse-replication}

* **Schlüssel**: ReverseReplication
* **Typ**: Code Smell/Cloud Service-Kompatibilität
* **Schweregrad**: Gering
* **Seit**: Version 2020.5.0

In Cloud Service-Implementierungen ist keine Unterstützung für die Rückwärtsreplikation verfügbar, wie unter [Versionshinweise: Entfernung von Replikationsagenten.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/aem-cloud-changes.html#replication-agents)

Kunden, die die Rückwärtsreplikation verwenden, sollten sich für alternative Lösungen an Adobe wenden.

### Ressourcen, die in Proxy-aktivierten Client-Bibliotheken enthalten sind, sollten sich in einem Ordner befinden, der Ressourcen heißt {#oakpal-resources-proxy}

* **Schlüssel**: ClientlibProxyResource
* **Typ**: Fehler
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Client-Bibliotheken können statische Ressourcen wie Bilder und Schriftarten enthalten. Wie im Abschnitt [Verwendung der Dokumentation zu Client-seitigen Bibliotheken,](https://experienceleague.adobe.com/docs/experience-manager-65/developing/introduction/clientlibs.html#using-preprocessors) Bei Verwendung von Proxyclient-Bibliotheken müssen diese statischen Ressourcen in einem untergeordneten Ordner mit dem Namen `resources` um effektiv auf die Veröffentlichungsinstanzen verwiesen zu werden.

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

### Verwendung inkompatibler Workflow-Prozesse in Cloud Service {#oakpal-usage-cloud-service}

* **Schlüssel**: CloudServiceIncompatibleWorkflowProcess
* **Typ**: Code Smell
* **Schweregrad**: Blocker
* **Seit**: Version 2021.2.0

Mit der Umstellung auf Asset-Microservices für die Asset-Verarbeitung auf AEM Cloud Service werden verschiedene Workflow-Prozesse, die in lokalen und AMS-Versionen von AEM verwendet wurden, entweder nicht länger unterstützt oder sind nicht mehr erforderlich.

Das Migrationstool im [as a Cloud Service GitHub-Repository für AEM Assets](https://github.com/adobe/aem-cloud-migration) kann verwendet werden, um Workflow-Modelle während der Migration auf AEM as a Cloud Service zu aktualisieren.

### Die Verwendung statischer Vorlagen wird zugunsten bearbeitbarer Vorlagen empfohlen. {#oakpal-static-template}

* **Schlüssel**: StaticTemplateUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die Verwendung von statischen Vorlagen war in AEM-Projekten stets weit verbreitet. Editierbare Vorlagen werden jedoch dringend empfohlen, da sie die größte Flexibilität bieten und zusätzliche Funktionen unterstützen, die in statischen Vorlagen nicht vorhanden sind. Weitere Informationen finden Sie im [Seitenvorlagen - bearbeitbare Dokumentation.](https://experienceleague.adobe.com/docs/experience-manager-65/developing/platform/templates/page-templates-editable.html)

Die Migration von statischen zu bearbeitbaren Vorlagen kann mithilfe der [AEM Modernisierungs-Tools.](https://opensource.adobe.com/aem-modernize-tools/)

### Die Verwendung älterer Foundation-Komponenten wird nicht empfohlen {#oakpal-usage-legacy}

* **Schlüssel**: LegacyFoundationComponentUsage
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Die veralteten Foundation-Komponenten (d. h. Komponenten unter `/libs/foundation`) wurden für mehrere AEM Versionen zugunsten der [Kernkomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) Die Verwendung der veralteten Foundation-Komponenten als Grundlage für benutzerdefinierte Komponenten, sei es durch Überlagerung oder Vererbung, wird empfohlen und sollte in die entsprechende Kernkomponente konvertiert werden.

Diese Konvertierung kann durch die [AEM Modernisierungs-Tools.](https://opensource.adobe.com/aem-modernize-tools/)

### Nur unterstützte Runmode-Namen und -Reihenfolge sollten verwendet werden {#oakpal-supported-runmodes}

* **Schlüssel**: SupportedRunmode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erzwingt eine strikte Benennungsrichtlinie für Runmode-Namen und eine strikte Reihenfolge für diese Laufzeitmodi. Die Liste der unterstützten Ausführungsmodi finden Sie im Abschnitt [Bereitstellen in AEM as a Cloud Service Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html#runmodes) und jede Abweichung davon wird als Problem identifiziert.

### Benutzerdefinierte Suchindex-Definitionsknoten müssen direkte untergeordnete Elemente von /oak:index sein. {#oakpal-custom-search}

* **Schlüssel**: OakIndexLocation
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) direkt untergeordnete Knoten von `/oak:index`. Indizes an anderen Orten müssen verschoben werden, um mit AEM Cloud Service kompatibel zu sein. Weitere Informationen zu Suchindizes finden Sie im [Dokumentation zur Inhaltssuche und -indizierung.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)

### Benutzerdefinierte Suchindex-Definitionsknoten müssen eine compatVersion von 2 haben. {#oakpal-custom-search-compatVersion}

* **Schlüssel**: IndexCompatVersion
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) muss die Variable `compatVersion` Eigenschaft auf `2`. Andere Werte werden von AEM Cloud Service nicht unterstützt. Weitere Informationen zu Suchindizes finden Sie im [Dokumentation zur Inhaltssuche und -indizierung.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html)

### Abhängige Knoten von benutzerdefinierten Suchindex-Definitionsknoten müssen vom Typ nt:unstructured sein. {#oakpal-descendent-nodes}

* **Schlüssel**: IndexDescendantNodeType
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Probleme können schwer zu beheben sein, wenn ein benutzerdefinierter Suchindex-Definitionsknoten ungeordnete untergeordnete Knoten aufweist. Um dies zu vermeiden, wird empfohlen, dass alle untergeordneten Knoten eines `oak:QueryIndexDefinition` node be of type `nt:unstructured`.

### Benutzerdefinierte Suchindex-Definitionsknoten müssen einen untergeordneten Knoten namens indexRules enthalten, der untergeordnete Elemente enthält {#oakpal-custom-search-index}

* **Schlüssel**: IndexRulesNode
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

Ein ordnungsgemäß definierter benutzerdefinierter Suchindex-Definitionsknoten muss einen untergeordneten Knoten mit dem Namen `indexRules` die wiederum mindestens ein Kind haben müssen. Weitere Informationen finden Sie im [Oak-Dokumentation.](https://jackrabbit.apache.org/oak/docs/query/lucene.html)

### Benutzerdefinierte Suchindex-Definitionsknoten müssen Namenskonventionen folgen {#oakpal-custom-search-definitions}

* **Schlüssel**: IndexName
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) muss nach einem bestimmten Muster benannt werden, das unter [Inhaltssuche und -indizierung.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use)

### Benutzerdefinierte Suchindex-Definitionsknoten müssen den Index-Typ-Lucene verwenden  {#oakpal-index-type-lucene}

* **Schlüssel**: IndexType
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service erfordert, dass benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`) haben eine `type` -Eigenschaft mit dem Wert `lucene`. Die Indizierung mit älteren Indextypen muss vor der Migration auf AEM Cloud Service aktualisiert werden. Siehe [Dokumentation zur Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) für weitere Informationen.

### Benutzerdefinierte Suchindex-Definitionsknoten dürfen keine Eigenschaft mit dem Namen Seed enthalten {#oakpal-property-name-seed}

* **Schlüssel**: IndexSeedProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service verbietet benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`), die eine Eigenschaft namens `seed`. Die Indizierung mit dieser Eigenschaft muss vor der Migration auf AEM Cloud Service aktualisiert werden. Siehe [Dokumentation zur Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) für weitere Informationen.

### Benutzerdefinierte Suchindex-Definitionsknoten dürfen keine Eigenschaft namens reindex enthalten. {#oakpal-reindex-property}

* **Schlüssel**: IndexReindexProperty
* **Typ**: Code Smell
* **Schweregrad**: Gering
* **Seit**: Version 2021.2.0

AEM Cloud Service verbietet benutzerdefinierte Suchindex-Definitionen (d. h. Knoten des Typs `oak:QueryIndexDefinition`), die eine Eigenschaft namens `reindex`. Die Indizierung mit dieser Eigenschaft muss vor der Migration auf AEM Cloud Service aktualisiert werden. Siehe [Dokumentation zur Inhaltssuche und -indizierung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/operations/indexing.html#how-to-use) für weitere Informationen.

## Dispatcher-Optimierungs-Tool {#dispatcher-optimization-tool-rules}

Im folgenden Abschnitt werden die von Cloud Manager ausgeführten DOT-Prüfungen (Dispatcher Optimization Tool) aufgeführt. Befolgen Sie die Links für jede Prüfung auf GitHub-Definition und Details.

* [Unerwartete Token für Dispatcher-Konfiguration](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unexpected-tokens)

* [Dispatcher-Konfiguration - nicht übereinstimmendes Angebot](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-unmatched-quote)

* [Dispatcher-Konfiguration - fehlende Klammer](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-brace)

* [Dispatcher-Konfiguration - extra Brace](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-extra-brace)

* [Dispatcher-Konfiguration Fehlt erforderliche Eigenschaft](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-missing-mandatory-property)

* [Veraltete Eigenschaft der Dispatcher-Konfiguration](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-deprecated-property)

* [Dispatcher-Konfiguration nicht gefunden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-not-found)

* [HTTP-Konfiguration Einschlussdatei nicht gefunden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---httpd-configuration-include-file-not-found)

* [Dispatcher-Konfiguration - Allgemein](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---parsing-violation---dispatcher-configuration-general)

* [Für den Cache der Veröffentlichungsfarm des Dispatchers sollte serveStaleOnError aktiviert sein.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-servestaleonerror-enabled)

* [Die Filter für die Veröffentlichungsfarm des Dispatchers sollten die standardmäßigen Ablehnungsregeln aus der 6.x.x-Version des AEM-Archetyps enthalten.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-contain-the-default-deny-rules-from-the-6xx-version-of-the-aem-archetype)

* [Die Cache-Eigenschaft des Dispatcher-Veröffentlichungsfarm-Cache statfileslevel sollte >= 2 sein.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-statfileslevel-property-should-be--2)

* [Die Eigenschaft gracePeriod der Dispatcher-Veröffentlichungsfarm sollte >= 2 sein.](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-graceperiod-property-should-be--2)

* [Jede Dispatcher-Farm sollte einen eindeutigen Namen haben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---each-dispatcher-farm-should-have-a-unique-name)

* [Die ignoreUrlParams-Regeln des Dispatcher-Veröffentlichungsfarm-Caches sollten auf Zulassungsliste konfiguriert werden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-cache-should-have-its-ignoreurlparams-rules-configured-in-an-allow-list-manner)

* [Die Dispatcher-Farm-Filter für Veröffentlichungen sollten die zulässigen Sling-Selektoren auf Zulassungsliste angeben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-selectors-in-an-allow-list-manner)

* [Die Dispatcher-Veröffentlichungsfarm-Filter sollten die zulässigen Sling-Suffix-Muster auf Zulassungsliste angeben](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-dispatcher-publish-farm-filters-should-specify-the-allowed-sling-suffix-patterns-in-an-allow-list-manner)

* [Die Anweisung &quot;Alle gewährt werden erforderlich&quot;sollte nicht in einem VirtualHost-Ordnerabschnitt mit einem Stammverzeichnis-Pfad verwendet werden](https://github.com/adobe/aem-dispatcher-optimizer-tool/blob/main/docs/Rules.md#dot---the-require-all-granted-directive-should-not-be-used-in-a-virtualhost-directory-section-with-a-root-directory-path)
