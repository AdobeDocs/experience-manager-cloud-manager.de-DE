---
title: Hinzufügen externer Repositorys in Cloud Manager - Early Adopter
description: Erfahren Sie, wie Sie in Cloud Manager ein externes Repository hinzufügen. Cloud Manager unterstützt die Integration mit GitHub Enterprise-, GitLab- und Bitbucket-Repositorys.
exl-id: 4500cacc-5e27-4bbb-b8f6-5144dac7e6da
source-git-commit: 5ba12cdfa4a0d790561fd2f3da738bf697133bee
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 75%

---

# Hinzufügen externer Repositorys in Cloud Manager - Early Adopter {#external-repositories}

Erfahren Sie, wie Sie in Cloud Manager ein externes Repository hinzufügen. Cloud Manager unterstützt die Integration mit GitHub Enterprise-, GitLab- und Bitbucket-Repositorys.

>[!NOTE]
>
>Die in diesem Artikel beschriebenen Funktionen sind nur über das Early-Adoption-Programm verfügbar. Weitere Informationen und die Möglichkeit, sich als frühzeitiger Anwender anzumelden, finden Sie unter [Eigenes Git mitbringen](/help/release-notes/current.md#gitlab-bitbucket).

## Konfigurieren eines externen Repositorys

Die Konfiguration eines externen Repositorys in Cloud Manager erfolgt in drei Schritten:

1. Fügen Sie einem ausgewählten Programm [ein externes Repository hinzu](#add-external-repo).
1. Stellen Sie ein Zugriffs-Token für das externe Repository bereit.
1. Überprüfen Sie die Eigentümerschaft des privaten GitHub-Repositorys.
1. [Webhook konfigurieren](#configure-webhook) zu einem externen Repository.


## Hinzufügen eines externen Repositorys {#add-ext-repo}

>[!NOTE]
>
>Externe Repositorys können nicht mit Konfigurations-Pipelines verknüpft werden.

<!-- THIS BULLET REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release. THEY CAN NOW START AUTOMATICALLY>
* Pipelines using external repositories (excluding GitHub-hosted repositories) and the **Deployment Trigger** option [!UICONTROL **On Git Changes**], triggers are not automatically started. They must be manually started. -->


1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/getting-started/navigation.md#my-programs-console)** das Programm aus, mit dem Sie ein externes Repository verknüpfen möchten.

1. Klicken Sie im Seitenmenü unter **Programm** auf ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorys**.

   ![Die Seite „Repositorys“](/help/managing-code/assets/repositories-tab.png)

1. Klicken Sie oben rechts auf der Seite **Repositorys** auf **Repository hinzufügen**.

1. Wählen Sie im Dialogfeld **Repository hinzufügen** die Option **Privates Repository** aus, um ein externes Git-Repository mit Ihrem Programm zu verknüpfen.

   ![Eigenes Repository hinzufügen](/help/managing-code/assets/repositories-private-repo-type.png)

1. Geben Sie in jedem Feld jeweils die folgenden Details zu Ihrem Repository an:

   | Feld | Beschreibung |
   | --- | --- |
   | **Repository-Name** | Erforderlich. Ein aussagekräftiger Name für Ihr neues Repository. |
   | **Repository-URL** | Erforderlich. Die URL des Repositorys.<br><br>Wenn Sie ein von GitHub gehostetes Repository verwenden, muss der Pfad mit `.git` enden.<br>Beispiel: *`https://github.com/org-name/repo-name.git`* (URL-Pfad dient nur zu Illustrationszwecken).<br><br>Wenn Sie ein externes Repository verwenden, muss es das folgende URL-Pfadformat verwenden:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> oder <br>`https://self-hosted-domain/org-name/repo-name.git`<br>. Außerdem muss es mit Ihrem Git-Anbieter übereinstimmen. |
   | **Repository-Typ auswählen** | Erforderlich. Wählen Sie den verwendeten Repository-Typ aus:<ul><li>**GitHub** (GitHub Enterprise und die selbst gehostete Version von GitHub)</li><li>**GitLab** (sowohl `gitlab.com` als auch die selbst gehostete GitLab-Version) </li><li>**Bitbucket** (nur `bitbucket.org` (Cloud-Version) wird unterstützt. Die selbst gehostete Version von Bitbucket wird seit dem 15. Februar 2024 nicht mehr unterstützt.)</li></ul>Wenn der obige Repository-URL-Pfad den Namen des Git-Anbieters enthält, z. B. GitLab oder Bitbucket, ist der Repository-Typ bereits für Sie vorausgewählt. |
   | **Beschreibung** | Optional. Eine längere Beschreibung des Repositorys. |

1. Wählen Sie **Speichern**, um das Repository hinzuzufügen.

1. Geben Sie im Dialogfeld **Validierung der Eigentümerschaft eines privaten Repositorys** ein Zugriffs-Token an, um die Eigentümerschaft des externen Repositorys zu validieren, sodass Sie darauf zugreifen können.

   ![Auswählen eines vorhandenen Zugriffs-Tokens für ein Repository](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Auswählen eines vorhandenen Zugriffs-Tokens für ein Bitbucket-Repository.*

   | Token-Typ | Beschreibung |
   | --- | --- |
   | **Vorhandenes Zugriffs-Token verwenden** | Wenn Sie bereits ein Repository-Zugriffs-Token für Ihre Organisation bereitgestellt haben und Zugriff auf mehrere Repositorys haben, können Sie ein vorhandenes Token auswählen. Verwenden Sie die Dropdown-Liste **Tokenname**, um das Token auszuwählen, das Sie auf das Repository anwenden möchten. Fügen Sie andernfalls ein neues Zugriffs-Token hinzu. |
   | **Neues Zugriffs-Token hinzufügen** | **Repository-Typ: GitHub Enterprise**<br><ul><li> Geben Sie im Textfeld **Token-Name** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<li>Erstellen Sie ein persönliches Zugriffs-Token, indem Sie die Anweisungen in der [GitHub-Dokumentation](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) befolgen.<li>Erforderliche Berechtigungen für das GitHub Enterprise Personal Access Token (PAT)<br>Diese Berechtigungen stellen sicher, dass Cloud Manager Pull-Anforderungen validieren, Commit-Statusprüfungen verwalten und auf erforderliche Repo-Details zugreifen kann.<br>Wenn Sie den Pfad in GitHub Enterprise generieren, stellen Sie sicher, dass er die folgenden Repository-Berechtigungen enthält:<ul><li>Pull-Anfrage (Lesen und Schreiben)<li>Commit-Status (Lesen und Schreiben)<li>Repository-Metadaten (schreibgeschützt)</li></li></ul></li></ul></ul></ul><ul><li>Fügen Sie im Feld **Zugriffs-Token** das soeben erstellte Token ein. |
   | | **Repository-Typ: GitLab**<ul><li>Geben Sie im Textfeld **Token-Name** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<li>Erstellen Sie ein persönliches Zugriffs-Token, indem Sie die Anweisungen in der [GitLab-Dokumentation](https://docs.gitlab.com/user/profile/personal_access_tokens/) befolgen.<li>Erforderliche Berechtigungen für das GitLab Personal Access Token (PAT)<br>Diese Bereiche ermöglichen Cloud Manager den Zugriff auf Repository-Daten und Benutzerinformationen, die für die Validierung und Webhook-Integration erforderlich sind.<br>Wenn Sie den Pfad in GitLab generieren, stellen Sie sicher, dass er die folgenden Token-Bereiche enthält:<ul><li>API<li>read_user</li></li></ul></li></li></ul></ul></ul><ul><li>Fügen Sie im Feld **Zugriffs-Token** das soeben erstellte Token ein. |
   | | **Repository-Typ: Bitbucket**<ul><li>Geben Sie im Textfeld **Token-Name** einen Namen für das Zugriffs-Token ein, das Sie erstellen.<li>Erstellen Sie ein Repository-Zugriffs-Token mithilfe der [Bitbucket-Dokumentation](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<li>Erforderliche Berechtigungen für den Bitbucket Personal Access Token (PAT)<br>Diese Berechtigungen ermöglichen Cloud Manager den Zugriff auf Repository-Inhalte, die Verwaltung von Pull-Anfragen und die Konfiguration von oder Reaktion auf Webhook-Ereignisse.<br>Wenn Sie das App-Kennwort in Bitbucket erstellen, stellen Sie sicher, dass es die folgenden erforderlichen App-Kennwortberechtigungen enthält:<ul><li>Repository (schreibgeschützt)<li>Pull-Anfragen (Lesen und Schreiben)<li>Webhooks (Lesen und Schreiben)</li></li></ul></li></li></ul></ul></ul><ul><li>Fügen Sie im Feld **Zugriffs-Token** das soeben erstellte Token ein. |

   >[!NOTE]
   >
   >Die Funktion „**Neues Zugriffs-Token hinzufügen**“ befindet sich derzeit in der Early-Adopter-Phase. Zusätzliche Funktionen sind in Planung. Daher können sich die erforderlichen Berechtigungen für Zugriffs-Token ändern. Darüber hinaus kann die Benutzeroberfläche für die Verwaltung von Token aktualisiert werden, möglicherweise einschließlich Funktionen wie Ablaufdaten von Token. Dazu gehören auch automatisierte Prüfungen, um sicherzustellen, dass mit Repositorys verknüpfte Token gültig bleiben.

1. Klicken Sie auf **Überprüfen**.

Nach der Überprüfung kann das externe Repository verwendet und mit einer Pipeline verknüpft werden.

## Verknüpfen eines validierten externen Repositorys mit einer Pipeline {#validate-ext-repo}

1. Hinzufügen oder Bearbeiten einer Pipeline:
   * [Hinzufügen einer Produktions-Pipeline](/help/using/production-pipelines.md#adding-production-pipeline)
   * [Hinzufügen einer produktionsfremden Pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline)
   * [Bearbeiten einer Pipeline](/help/using/managing-pipelines.md#editing-pipelines)

   ![Quell-Code-Repository der Pipeline und Git-Verzweigung](/help/managing-code/assets/pipeline-repo-gitbranch.png)
   *Dialogfeld „Produktionsfremde Pipeline hinzufügen“ mit ausgewähltem Repository und Git-Verzweigung*

1. Wählen Sie beim Hinzufügen oder Bearbeiten einer Pipeline zum Angeben des **Quell-Code**-Speicherorts für die neue oder vorhandene Pipeline das zu verwendende externe Repository aus der Dropdown-Liste **Repository** aus.

1. Wählen Sie in der Dropdown-Liste **Git-Verzweigung** die Verzweigung als Quelle für die Pipeline aus.

1. Klicken Sie auf **Speichern**.


>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/managing-code/managing-repositories.md).

## Konfigurieren eines Webhooks für externe Repositorys {#configure-webhook}

Mit Cloud Manager können Sie Webhooks für externe Git-Repositorys konfigurieren, die Sie hinzugefügt haben. Siehe [Hinzufügen eines externen Repositorys](#add-ext-repo). Diese Webhooks ermöglichen es Cloud Manager, Ereignisse zu empfangen, die sich auf verschiedene Aktionen in Ihrer Git-Anbieterlösung beziehen.

Mit Webhooks kann Cloud Manager beispielsweise Aktionen auf Grundlage von Ereignissen wie den folgenden auslösen:

* Erstellung einer Pull-Anfrage (Pull Request, PR): Initiiert die PR-Validierungsfunktionalität.
* Push-Ereignisse: Startet Pipelines, wenn der Trigger „Bei Git-Commit“ aktiviert ist.
* Künftige kommentarbasierte Aktionen: Ermöglicht Workflows, etwa die direkte Bereitstellung aus einer PR in einer schnellen Entwicklungsumgebung (Rapid Development Environment, RDE).

Die Webhook-Konfiguration ist für auf `GitHub.com` gehostete Repositorys nicht erforderlich, da Cloud Manager direkt über die GitHub-App integriert wird.

Für alle anderen externen Repositorys, die mit einem Zugriffstoken integriert werden, wie GitHub Enterprise, GitLab und Bitbucket, ist eine Webhook-Konfiguration verfügbar und muss manuell eingerichtet werden.

**So konfigurieren Sie einen Webhook für ein externes Repository:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/getting-started/navigation.md#my-programs-console)** das Programm aus, mit dem ein Webhook für ein externes Repository konfiguriert werden soll.

1. Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.

1. Klicken Sie im linken Seitenmenü unter der Überschrift **Programm** auf ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorys**.

1. Wählen Sie auf der **Repositorys** mithilfe der Spalte **Typ** das gewünschte Repository und klicken Sie dann daneben auf ![Auslassungspunkte – Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).

   ![Option „Webhook konfigurieren“ im Dropdown-Menü für ein ausgewähltes Repository](/help/managing-code/assets/repository-config-webhook.png)

1. Klicken Sie im Dropdown-Menü auf **Webhook konfigurieren**.

   ![Dialogfeld „Webhook konfigurieren“](/help/managing-code/assets/config-webhook.png)

1. Gehen Sie im Dialogfeld **Webhook konfigurieren** wie folgt vor:

   1. Klicken Sie neben dem Feld **Webhook-URL** auf ![Kopieren-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Fügen Sie die URL in eine einfache Textdatei ein. Die kopierte URL ist für die Webhook-Einstellungen Ihres Git-Anbieters erforderlich.
   1. Klicken Sie neben dem Feld **Webhook-Geheimnis** auf **Generieren** und dann auf ![Kopieren-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg).
Fügen Sie das Geheimnis in eine einfache Textdatei ein. Das kopierte Geheimnis ist für die Webhook-Einstellungen Ihres Git-Anbieters erforderlich.
1. Klicken Sie auf **Schließen**.
1. Navigieren Sie zu Ihrer Git-Anbieterlösung (GitHub Enterprise, GitLab oder Bitbucket).

   Alle Details zur Webhook-Konfiguration und den für jeden Anbieter erforderlichen Ereignissen finden Sie unter [Hinzufügen eines externen Repositorys](#add-ext-repo). Sehen Sie sich die Tabelle unter Schritt 8 an.

1. Gehen Sie in der Lösung zum Abschnitt mit den **Webhook**-Einstellungen.
1. Fügen Sie die zuvor kopierte Webhook-URL in das URL-Textfeld ein.
   1. Ersetzen Sie den Abfrageparameter `api_key` in der Webhook-URL durch Ihren eigenen echten API-Schlüssel.

      Um einen API-Schlüssel zu generieren, müssen Sie ein Integrationsprojekt in Adobe Developer Console erstellen. Ausführliche Informationen finden Sie unter [Erstellen eines API-Integrationsprojekts](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/create-api-integration/).

1. Fügen Sie das zuvor kopierte Webhook-Geheimnis in das Textfeld **Geheimnis** (oder **Geheimer Schlüssel** oder **Geheimes Token**) ein.
1. Konfigurieren Sie den Webhook so, dass die erforderlichen Ereignisse gesendet werden, die von Cloud Manager erwartet werden.

   | Repository | Erforderliche Webhook-Ereignisse |
   | --- | --- |
   | GitHub Enterprise | Diese Ereignisse ermöglichen es Cloud Manager, auf GitHub-Aktivitäten zu reagieren, z. B. die Validierung von Pull-Anforderungen, Push-basierte Trigger für Pipelines oder Edge Delivery Services-Codesynchronisierung.<br>Stellen Sie sicher, dass der Webhook für die folgenden erforderlichen Webhook-Ereignisse auf Trigger eingerichtet ist:<ul><li>Pull-Anfragen<li>Push-Benachrichtigungen<li>Anmerkungen zu Problemen</li></li></li></ul></ul></ul> |
   | GitLab | Diese Webhook-Ereignisse ermöglichen es Cloud Manager, Pipelines beim Pushen von Trigger oder bei der Übermittlung einer Zusammenführungsanfrage zu konfigurieren. Sie verfolgen außerdem Kommentare im Zusammenhang mit der Validierung von Pull-Anfragen (durch Notizereignisse).<br>Stellen Sie sicher, dass der Webhook für die folgenden erforderlichen Webhook-Ereignisse auf Trigger eingerichtet ist<ul><li>Push-Ereignisse<li>Zusammenführen von Anfrageereignissen<li>Notizereignisse</li></li></li></ul></ul></ul> |
   | Bitbucket | Diese Ereignisse stellen sicher, dass Cloud Manager Pull-Anforderungen validieren, auf Code-Push-Benachrichtigungen reagieren und mit Kommentaren zur Pipeline-Koordinierung interagieren kann.<br>Stellen Sie sicher, dass der Webhook für die folgenden erforderlichen Webhook-Ereignisse auf Trigger eingerichtet ist<ul><li>Pull-Anfrage: Erstellt<li>Pull-Anfrage: Aktualisiert<li>Pull-Anfragen: Zusammengeführt<li>Pull-Anfrage: Kommentar<li>Repository: Push</li></li></li></ul></ul></ul> |

### Validierung von Pull-Anfragen mit Webhooks

Wenn Webhooks korrekt konfiguriert sind, löst Cloud Manager Trigger automatisch Pipeline-Ausführungen oder PR-Validierungsprüfungen für Ihr Repository aus.

Es zeigt sich das folgende Verhalten:

* **GitHub Enterprise**

  Wenn die Prüfung erstellt wird, sieht sie wie der folgende Screenshot aus. Der wesentliche Unterschied zu `GitHub.com` besteht darin, dass `GitHub.com` einen Check-Run verwendet, während GitHub Enterprise (unter Verwendung von persönlichen Zugriffstoken) einen Commit-Status generiert:

  ![Commit-Status, um den PR-Validierungsprozess auf GitHub Enterprise anzugeben](/help/managing-code/assets/repository-webhook-github-pr-validation.png)

* **Bitbucket**

  Wenn die Validierung der Code-Qualität ausgeführt wird:

  ![Status während der Ausführung der Validierung der Code-Qualität](/help/managing-code/assets/repository-webhook-bitbucket1.png)

  Verwendet den Commit-Status zum Tracking des PR-Validierungsfortschritts. Im folgenden Fall zeigt der Screenshot, was passiert, wenn eine Validierung der Code-Qualität aufgrund eines Kundenproblems fehlschlägt. Es wird ein Kommentar mit detaillierten Fehlerinformationen hinzugefügt und eine Commit-Prüfung erstellt, die den Fehler anzeigt (rechts sichtbar):

  ![Validierungsstatus der Pull-Anfrage für Bitbucket](/help/managing-code/assets/repository-webhook-bitbucket2.png)

* **GitLab**

  GitLab-Interaktionen basieren ausschließlich auf Kommentaren. Bei Start der Validierung wird ein Kommentar hinzugefügt. Nach Abschluss der Validierung (ob erfolgreich oder fehlgeschlagen) wird der ursprüngliche Kommentar entfernt und durch einen neuen Kommentar mit Validierungsergebnissen oder Fehlerdetails ersetzt.

  Wenn die Validierung der Code-Qualität ausgeführt wird:

  ![Wenn die Validierung der Code-Qualität ausgeführt wird](/help/managing-code/assets/repository-webhook-gitlab1.png)

  Wenn die Validierung der Code-Qualität abgeschlossen ist:

  ![Wenn die Validierung der Code-Qualität abgeschlossen ist](/help/managing-code/assets/repository-webhook-gitlab2.png)

  Wenn die Validierung der Code-Qualität mit einem Fehler fehlschlägt:

  ![Wenn die Validierung der Code-Qualität mit einem Fehler fehlschlägt](/help/managing-code/assets/repository-webhook-gitlab3.png)

  Wenn die Validierung der Code-Qualität aufgrund von Kundenproblemen fehlschlägt:

  ![Wenn die Validierung der Code-Qualität aufgrund von Kundenproblemen fehlschlägt](/help/managing-code/assets/repository-webhook-gitlab4.png)


## Fehlerbehebung bei Webhook-bezogenen Problemen

* Stellen Sie sicher, dass die Webhook-URL einen gültigen API-Schlüssel enthält.
* Vergewissern Sie sich, dass Webhook-Ereignisse in Ihren Git-Anbietereinstellungen korrekt konfiguriert sind.
* Wenn die PR-Validierung oder die Pipeline-Trigger nicht funktionieren, stellen Sie sicher, dass das Webhook-Geheimnis sowohl in Cloud Manager als auch bei Ihrem Git-Anbieter auf dem neuesten Stand ist.