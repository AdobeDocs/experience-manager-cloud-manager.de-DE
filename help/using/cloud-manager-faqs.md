---
title: Häufig gestellte Fragen zu Cloud Manager
seo-title: Häufig gestellte Fragen zu Cloud Manager
description: Tipps zur Fehlerbehebung finden Sie in den häufig gestellten Fragen zu Cloud Manager .
seo-description: Auf dieser Seite erhalten Sie Antworten auf häufig gestellte Fragen zu Cloud Manager
feature: Erste Schritte
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---

# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen zu Cloud Manager.

## Ist die Verwendung von Java 11 mit Cloud Manager-Builds möglich? {#java-11-cloud-manager}

Der Build von AEM Cloud Manager schlägt beim Versuch fehl, den Build von Java 8 auf 11 zu wechseln. Das Problem kann viele Ursachen haben. Die häufigsten Ursachen sind nachfolgend beschrieben:

* Fügen Sie das maven-toolchain-plugin mit den richtigen Einstellungen für Java 11 hinzu, wie in [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started) beschrieben.  Siehe beispielsweise den Beispielcode für das Projekt [wknd](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Wenn der folgende Fehler auftritt, müssen Sie die Verwendung von `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren. Anweisungen finden Sie unter [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Bei Cloud Manager-Builds schlägt das Maven-Enforcer-Plug-in mit dem Fehler `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"` fehl. Dies ist ein bekanntes Problem, da Cloud Manager eine andere Version von Java verwendet, um den Maven-Befehl im Vergleich zum Kompilierungscode auszuführen. Lassen Sie zunächst `requireJavaVersion` aus Ihren Maven-Enforcer-Plug-in-Konfigurationen weg.

## Unsere Implementierung hängt davon ab, dass die Überprüfung der Code-Qualität fehlgeschlagen ist. Gibt es eine Möglichkeit, diese Prüfung zu umgehen? {#deployment-stuck}

Alle Fehler bei der Code-Qualität mit Ausnahme von *Sicherheitsbewertung* sind nicht kritische Metriken, sodass sie umgangen werden können, indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Benutzer mit der Rolle [Bereitstellungsmanager, Projektmanager oder Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt oder sie können die Probleme akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.  Weitere Informationen finden Sie unter [Dreistufige Akzeptanztests beim Ausführen einer Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#how-to-use).

## Cloud Manager-Implementierungen schlagen beim Leistungstestschritt in Adobe Managed Services-Umgebungen fehl. Wie können wir dies debuggen, um die kritischen Metriken zu übergeben? {#debug-critical-metrics}

Weitere Informationen zu den Ergebnissen finden Sie unter [Grundlegendes zu Ihren Testergebnissen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) .

Einige Hinweise zum Schritt &quot;Leistungstest&quot;:

* Der *Leistungsschritt* ist ein Webleistungsschritt, d. h. der Zeitpunkt, zu dem die Seite mit einem Webbrowser geladen wird.
* Die in der Ergebnisdatei *CSV* aufgelisteten URLs werden während des Tests in einen Chrome-Browser in der Cloud Manager-Infrastruktur geladen.
* Eine gängige Metrik, die fehlschlägt, ist die *Fehlerrate*. Damit eine URL übergeben werden kann, muss die Haupt-URL mit dem Status `200` und in weniger als `20` Sekunden geladen werden. Seitenladevorgänge, die `20` Sekunden überschreiten, werden als `504` Fehler markiert.
* Wenn für Ihre Site die Benutzerauthentifizierung erforderlich ist, finden Sie unter [Authentifizierte Leistungstests](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) Informationen zum Konfigurieren des Tests für die Authentifizierung bei Ihrer Site.

## Können wir SNAPSHOT in der Version des Maven-Projekts verwenden? Wie funktioniert die Versionierung der Pakete und Bundle-JAR-Dateien für Staging- und Produktionsimplementierungen? {#snapshot-version}

In den folgenden Szenarien erfahren Sie mehr über die Versionierung der Pakete und Bundle-JAR-Dateien für Staging- und Produktionsimplementierungen:

1. Bei Entwicklerbereitstellungen muss die Git-Verzweigung `pom.xml` -Dateien `-SNAPSHOT` am Ende des Wertes `<version>` enthalten. Dies ermöglicht eine nachfolgende Bereitstellung, bei der die Version nicht geändert wird, um weiterhin installiert zu werden. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

1. In der Staging- und Produktionsimplementierung wird eine automatische Version generiert, wie dokumentiert [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Legen Sie für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen eine 3-teilige geeignete Maven-Version wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie eine andere Bereitstellung für die Produktion durchführen müssen.

1. Cloud Manager fügt seine Version automatisch zu Staging- und Produktions-Builds hinzu und erstellt sogar eine Git-Verzweigung. Es ist keine spezielle Konfiguration erforderlich. Wenn Schritt 3 oben übersprungen wird, funktioniert die Bereitstellung weiterhin einwandfrei und eine Version wird automatisch festgelegt.

1. Es gibt keine Probleme, wenn Sie die Version für Staging- und Produktions-Builds oder -Bereitstellungen mit `-SNAPSHOT` belassen. Cloud Manager legt automatisch eine ordnungsgemäße Versionsnummer fest und erstellt ein Tag für Sie in Git. Auf dieses Tag kann bei Bedarf später verwiesen werden.

1. Wenn Sie einen experimentellen Code in der Entwicklungsumgebung ausprobieren möchten, können Sie eine neue Git-Verzweigung erstellen und die Pipeline so einrichten, dass sie diese andere Verzweigung verwendet. Dies ist nützlich, wenn Bereitstellungen fehlschlagen und Sie mit älteren Versionen des Codes testen möchten, um zu sehen, wann er fehlschlug.

   Der folgende Git-Befehl erstellt eine Remote-Verzweigung mit dem Namen *testbranch1* für einen bestimmten bereits vorhandenen Commit `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Diese spezielle Verzweigung kann in Cloud Manager verwendet werden, ohne dass andere Verzweigungen betroffen sind:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Weitere Informationen finden Sie in der [Git-Dokumentation](https://git-scm.com/book/en/v2/Git-Internals-Git-References) .

   Wenn Sie die Testverzweigung später löschen möchten, verwenden Sie den Befehl zum Löschen :

   `git push origin --delete testbranch1`

## Maven-Build schlägt in Cloud Manager fehl, wird jedoch fehlerfrei lokal erstellt. Debugging? {#maven-build-fail}

Weitere Informationen finden Sie unter [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) .

## Pipeline-Variablen können nicht über aio Cloud Manager festgelegt werden. Wie können diese Probleme behoben werden? {#set-variable}

Wenn Sie beim Versuch, Pipeline-Variablen über ähnliche Befehle wie die folgenden aufzulisten oder festzulegen, den Fehler `403` erhalten, müssen Sie in der Admin Console als *Bereitstellungsmanager* Cloud Manager -Produktrolle hinzugefügt werden.\
Weitere Informationen finden Sie unter [API-Berechtigungen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) .

Verwandte Befehle und Fehler:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fehler*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`
