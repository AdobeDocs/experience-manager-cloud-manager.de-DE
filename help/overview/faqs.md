---
title: Häufig gestellte Fragen zu Cloud Manager
description: Erfahren Sie mehr über die Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager für AMS-Kunden.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 52%

---


# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Dieses Dokument enthält Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager für AMS-Kunden.

## Kann Java 11 mit Cloud Manager-Builds verwendet werden? {#java-11}

Ja. Sie müssen die `maven-toolchains-plugin` mit den richtigen Einstellungen für Java 11 hinzufügen.

* Dieser Prozess wird [hier](/help/getting-started/using-the-wizard.md) dokumentiert.
* Ein Beispiel finden Sie unter dem Beispielprojektcode [WKND](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Nach dem Wechsel von Java 8 zu Java 11 schlägt mein Build mit einer Fehlermeldung über das maven-scr-plugin fehl. Was kann ich tun? {#maven-src-plugin}

Ihr AEM Cloud Manager-Build schlägt fehl beim Versuch, den Build von Java 8 auf 11 umzuschalten. Wenn der unten stehende Fehler auftritt, müssen Sie das `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Anweisungen zum Entfernen dieses Plug-ins finden Sie in [hier](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Nach dem Wechsel von Java 8 zu Java 11 schlägt mein Build mit einer Fehlermeldung über RequireJavaVersion fehl. Was kann ich tun? {#requirejavaversion}

Bei Cloud Manager-Builds kann das `maven-enforcer-plugin` mit diesem Fehler fehlschlagen.

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Dieses bekannte Problem liegt daran, dass Cloud Manager eine andere Java-Version verwendet, um den Maven-Befehl und den Kompilierungscode auszuführen. Lassen Sie `requireJavaVersion` aus Ihren `maven-enforcer-plugin` -Konfigurationen weg.

## Die Code-Qualitätsprüfung ist fehlgeschlagen und die Implementierung ist jetzt blockiert. Gibt es eine Möglichkeit, diese Überprüfung zu umgehen? {#deployment-stuck}

Ja. Alle Fehler bei der Code-Qualität mit Ausnahme von Sicherheitsbewertungen sind nicht kritische Metriken. Daher können sie im Rahmen einer Bereitstellungs-Pipeline übersprungen werden, indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Benutzer mit der Rolle [Bereitstellungsmanager, Projektmanager oder Business Owner](/help/requirements/users-and-roles.md#role-definitions) können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Alternativ können sie die Probleme akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.

Weitere Informationen finden Sie unter [Code-Qualitätstests von Pipelines](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md#understanding-the-flow).

## Cloud Manager-Bereitstellungen schlagen beim Leistungstest in Adobe Managed Services-Umgebung fehl. Wie kann dieses Problem behoben werden, um die kritischen Metriken zu übergeben? {#debug-critical-metrics}

Auf diese Frage gibt es keine einzelne Antwort. Die folgenden Punkte zum Leistungstestschritt sind jedoch hilfreich:

* Dieser Schritt ist ein Schritt zur Webleistung. Das heißt, es ist an der Zeit, die Seite mit einem Webbrowser zu laden.
* Die in der. CSV-Ergebnisdatei aufgelisteten URLs werden während des Tests im Chrome-Browser in der Cloud Manager-Infrastruktur geladen.
* Eine gängige Metrik, die fehlschlägt, ist die Fehlerrate. Damit eine URL übergeben werden kann, muss die Haupt-URL mit dem Status `200` und in weniger als `20` Sekunden geladen werden. Wenn das Laden einer Seite den Wert `20` Sekunden überschreitet, wird sie als `504`-Fehler markiert.
* Wenn für Ihre Site eine Benutzerauthentifizierung erforderlich ist, lesen Sie [Wissenswertes zu Testergebnissen](/help/using/code-quality-testing.md#authenticated-performance-testing) , um den Test zu konfigurieren, damit Sie sich bei Ihrer Site authentifizieren können.

Weitere Informationen zu Qualitätsprüfungen finden Sie unter [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md) .

## Kann ich SNAPSHOT für die Version des Maven-Projekts verwenden? {#snapshot}

Ja. Bei Entwicklerbereitstellungen müssen die Dateien der Git-Verzweigung `pom.xml` am Ende des `<version>` -Werts `-SNAPSHOT` enthalten.

Auf diese Weise können nachfolgende Bereitstellungen weiterhin installiert werden, wenn sich die Version nicht geändert hat. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

Sie können die Version für Staging- und Produktions-Builds oder -Bereitstellungen auch auf `-SNAPSHOT` setzen. Cloud Manager legt automatisch eine geeignete Versionsnummer fest und erstellt ein Tag für Sie in Git. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

Weitere Informationen zur Versionsverwaltung finden Sie [hier dokumentiert](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## Wie funktioniert die Paket- und Bundle-Versionierung für Staging- und Produktionsbereitstellungen? {#staging-production}

In Staging- und Produktionsimplementierungen wird eine automatische Version [generiert, wie hier dokumentiert](/help/managing-code/maven-project-version.md).

Für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen legen Sie eine korrekte dreiteilige Maven-Version wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie sie in der Produktion bereitstellen.

Cloud Manager fügt seine Version automatisch den Staging- und Produktions-Builds hinzu und erstellt eine Git-Verzweigung. Es ist keine spezielle Konfiguration notwendig. Wenn Sie keine Maven-Version wie zuvor beschrieben festlegen, ist die Bereitstellung trotzdem erfolgreich und eine Version wird automatisch festgelegt.

## Mein Maven-Build schlägt bei Cloud Manager-Bereitstellungen fehl, lokal wird er jedoch ohne Fehler erstellt. Was ist los? {#maven-build-fail}

Weitere Informationen finden Sie in dieser [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) .

## Ich bin nicht in der Lage, eine Variable mit einem aio-Befehl zu setzen. Was kann ich tun? {#set-variable}

Möglicherweise erhalten Sie eine 403-Fehlermeldung wie die folgende, wenn Sie versuchen, Pipeline-Variablen über `aio`-Befehle aufzulisten oder zu setzen.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In diesem Fall muss der Benutzer, der diese Befehle ausführt, in der Admin Console zur Rolle des **Bereitstellungs-Managers** hinzugefügt werden.

Weitere Informationen finden Sie unter [API-Berechtigungen](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/).
