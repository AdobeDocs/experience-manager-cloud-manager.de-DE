---
title: Häufig gestellte Fragen zu Cloud Manager
description: Hier finden Sie Antworten auf die am häufigsten gestellten Fragen zu Cloud Manager für AMS-Kundinnen und -Kunden.
exl-id: 52c1ca23-5b42-4eae-b63a-4b22ef1a5aee
TQID: https://experienceleague.adobe.com/aBIiazPCm-krE6rew6k-HSl-Uvc79eagMzM7uYciWdc
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 4dcc367f82c51626ca449ff389a9c9574a562ff7
workflow-type: tm+mt
source-wordcount: 764
ht-degree: 69%

---

# Häufig gestellte Fragen zu Cloud Manager {#cloud-manager-faqs}

Dieses Dokument enthält Antworten für AMS-Kundinnen und -Kunden auf die am häufigsten gestellten Fragen zu Cloud Manager.

<!-- 
## Is it possible to use Java 11 with Cloud Manager builds? {#java-11}

Yes. You need to add the `maven-toolchains-plugin` with the correct settings for Java 11.

* This process is documented [here](/help/getting-started/using-the-wizard.md).
* For an example, see the [WKND sample project code](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75). 
-->

## Nach dem Wechsel von Java 8 zu Java 11 schlägt mein Build mit einer Fehlermeldung über das maven-scr-plugin fehl. Was kann ich tun? {#maven-src-plugin}

Ihr AEM Cloud Manager-Build schlägt fehl beim Versuch, von Java 8 zu Java 11 zu wechseln. Wenn der unten stehende Fehler auftritt, müssen Sie das `maven-scr-plugin` entfernen und alle OSGi-Anmerkungen in OSGi R6-Anmerkungen konvertieren.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Anweisungen zum Entfernen dieses Plug-ins finden Sie [hier](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Nach dem Wechsel von Java 8 zu Java 11 schlägt mein Build mit einer Fehlermeldung über RequireJavaVersion fehl. Was kann ich tun? {#requirejavaversion}

Bei Cloud Manager-Builds kann das `maven-enforcer-plugin` mit diesem Fehler fehlschlagen.

```text
[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion
```

Dieses Problem tritt auf, weil Cloud Manager eine andere Java-Version verwendet, um den Maven-Befehl auszuführen. Diese Version unterscheidet sich von der, die zum Kompilieren von Code verwendet wird. Lassen Sie `requireJavaVersion` in Ihren `maven-enforcer-plugin`-Konfigurationen weg.

## Die Code-Qualitätsprüfung ist fehlgeschlagen und die Bereitstellung wird jetzt angehalten. Gibt es eine Möglichkeit, diese Überprüfung zu umgehen? {#deployment-stuck}

Ja. Alle Fehler bei der Überprüfung der Code-Qualität mit Ausnahme der Sicherheitseinstufung sind nicht kritische Metriken. Daher können sie als Teil einer Implementierungs-Pipeline übersprungen werden. indem die Elemente in der Ergebnis-Benutzeroberfläche erweitert werden.

Benutzende mit der Rolle [Bereitstellungs-Manager, Projekt-Manager oder Geschäftsinhaber](/help/requirements/users-and-roles.md#role-definitions) können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Oder sie können die Probleme akzeptieren. In diesem Fall wird die Pipeline mit einem Fehler angehalten.

Weitere Informationen finden Sie unter [Code-Qualitätstests von Pipelines](/help/using/code-quality-testing.md#three-tier-gates-while-running-a-pipeline) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md#understanding-the-flow).

## Cloud Manager-Bereitstellungen schlagen beim Leistungstest in Adobe Managed Services-Umgebung fehl. Wie kann dieses Problem behoben werden, um kritische Metriken zu erfüllen? {#debug-critical-metrics}

Auf diese Frage gibt es keine endgültige Antwort. Die folgenden Punkte zum Leistungstest sind jedoch hilfreich:

* Dieser Schritt ist ein Schritt zur Web-Leistung. Das heißt, es ist ungefähr die Zeit, die zum Laden einer Seite in einem Webbrowser benötigt wird.
* Die in der CSV-Ergebnisdatei aufgelisteten URLs werden während des Tests in einem Chrome-Browser in der Cloud Manager-Infrastruktur geladen.
* Eine häufig fehlgeschlagene Metrik ist die Fehlerquote. Damit also eine URL den Test besteht, muss die Haupt-URL mit dem Status `200` und in weniger als `20` Sekunden geladen werden. Wenn das Laden einer Seite `20` Sekunden überschreitet, wird sie als `504`-Fehler markiert.
* Wenn für Ihre Website eine Benutzerauthentifizierung erforderlich ist, finden Sie unter [Wissenswertes zu Testergebnissen](/help/using/code-quality-testing.md#authenticated-performance-testing) weitere Informationen dazu, wie Sie den Test zur Authentifizierung Ihrer Website konfigurieren.

Weitere Informationen zu Qualitätsprüfungen finden Sie unter [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md).

## Kann ich SNAPSHOT für die Version des Maven-Projekts verwenden? {#snapshot}

Ja. Bei Entwicklerbereitstellungen müssen die `pom.xml`-Dateien der Git-Verzweigung am Ende des `<version>`-Werts `-SNAPSHOT` enthalten.

Dadurch können nachfolgende Bereitstellungen installiert werden, wenn sich die Version nicht geändert hat. In Entwicklerbereitstellungen wird keine automatische Version für den Maven-Build hinzugefügt oder generiert.

Sie können die Version für Staging- und Produktions-Builds oder -Bereitstellungen auch auf `-SNAPSHOT` setzen. Cloud Manager legt automatisch eine geeignete Versionsnummer fest und erstellt ein Tag für Sie in Git. Falls erforderlich, kann auf dieses Tag später verwiesen werden.

Weitere Informationen zur Versionsverwaltung finden Sie [hier dokumentiert](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/project-version-handling).

## Wie funktioniert die Paket- und Bundle-Versionierung für Staging- und Produktionsbereitstellungen? {#staging-production}

Bei Staging- und Produktionsbereitstellungen wird, wie [hier beschrieben](/help/managing-code/maven-project-version.md), eine automatische Version generiert.

Für die benutzerdefinierte Versionierung in Staging- und Produktionsbereitstellungen legen Sie eine korrekte dreiteilige Maven-Version wie `1.0.0` fest. Erhöhen Sie die Version jedes Mal, wenn Sie sie in der Produktion bereitstellen.

Cloud Manager fügt zu Staging- und Produktions-Builds automatisch eine eigene Version hinzu und erstellt eine Git-Verzweigung. Es ist keine spezielle Konfiguration notwendig. Wenn Sie keine Maven-Version wie zuvor beschrieben festlegen, ist die Bereitstellung dennoch erfolgreich und eine Version wird automatisch festgelegt.

## Mein Maven-Build schlägt für Cloud Manager-Bereitstellungen fehl, lokal wird er jedoch ohne Fehler erstellt. Was ist die Ursache? {#maven-build-fail}

Weitere Informationen finden Sie in dieser [Git-Ressource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md).

## Ich kann eine Variable nicht mit einem aio-Befehl festlegen. Was kann ich tun? {#set-variable}

Sie erhalten eine 403-Fehlermeldung wie die folgende, wenn Sie versuchen, Pipeline-Variablen über `aio`-Befehle aufzulisten oder zu setzen.

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

Weitere Informationen finden Sie unter [API-Berechtigungen](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions).
