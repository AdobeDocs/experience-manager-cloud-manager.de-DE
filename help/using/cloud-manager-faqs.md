---
title: Häufig gestellte Fragen zu Cloud Manager
seo-title: Cloud Manager FAQs
description: Unter „Häufig gestellte Fragen zu Cloud Manager“ erhalten Sie Tipps zur Fehlerbehebung
seo-description: Follow this page to get answers on Cloud Manager FAQs
feature: Getting Started
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 6dce1f48b66c6970c3ba025031f0adcbd01195dd
workflow-type: ht
source-wordcount: '874'
ht-degree: 100%

---

# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen zu Cloud Manager.

## Kann Java 11 mit Cloud Manager-Builds verwendet werden? {#java-11-cloud-manager}

AEM Cloud Manager-Build schlägt fehl beim Versuch, den Build von Java 8 auf 11 umzuschalten. Das Problem kann viele Ursachen haben. Die häufigsten Ursachen werden nachfolgend beschrieben:

* Fügen Sie das maven-toolchain-plugin mit den richtigen Einstellungen für Java 11 hinzu, wie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=de#getting-started) beschrieben.  Ein Beispiel finden Sie unter [wknd-Beispielprojekt-Code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Wenn der unten stehende Fehler auftritt, müssen Sie die Verwendung von `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren. Anweisungen finden Sie [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Bei Cloud Manager-Builds schlägt das Maven-Enforcer-Plug-in mit dem Fehler `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` fehl. Dies ist ein bekanntes Problem, da Cloud Manager eine andere Version von Java verwendet, um den maven-Befehl auszuführen, anstatt Code zu kompilieren. Verwenden Sie `requireJavaVersion` vorerst nicht in Ihren maven-enforcer-plugin-Konfigurationen.

## Unsere Bereitstellung ist blockiert, da die Code-Qualitätsprüfung fehlgeschlagen ist. Gibt es eine Möglichkeit, diese Überprüfung zu umgehen? {#deployment-stuck}

Ja. Alle Fehler bei der Überprüfung der Code-Qualität mit Ausnahme der *Sicherheitseinstufung* sind nicht kritische Metriken, sodass sie als Teil einer Bereitstellungs-Pipeline übersprungen werden können, indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Benutzer mit der Rolle [Implementierungs-Manager, Projekt-Manager oder Geschäftsinhaber](/help/using/setting-up-users-and-roles.md#role-definitions) können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.

Weitere Informationen finden Sie unter [Code-Qualitätstests von Pipelines](/help/using/understand-your-test-results.md#three-tier-gates-while-running-a-pipeline) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/configuring-non-production-pipelines.md#understanding-the-flow).

## Cloud Manager-Bereitstellungen schlagen beim Leistungstest in Adobe Managed Services-Umgebung fehl. Wie können wir dies debuggen, um kritische Metriken zu erfüllen? {#debug-critical-metrics}

Informationen zur Auswertung der Ergebnisse finden Sie unter [Wissenswertes zu Testergebnissen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#how-to-use).

Einige Hinweise zum Leistungstest:

* Der *Leistungstest* ist ein Web-Leistungsschritt, d. h. der Zeitaufwand, bis die Seite in einem Webbrowser geladen ist.
* Die in der *CSV*-Ergebnisdatei aufgelisteten URLs werden während des Tests im Chrome-Browser in der Cloud Manager-Infrastruktur geladen.
* Eine häufig fehlgeschlagene Metrik ist die *Fehlerquote*. Damit eine URL den Test besteht, muss die Haupt-URL mit dem Status `200` und in weniger als `20` Sekunden geladen werden. Seitenladevorgänge, die länger als `20` Sekunden dauern, werden als `504`-Fehler gekennzeichnet.
* Wenn für die Site eine Benutzerauthentifizierung erforderlich ist, finden Sie unter [Wissenswertes zu Testergebnissen](understand-your-test-results.md#authenticated-performance-testing) weitere Informationen dazu, wie Sie den Test zur Authentifizierung auf Ihrer Site konfigurieren.

## Können wir SNAPSHOT in der Version des Maven-Projekts verwenden? Wie funktioniert die Versionierung der Pakete und der JAR-Paketdateien für Staging- und Produktionsbereitstellungen? {#snapshot-version}

In den folgenden Szenarien erfahren Sie mehr über die Versionierung der Pakete und JAR-Paketdateien für Staging- und Produktionsbereitstellungen:

1. Bei Entwicklerbereitstellungen müssen die `pom.xml`-Dateien der Git-Verzweigung `-SNAPSHOT` am Ende des `<version>`-Werts enthalten. Dies ermöglicht nachfolgend eine Bereitstellung, bei der die Version nicht geändert und dennoch installiert wird. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

1. Bei der Staging- und Produktionsbereitstellung wird wie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=den#managing-code) beschrieben eine automatische Version generiert.

1. Legen Sie für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen eine geeignete dreiteilige Maven-Version wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie eine andere Bereitstellung für die Produktion durchführen müssen.

1. Cloud Manager fügt Staging- und Produktions-Builds automatisch eine eigene Version hinzu und erstellt sogar eine Git-Verzweigung. Es ist keine spezielle Konfiguration notwendig. Wenn Schritt 3 oben übersprungen wird, funktioniert die Bereitstellung dennoch einwandfrei und es wird automatisch eine Version festgelegt.

1. Es gibt keine Probleme, wenn Sie die Version für Staging- und Produktions-Builds oder -Bereitstellungen `-SNAPSHOT` überlassen. Cloud Manager legt automatisch eine geeignete Versionsnummer fest und erstellt ein Tag für Sie in Git. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

1. Wenn Sie einen experimentellen Code für die Entwicklungsumgebung ausprobieren möchten, können Sie eine neue Git-Verzweigung erstellen und die Pipeline so einrichten, dass diese andere Verzweigung verwendet wird. Dies ist nützlich, wenn Bereitstellungen fehlschlagen und Sie ältere Versionen des Codes testen möchten, um zu sehen, wann der Fehler erstmals aufgetreten ist.

   Der unten stehende Git-Befehl erstellt eine Remote-Verzweigung mit dem Namen *testbranch1* gegen einen bestimmten bereits vorhandenen Commit `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Diese spezielle Verzweigung kann in Cloud Manager verwendet werden, ohne dass sich dies auf andere Verzweigungen auswirkt:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Weitere Informationen finden Sie in der [Git-Dokumentation](https://git-scm.com/book/en/v2/Git-Internals-Git-References).

   Wenn Sie die Testverzweigung später löschen möchten, verwenden Sie den Befehl „delete“:

   `git push origin --delete testbranch1`

## Der Maven-Build schlägt in Cloud Manager-Bereitstellungen fehl, wird jedoch ohne Fehler lokal erstellt. Vorgehensweise beim Debugging? {#maven-build-fail}

Weitere Informationen finden Sie unter [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Es ist nicht möglich, eine Variable über „aio cloud manager set pipeline“-Variablen festzulegen. Wie können diese Probleme behoben werden? {#set-variable}

Wenn beim Versuch, Pipeline-Variablen über Befehle wie die folgenden aufzulisten oder festzulegen, der Fehler `403` auftritt, müssen Sie in der Admin Console in der Cloud Manager-Produktrolle *Bereitstellungs-Manager* hinzugefügt werden.\
Weitere Informationen finden Sie unter [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md).

Weitere Befehle und Fehler:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
