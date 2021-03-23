---
title: Häufig gestellte Fragen zu Cloud Manager
seo-title: Häufig gestellte Fragen zu Cloud Manager
description: Unter Häufig gestellte Fragen zu Cloud Manager erhalten Sie Tipps zur Fehlerbehebung
seo-description: Auf dieser Seite finden Sie Antworten zu den häufig gestellten Fragen zu Cloud Manager
feature: Erste Schritte
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---


# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen zu Cloud Manager.

## Kann Java 11 mit Cloud Manager-Builds verwendet werden? {#java-11-cloud-manager}

AEM Cloud Manager-Build schlägt fehl, wenn versucht wird, den Build von Java 8 auf 11 umzuschalten. Das Problem kann viele Ursachen haben, und die häufigsten Ursachen werden nachfolgend beschrieben:

* hinzufügen Sie das maven-toolchain-plugin mit den richtigen Einstellungen für Java 11, wie hier beschrieben [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Beispiel: Siehe [Arbeits-Beispielprojektcode](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Wenn der unten stehende Fehler auftritt, müssen Sie die Verwendung von `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren. Anweisungen finden Sie unter [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Bei Cloud Manager-Builds schlägt das Maven-Enforcer-Plugin mit dem Fehler `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` fehl. Dies ist ein bekanntes Problem, da Cloud Manager eine andere Version von Java verwendet, um den Befehl maven im Vergleich zum Kompilierungscode auszuführen. Lassen Sie vorerst `requireJavaVersion` aus Ihren maven-enforcer-plugin-Konfigurationen aus.

## Unsere Bereitstellung ist blockiert, da die Überprüfung der Code-Qualität fehlgeschlagen ist. Gibt es eine Möglichkeit, diesen Scheck zu umgehen? {#deployment-stuck}

Alle Fehler in der Codequalität mit Ausnahme von *Sicherheitsbewertung* sind nicht kritische Metriken, sodass sie umgangen werden können, indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Ein Benutzer mit der Rolle [Deployment Manager, Project Manager oder Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) kann die Probleme überschreiben. In diesem Fall wird die Pipeline fortgesetzt oder er kann die Probleme akzeptieren. In diesem Fall stoppt die Pipeline bei einem Fehler.  Weitere Informationen finden Sie unter [Dreistufige Tore beim Ausführen einer Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#how-to-use).

## Cloud Manager-Bereitstellungen schlagen beim Leistungstest in Adobe Managed Services-Umgebung fehl. Wie können wir dies debuggen, um die kritischen Metriken zu übergeben? {#debug-critical-metrics}

Die Ergebnisse finden Sie unter [Testergebnisse verstehen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use).

Einige Hinweise zum Schritt &quot;Leistungstest&quot;:

* Der *Leistungsschritt* ist ein Webleistungsschritt, d. h. der Zeitpunkt, zu dem die Seite mit einem Webbrowser geladen wird.
* Die in der Ergebnisdatei *CSV* aufgelisteten URLs werden während des Tests in einem Chrome-Browser in der Cloud Manager-Infrastruktur geladen.
* Eine häufig vorkommende Metrik, die fehlschlägt, ist die *Fehlerquote*. Damit eine URL übergeben wird, muss die Haupt-URL mit dem Status `200` und in weniger als `20` Sekunden geladen werden. Seitenladevorgänge, die länger als `20` Sekunden sind, werden als `504`-Fehler gekennzeichnet.
* Wenn für Ihre Site die Benutzerauthentifizierung erforderlich ist, lesen Sie [Authentifizierter Leistungstest](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) für die Konfiguration des Tests zur Authentifizierung für Ihre Site.

## Können wir SNAPSHOT in der Version des Maven Projekts verwenden? Wie funktioniert die Versionierung der Pakete und der Bundle-JAR-Dateien für Bereitstellungen von Stage und Produktion? {#snapshot-version}

In den folgenden Szenarien erfahren Sie mehr über die Versionierung der Pakete und Bundle-JAR-Dateien für Bereitstellungen von Stage und Produktion:

1. Bei Entwicklerbereitstellungen müssen die Git-Zweig-Dateien `pom.xml` `-SNAPSHOT` am Ende des `<version>`-Werts enthalten. Dies ermöglicht eine spätere Bereitstellung, bei der die Version nicht geändert wird und weiterhin installiert wird. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

1. In der Bereitstellung für Stage und Produktion wird eine automatische Version generiert, wie beschrieben [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Legen Sie für benutzerdefinierte Versionen in Bereitstellungen von Stage und Produktion eine 3-teilige Masterversion wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie eine andere Bereitstellung für die Produktion durchführen müssen.

1. Cloud Manager fügt seine Version automatisch den Stage- und Production-Builds hinzu und erstellt sogar eine Git-Verzweigung. Es ist keine spezielle Konfiguration erforderlich. Wenn Schritt 3 oben übersprungen wird, funktioniert die Bereitstellung weiterhin einwandfrei und eine Version wird automatisch eingestellt.

1. Es gibt keine Probleme, wenn Sie die Version für Stage- und Production-Builds oder Bereitstellungen mit `-SNAPSHOT` belassen. Cloud Manager legt automatisch eine korrekte Versionsnummer fest und erstellt ein Tag für Sie in Git. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

1. Wenn Sie einen experimentellen Code für die Entwicklungs-Umgebung ausprobieren möchten, können Sie eine neue Git-Verzweigung erstellen und die Pipeline so einrichten, dass diese andere Verzweigung verwendet wird. Dies ist nützlich, wenn Bereitstellungs-Beginn fehlschlagen und Sie mit älteren Versionen des Codes testen möchten, um zu sehen, wann der Fehler auftritt.

   Der unten stehende Befehl &quot;Git&quot;erstellt eine Remote-Verzweigung mit dem Namen *testbranch1* gegen eine bestimmte bereits vorhandene Bindung `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Diese spezielle Verzweigung kann in Cloud Manager verwendet werden, ohne dass sich dies auf andere Verzweigungen auswirkt:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Weitere Informationen finden Sie in der [Git-Dokumentation](https://git-scm.com/book/en/v2/Git-Internals-Git-References).

   Wenn Sie die Testverzweigung später löschen möchten, verwenden Sie den Befehl delete:

   `git push origin --delete testbranch1`

## Der Maven-Build schlägt in der Cloud Manager-Bereitstellung fehl, wird jedoch ohne Fehler lokal erstellt. Debugging? {#maven-build-fail}

Weitere Informationen finden Sie unter [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Es ist nicht möglich, eine Variable über AEM Cloud Manager Pipeline-Variablen festzulegen. Wie können diese Probleme behoben werden? {#set-variable}

Wenn Sie beim Versuch, Pipelinevariablen über ähnliche Befehle wie die folgenden Liste oder festzulegen, den Fehler `403` erhalten, müssen Sie als *Deployment Manager* Cloud Manager-Produktrolle in der Admin Console hinzugefügt werden.\
Weitere Informationen finden Sie unter [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md).

Weitere Befehle und Fehler:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
