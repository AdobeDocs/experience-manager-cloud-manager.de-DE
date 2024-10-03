---
title: Hinzufügen externer Repositorys in Cloud Manager (früher Adobe Experience Manager)
description: Erfahren Sie, wie Sie ein externes Repository zu Cloud Manager hinzufügen. Cloud Manager unterstützt die Integration mit GitHub-, GitLab- und Bitbucket-Repositorys.
source-git-commit: 054c214be3c8c6e8a8bd4691b70ae2098263ef5b
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 6%

---


# Hinzufügen externer Repositorys in Cloud Manager {#external-repositories}

Erfahren Sie, wie Sie ein externes Repository zu Cloud Manager hinzufügen. Cloud Manager unterstützt die Integration mit GitHub-, GitLab- und Bitbucket-Repositorys.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/release-notes/current.md#early-adoption) verfügbar.

## Externes Repository konfigurieren

Die Konfiguration eines externen Repositorys in Cloud Manager erfolgt in drei Schritten:

1. [Fügen Sie ein externes Repository hinzu](#add-external-repo), um es einem ausgewählten Programm hinzuzufügen.
1. Stellen Sie ein Zugriffstoken für das externe Repository bereit.
1. Validieren Sie die Eigentümerschaft des externen Repositorys.


## Externes Repository hinzufügen {#add-ext-repo}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/getting-started/navigation.md#my-programs-console) das Programm aus, mit dem Sie ein externes Repository verknüpfen möchten.


1. Wählen Sie im Seitenmenü unter **Dienste** das Symbol ![Ordner](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorys**.

   ![Die Seite &quot;Repositorys&quot;](/help/managing-code/assets/repositories-tab.png)

1. Klicken Sie in der rechten oberen Ecke der Seite **Repositorys** auf **Repository hinzufügen**.

1. Wählen Sie im Dialogfeld **Repository hinzufügen** die Option **Privates Repository** aus, um ein externes Git-Repository mit Ihrem Programm zu verknüpfen.

   ![Eigenes Repository hinzufügen](/help/managing-code/assets/repositories-private-repo-type.png)

1. Geben Sie in jedem Feld die folgenden Details zu Ihrem Repository an:

   | Feld | Beschreibung |
   | --- | --- |
   | **Repository-Name** | Erforderlich. Ein ausdrucksstarker Name für Ihr neues Repository. |
   | **Repository-URL** | Erforderlich. Die URL des Repositorys.<br><br> Wenn Sie ein von GitHub gehostetes Repository verwenden, muss der Pfad in `.git` enden.<br>Beispiel: *`https://github.com/org-name/repo-name.git`* (URL-Pfad dient nur zu Veranschaulichungszwecken).<br><br>Wenn Sie ein externes Repository verwenden, muss es das folgende URL-Pfadformat verwenden:<br>`https://git-vendor-name.com/org-name/repo-name.git`<br> oder <br>`https://self-hosted-domain/org-name/repo-name.git`<br> und mit Ihrem Git-Anbieter übereinstimmen. |
   | **Repository-Typ auswählen** | Erforderlich. Wählen Sie den von Ihnen verwendeten Repository-Typ aus: **GitHub**, **GitLab** oder **BitBucket**. Wenn der obige Repository-URL-Pfad den Namen des Git-Anbieters enthält, z. B. GitLab oder Bitbucket, ist der Repository-Typ bereits für Sie vorausgewählt. |
   | **Beschreibung** | Optional. Eine detaillierte Beschreibung des Repositorys. |

1. Wählen Sie **Speichern** aus, um das Repository hinzuzufügen.

1. Geben Sie im Dialogfeld **Validierung der Eigentümerschaft des privaten Repositorys** ein Zugriffstoken an, um die Eigentümerschaft des externen Repositorys zu validieren, sodass Sie darauf zugreifen können.

   ![Auswählen eines vorhandenen Zugriffstokens für ein Repository](/help/managing-code/assets/repositories-exisiting-access-token.png)
   *Auswählen eines vorhandenen Zugriffstokens für ein BitBucket-Repository*

   | Tokentyp | Beschreibung |
   | --- | --- |
   | **Vorhandenes Zugriffs-Token verwenden** | Wenn Sie bereits ein Repository-Zugriffstoken für Ihre Organisation bereitgestellt haben und Zugriff auf mehrere Repositorys haben, können Sie ein vorhandenes Token auswählen. Verwenden Sie die Dropdownliste **Token-Name** , um das Token auszuwählen, das Sie auf das Repository anwenden möchten. Fügen Sie andernfalls ein neues Zugriffstoken hinzu. |
   | **Neues Zugriffstoken hinzufügen** | **Repository-Typ: GitHub**<br> ・ Geben Sie im Textfeld **Token-Name** einen Namen für das Zugriffstoken ein, das Sie erstellen.<br> ・ Erstellen Sie ein persönliches Zugriffstoken, indem Sie die Anweisungen in der [GitHub-Dokumentation](https://docs.github.com/en/enterprise-server@3.14/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) befolgen.<br> ・ erforderliche Berechtigungen:<br>  ・ `Read access to metadata`.<br>  ・ `Read and write access to code and pull requests`.<br> ・ Fügen Sie im Feld **Zugriffstoken** das soeben erstellte Token ein. |
   |  | **Repository-Typ: GitLab**<br> ・ Geben Sie im Textfeld **Token-Name** einen Namen für das Zugriffstoken ein, das Sie erstellen.<br> ・ Erstellen Sie ein persönliches Zugriffstoken, indem Sie die Anweisungen in der [GitLab-Dokumentation](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) befolgen.<br> ・ erforderliche Berechtigungen:<br>  ・ `api`<br>  ・ `read_api`<br>  ・ `read_repository`<br>  ・ `write_repository`<br> ・ Fügen Sie im Feld **Zugriffstoken** das soeben erstellte Token ein. |
   |  | **Repository-Typ: Bitbucket**<br> ・ Geben Sie im Textfeld **Token-Name** einen Namen für das Zugriffstoken ein, das Sie erstellen.<br> ・ Erstellen Sie ein Repository-Zugriffstoken mithilfe der [Bitbucket-Dokumentation](https://support.atlassian.com/bitbucket-cloud/docs/create-a-repository-access-token/).<br> ・ erforderliche Berechtigungen:<br>  ・ `Read and write access to code and pull requests`. |

   >[!NOTE]
   >
   >Die Funktion &quot;**Neues Zugriffstoken hinzufügen**&quot; befindet sich derzeit in der Phase der frühen Teilnehmer. Zusätzliche Funktionen sind in Planung. Daher können sich die erforderlichen Berechtigungen für Zugriffstoken ändern. Darüber hinaus kann die Benutzeroberfläche für die Verwaltung von Tokens aktualisiert werden, möglicherweise einschließlich Funktionen wie Ablaufdaten von Token. Und automatisierte Prüfungen, um sicherzustellen, dass mit Repositorys verknüpfte Token gültig bleiben.

1. Klicken Sie auf **Validieren**.

Nach der Validierung kann das externe Repository verwendet werden und eine Verknüpfung zu einer Pipeline herstellen.

## Verknüpfen eines validierten externen Repositorys mit einer Pipeline {#validate-ext-repo}

1. Hinzufügen oder Bearbeiten einer Pipeline:
   * [Hinzufügen einer Produktions-Pipeline](/help/using/production-pipelines.md)
   * [Nicht-Produktions-Pipelines hinzufügen](/help/using/non-production-pipelines.md)
   * [Pipeline bearbeiten](/help/using/managing-pipelines.md#editing-pipelines)

   ![Quellcode-Repository der Pipeline und Git-Verzweigung](/help/managing-code/assets/pipeline-repo-gitbranch.png)
   *Dialogfeld &quot;Nicht-Produktions-Pipeline hinzufügen&quot;mit ausgewähltem Repository und Git-Verzweigung,*

1. Wählen Sie beim Hinzufügen oder Bearbeiten einer Pipeline zum Angeben des **Source-Code**-Speicherorts für die neue oder vorhandene Pipeline das zu verwendende externe Repository aus der Dropdownliste **Repository** aus.

1. Wählen Sie in der Dropdownliste **Git-Verzweigung** die Verzweigung als Quelle für die Pipeline aus.

1. Klicken Sie auf **Speichern**.


>[!TIP]
>
>Weitere Informationen zum Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/managing-code/managing-repositories.md).


## Einschränkungen

* Externe Repositorys können nicht mit Konfigurations-Pipelines verknüpft werden.
* Pipelines, die externe Repositorys verwenden (ausgenommen GitHub-gehostete Repositorys) und die Option **Deployment Trigger** [!UICONTROL **Bei Git-Änderungen**] werden Trigger nicht automatisch gestartet. Sie müssen manuell gestartet werden.
