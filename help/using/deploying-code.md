---
title: Bereitstellen Ihres Codes
seo-title: Bereitstellen Ihres Codes
description: Bietet eine Übersicht über den Bereitstellungsprozess in Cloud Manager
seo-description: Erfahren Sie, wie Sie den Code nach der Konfiguration der Pipeline (Repository, Umgebung und Testing-Umgebung) bereitstellen.
uuid: 4e3807e1-437e-4922-ba48-0bcadf293a99
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
discoiquuid: 832a4647-9b83-4a9d-b373-30fe16092b15
feature: Code-Bereitstellung
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: df2f598f91201d362f54b17e4092ff6bd6a72cec
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 91%

---

# Bereitstellen Ihres Codes {#deploy-your-code}

## Bereitstellen von Code mit Cloud Manager {#deploying-code-with-cloud-manager}

>[!NOTE]
>Weitere Informationen zum Bereitstellen von Code für Cloud Manager in AEM als Cloud Service finden Sie unter [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#using-cloud-manager).

Sobald Sie Ihre Produktions-Pipeline (Repository, Umgebung und Testumgebung) konfiguriert haben, können Sie Ihren Code bereitstellen.

1. Klicken Sie in Cloud Manager auf **Bereitstellen**, um den Implementierungsprozess zu starten.

   ![](assets/Deploy1.png)

1. Der Bildschirm **Pipeline-Ausführung** wird angezeigt.

   Klicken Sie auf **Erstellen**, um den Prozess zu starten.

   ![](assets/Deploy2.png)

1. Der vollständige Build-Prozess stellt Ihren Code bereit.

   Der Build-Prozess umfasst die folgenden Phasen:

   1. Staging-Implementierung
   1. Staging-Tests
   1. Produktionsimplementierung

   >[!NOTE]
   >
   >Außerdem können Sie die Schritte der verschiedenen Implementierungsprozesse überprüfen, indem Sie die Protokolle anzeigen oder die Ergebnisse anhand der Testkriterien überprüfen.

   Die **Staging-Implementierung** umfasst die folgenden Schritte:

   * Validierung: Dieser Schritt stellt sicher, dass die Pipeline so konfiguriert ist, dass die derzeit verfügbaren Ressourcen verwendet werden. So wird z. B. überprüft, ob die konfigurierte Verzweigung vorhanden ist und die Umgebungen verfügbar sind.
   * Build- und Komponententests: Dieser Schritt führt einen containerisierten Build-Prozess aus. Weitere Informationen zur Build-Umgebung finden Sie unter [Grundlagen zur Build-Umgebung](/help/using/build-environment-details.md).
   * Code-Scan: Dieser Schritt bewertet die Qualität Ihres Anwendungs-Codes. Weitere Informationen zum Testprozess finden Sie unter [Testergebnisse verstehen](understand-your-test-results.md).
   * Bereitstellung in der Staging-Umgebung

   ![](assets/Stage_Deployment1.png)

   **Staging-Tests** umfassen die folgenden Schritte:

   * Sicherheitstests: Dieser Schritt bewertet die Auswirkungen Ihres Anwendungs-Codes auf die Sicherheit der AEM-Umgebung. Weitere Informationen zum Testprozess finden Sie unter [Testergebnisse verstehen](understand-your-test-results.md).
   * Leistungstests: Dieser Schritt bewertet die Leistung Ihres Anwendungs-Codes. Weitere Informationen zum Testprozess finden Sie unter [Testergebnisse verstehen](understand-your-test-results.md).

   ![](assets/Stage_Testing1.png)

   Die **Produktionsbereitstellung** umfasst die folgenden Schritte:

   * **Genehmigungsantrag** (sofern aktiviert)
   * **Zeitplan zur Produktionsbereitstellung** (sofern aktiviert)
   * **CSE-Unterstützung** (sofern aktiviert)
   * **Bereitstellung für Produktion**

   ![](assets/Prod_Deployment1.png)

   >[!NOTE]
   >
   >Der **Zeitplan zur Produktionsbereitstellung** wird bei der Konfiguration der Pipeline aktiviert.
   >
   >
   >Mit dieser Option können Sie die Produktionsbereitstellung planen. Oder klicken Sie auf **Jetzt**, um die Produktionsbereitstellung sofort auszuführen.
   >
   >
   >Datum und Uhrzeit für den Zeitplan beziehen sich auf die Zeitzone des Benutzers.
   >
   >
   >Klicken Sie auf **Bestätigen**, um die Einstellungen zu überprüfen.

   ![](assets/Production_Deployment1.png)

   Sobald Sie den Bereitstellungsplan bestätigt haben, wird die Codebereitstellung abgeschlossen.

   Der folgende Bildschirm wird angezeigt, wenn im obigen Schritt die Option **Jetzt** ausgewählt wurde.

   ![](assets/Production_Deployment2.png)

## Timeouts {#timeouts}

Die folgenden Schritte führen zu einem Timeout, wenn auf Benutzerfeedback gewartet wird:

| Schritt | Zeitüberschreitung |
|--- |--- |
| Testen der Code-Qualität | 7 Tage |
| Sicherheitstests | 7 Tage |
| Leistungstests | 7 Tage |
| Genehmigungsantrag | 7 Tage |
| Planen der Bereitstellung für die Produktion | 7 Tage |
| CSE-Unterstützung | 7 Tage |

## Implementierungsprozess {#deployment-process}

Im folgenden Abschnitt wird beschrieben, wie AEM- und Dispatcher-Pakete in der Staging- und Produktionsphase bereitgestellt werden.

Cloud Manager lädt alle beim Build-Prozess generierten target/*.zip-Dateien in einen Speicherort hoch. Diese Artefakte werden in der Pipeline-Bereitstellungsphase von diesem Speicherort abgerufen.

Wenn Cloud Manager in produktionsfremden Topologien bereitgestellt wird, besteht das Ziel darin, die Implementierung so schnell wie möglich abzuschließen. Daher werden die Artefakte wie folgt auf allen Knoten gleichzeitig bereitgestellt:

1. Cloud Manager bestimmt für jedes Artefakt, ob es sich um ein AEM- oder Dispatcher-Paket handelt.
1. Cloud Manager entfernt alle Dispatcher aus dem Lastenausgleich, um die Umgebung während der Implementierung zu isolieren.

   Sofern nicht anders konfiguriert, können Sie die Load-Balancer-Änderungen in Entwicklungs- und Staging-Umgebungen überspringen, d. h. das Trennen und Anfügen in beiden Nicht-Produktions-Pipelines bei Entwicklungsumgebungen und in der Produktions-Pipeline bei Staging-Umgebungen.

   ![](assets/load_balancer.png)

   >[!NOTE]
   >
   >Diese Funktion wird voraussichtlich hauptsächlich von 1-1-1-Kunden verwendet.

1. Jedes AEM-Artefakt wird über Package Manager-APIs in jeder AEM-Instanz bereitgestellt, wobei Paketabhängigkeiten die Implementierungsreihenfolge bestimmen.

   Weitere Informationen dazu, wie Sie mit Paketen neue Funktionen installieren, Inhalte zwischen Instanzen übertragen und Repository-Inhalte sichern können, finden Sie unter „Arbeiten mit Paketen“.

   >[!NOTE]
   >
   >Alle AEM-Artefakte werden für Autor und Publisher bereitgestellt. Wenn knotenspezifische Konfigurationen erforderlich sind, sollten Ausführungsmodi genutzt werden. Weitere Informationen dazu, wie Sie mit Ausführungsmodi die AEM-Instanz für einen bestimmten Zweck anpassen können, finden Sie unter „Ausführungsmodi“.

1. Das Dispatcher-Artefakt wird wie folgt für jeden Dispatcher bereitgestellt:

   1. Aktuelle Konfigurationen werden gesichert und in einen temporären Speicherort kopiert.
   1. Alle Konfigurationen (mit Ausnahme der unveränderlichen Dateien) werden gelöscht. Weitere Informationen finden Sie unter „Verwalten von Dispatcher-Konfigurationen“. Mit diesem Schritt werden die Verzeichnisse gelöscht, damit keine verwaisten Dateien übrig bleiben.
   1. Das Artefakt wird in das `httpd`-Verzeichnis extrahiert. Unveränderliche Dateien werden nicht überschrieben. Alle Änderungen an unveränderlichen Dateien in Ihrem Git-Repository werden bei der Implementierung ignoriert. Diese Dateien bilden den Kern des AMS Dispatcher-Frameworks und können nicht geändert werden.
   1. Apache führt einen Konfigurationstest durch. Wenn keine Fehler gefunden werden, wird der Service neu geladen. Falls ein Fehler auftritt, werden die Konfigurationen aus der Sicherung wiederhergestellt, der Service wird neu geladen und der Fehler wird an Cloud Manager gemeldet.
   1. Jeder in der Pipelinekonfiguration angegebene Pfad wird ungültig oder aus dem Dispatcher-Cache entfernt.

   >[!NOTE]
   >Cloud Manager geht davon aus, dass das Dispatcher-Artefakt alle Dateien enthält. Alle Dispatcher-Konfigurationsdateien müssen im Git-Repository vorhanden sein. Fehlende Dateien oder Ordner führen zu Implementierungsfehlern.

1. Nach der erfolgreichen Implementierung aller AEM- und Dispatcher-Pakete auf allen Knoten werden die Dispatcher wieder zum Lastenausgleich hinzugefügt und die Implementierung wird abgeschlossen.

   >[!NOTE]
   >Sie können Änderungen am Load-Balancer in Entwicklungs- und Staging-Implementierungen überspringen, d. h. das Trennen und Anfügen in beiden produktionsfremden Pipelines bei Entwicklungsumgebungen und in der Produktions-Pipeline bei Staging-Umgebungen.

### Implementierung in der Produktionsphase {#deployment-production-phase}

Der Prozess zur Bereitstellung auf Produktionstopologien unterscheidet sich geringfügig, um die Auswirkungen auf AEM Sites-Besucher zu minimieren.

Produktionsimplementierungen nutzen im Allgemeinen die oben beschriebenen Schritte, aber auf rollierende Weise:

1. AEM-Pakete werden für den Autor bereitgestellt
1. dispatcher1 wird aus dem Lastenausgleich gelöst
1. Stellen Sie AEM Pakete für publish1 und das Dispatcher-Paket parallel zum Dispatcher1 bereit, um den Dispatcher-Cache zu leeren.
1. dispatcher1 wird in den Lastenausgleich zurückgesetzt
1. Sobald dispatcher1 wieder aktiv ist, wird dispatcher2 aus dem Lastenausgleich entfernt
1. Stellen Sie AEM Pakete für publish2 und das Dispatcher-Paket parallel zum Dispatcher2 bereit, um den Dispatcher-Cache zu leeren.
1. dispatcher2 wird in den Lastenausgleich zurückgesetzt
Dieser Vorgang wird fortgesetzt, bis die Implementierung alle Publisher und Dispatcher in der Topologie erreicht hat.
