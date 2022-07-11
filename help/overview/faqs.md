---
title: Häufig gestellte Fragen zu Cloud Manager
description: Dieses Dokument enthält Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager für AMS-Kunden.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 6be659e02df0657ec7d3dbce8c18c44a327a36f4
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 28%

---


# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Dieses Dokument enthält Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager für AMS-Kunden.

## Kann Java 11 mit Cloud Manager-Builds verwendet werden? {#java-11}

Ja. Sie müssen die `maven-toolchains-plugin` mit den richtigen Einstellungen für Java 11.

* Dieser Vorgang wird dokumentiert [hier.](/help/getting-started/using-the-wizard.md)
* Ein Beispiel finden Sie unter [Beispiel-Projektcode anzeigen.](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)

## Mein Build schlägt mit einem Fehler bezüglich maven-scr-plugin nach dem Wechsel von Java 8 zu Java 11 fehl. Was kann ich tun? {#maven-src-plugin}

Ihr AEM Cloud Manager-Build schlägt möglicherweise fehl, wenn versucht wird, den Build von Java 8 auf 11 zu wechseln. Wenn der folgende Fehler auftritt, müssen Sie `maven-scr-plugin` und konvertieren Sie alle OSGi-Anmerkungen in OSGi R6-Anmerkungen.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Anweisungen zum Entfernen dieses Plug-ins finden Sie unter [siehe hier.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)

## Mein Build schlägt mit einem Fehler bezüglich RequireJavaVersion nach dem Wechsel von Java 8 zu Java 11 fehl. Was kann ich tun? {#requirejavaversion}

Bei Cloud Manager-Builds muss die `maven-enforcer-plugin` kann bei diesem Fehler fehlschlagen

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Dies ist ein bekanntes Problem, da Cloud Manager eine andere Version von Java verwendet, um den maven-Befehl auszuführen, anstatt Code zu kompilieren. Einfach weglassen `requireJavaVersion` von `maven-enforcer-plugin` -Konfigurationen.

## Die Code-Qualitätsprüfung ist fehlgeschlagen und unsere Implementierung ist blockiert. Gibt es eine Möglichkeit, diese Überprüfung zu umgehen? {#deployment-stuck}

Ja. Alle Fehler bei der Code-Qualität mit Ausnahme von Sicherheitsbewertungen sind nicht kritische Metriken, sodass sie als Teil einer Bereitstellungs-Pipeline übersprungen werden können, indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Benutzer mit der Rolle [Implementierungs-Manager, Projekt-Manager oder Geschäftsinhaber](/help/requirements/users-and-roles.md#role-definitions) können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.

Weitere Informationen finden Sie unter [Code-Qualitätstests von Pipelines](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md#understanding-the-flow).

## Cloud Manager-Bereitstellungen schlagen beim Leistungstest in Adobe Managed Services-Umgebung fehl. Wie können wir dies debuggen, um kritische Metriken zu erfüllen? {#debug-critical-metrics}

Auf diese Frage gibt es keine einzige Antwort. Dies sind jedoch einige wichtige Punkte bezüglich des Leistungstestschritts, die Sie beachten sollten:

* Dieser Schritt ist ein Schritt zur Webleistung, d. h. die Zeit, die Seite mit einem Webbrowser zu laden.
* Die in der .csv-Ergebnisdatei aufgelisteten URLs werden während des Tests in einen Chrome-Browser in der Cloud Manager-Infrastruktur geladen.
* Eine häufig fehlgeschlagene Metrik ist die Fehlerquote.
   * Damit eine URL den Test besteht, muss die Haupt-URL mit dem Status `200` und in weniger als `20` Sekunden geladen werden.
   * Seitenladevorgänge, die länger als `20` Sekunden dauern, werden als `504`-Fehler gekennzeichnet.
* Wenn für Ihre Site eine Benutzerauthentifizierung erforderlich ist, lesen Sie das Dokument . [Wissenswertes zu Testergebnissen](/help/using/code-quality-testing.md#authenticated-performance-testing) zum Konfigurieren des Tests zur Authentifizierung für Ihre Site.

Lesen Sie das Dokument [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md) für weitere Informationen über Qualitätsprüfungen.

## Kann ich SNAPSHOT für die Version des Maven-Projekts verwenden? {#snapshot}

Ja. Bei Entwicklerbereitstellungen die Git-Verzweigung `pom.xml` -Dateien müssen `-SNAPSHOT` am Ende des `<version>` -Wert.

Dadurch kann die nachfolgende Bereitstellung weiterhin installiert werden, wenn sich die Version nicht geändert hat. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

Sie können die Version auch auf `-SNAPSHOT` für Staging- und Produktions-Builds oder -Bereitstellungen. Cloud Manager legt automatisch eine ordnungsgemäße Versionsnummer fest und erstellt ein Tag für Sie in Git. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

Weitere Informationen zur Versionsverwaltung finden Sie unter [dokumentiert.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling.html)

## Wie funktioniert die Paket- und Bundle-Versionierung für Staging- und Produktionsimplementierungen? {#staging-production}

In Staging- und Produktionsimplementierungen wird eine automatische Version generiert [wie hier beschrieben.](/help/managing-code/maven-project-version.md)

Legen Sie für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen eine geeignete dreiteilige Maven-Version wie `1.0.0`. Erhöhen Sie die Version jedes Mal, wenn Sie sie in der Produktion bereitstellen.

Cloud Manager fügt seine Version automatisch den Staging- und Produktions-Builds hinzu und erstellt eine Git-Verzweigung. Es ist keine spezielle Konfiguration notwendig. Wenn Sie keine Maven-Version wie zuvor beschrieben festlegen, ist die Bereitstellung weiterhin erfolgreich und es wird automatisch eine Version festgelegt.

## Mein Maven-Build schlägt bei Cloud Manager-Implementierungen fehl, er wird jedoch ohne Fehler lokal erstellt. Was ist los? {#maven-build-fail}

Siehe dies [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) für weitere Details.

## Ich kann eine Variable nicht mit einem aio-Befehl festlegen. Was kann ich tun? {#set-variable}

Beim Versuch, Pipeline-Variablen aufzulisten oder festzulegen über `aio` Befehle.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In diesem Fall muss der Benutzer, der diese Befehle ausführt, zum **Bereitstellungsmanager** Rolle in der Admin Console.

Weitere Informationen finden Sie unter [API-Berechtigungen](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/).
