---
title: Benutzerdefinierte Berechtigungen
description: Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 99%

---

# Benutzerdefinierte Berechtigungen {#custom-permissions}

Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.

## Einführung {#introduction}

Cloud Manager bietet eine Reihe vordefinierter Rollen, die den Zugriff auf verschiedene Cloud Manager-Funktionen steuern:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwicklerin oder Entwickler

Mit benutzerdefinierten Berechtigungen können Benutzende neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um für Cloud Manager-Benutzende den Zugriff auf Programme, Pipelines und Umgebungen zu beschränken.

>[!TIP]
>
>Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [Rollenbasierte Berechtigungen.](/help/requirements/role-based-permissions.md).

## Verwenden benutzerdefinierter Berechtigungen {#using}

Für das Erstellen und Verwenden eigener, benutzerdefinierter Berechtigungen sind drei Schritte erforderlich:

1. [Erstellen eines neuen Produktprofils](#create).
1. [Zuweisen benutzerdefinierter Berechtigungen zu dem neuen Produktprofil](#assign-permissions).
1. [Zuweisen von Benutzenden zu dem neuen Produktprofil](#assign-users).

In diesem Abschnitt werden diese Schritte beschrieben. Möglicherweise helfen Ihnen die Informationen in den Abschnitten [Begriffe](#terms) und [Konfigurierbare Berechtigungen](#configurable-permissions) bei der Erstellung Ihrer eigenen benutzerdefinierten Berechtigungen.

>[!NOTE]
>
>Sie müssen über Produktadministrator-Berechtigungen in der Admin Console verfügen, um neue Profile erstellen und Cloud Manager-Berechtigungen verwalten zu können.

### Erstellen eines neuen Produktprofils {#create}

Erstellen Sie zunächst ein neues Produktprofil, dem Sie benutzerdefinierte Berechtigungen zuweisen können.

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an.

1. Wählen Sie das Produkt **AEM Managed Services** aus.

1. Suchen Sie nach einer Instanz, deren Name dem Muster `*-cloud-manager` entspricht, und klicken Sie darauf, um Benutzende und Berechtigungen zu verwalten.

1. Sie werden zur Registerkarte **Produkte** der Admin Console geleitet, auf der Sie Benutzende und Berechtigungen für Cloud Manager verwalten können. Klicken Sie in der Admin Console auf **Neues Profil**.

![Schaltfläche „Neues Profil“](/help/assets/admin-console-new-profile.png)

1. Geben Sie die allgemeinen Details zum Profil an.

   * **Name des Produktprofils** – Ein aussagekräftiger Name des Profils
   * **Anzeigename**: Ein abgekürzter Name, der auf der Benutzeroberfläche angezeigt wird (optional)
   * **Beschreibung**: Eine informative Beschreibung des Profils, das seinen Zweck erklärt (optional)
   * **Benutzende per E-Mail benachrichtigen**: Wenn diese Option aktiviert ist, werden Benutzende per E-Mail benachrichtigt, wenn sie zu diesem Profil hinzugefügt oder daraus entfernt werden.

1. Klicken Sie auf **Speichern**.

Das neue Produktprofil wird gespeichert und ist in der Liste der Produktprofile in der Admin Console sichtbar.

### Zuweisen benutzerdefinierter Berechtigungen zum neuen Produtkprofil {#assign-permissions}

Nachdem Sie ein neues Produktprofil erstellt haben, können Sie ihm benutzerdefinierte Berechtigungen zuweisen.

1. Klicken Sie in der Admin Console auf den Namen des [neuen Produktprofils, das Sie soeben erstellt haben](#create).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Berechtigungen**, um eine Liste bearbeitbarer Berechtigungen anzuzeigen.

   ![Bearbeitbare Berechtigungen](/help/assets/permissions-tab.png)

1. Klicken Sie auf den Link **Bearbeiten** einer Berechtigung, um sie zu bearbeiten.

1. Das Fenster **Berechtigungen bearbeiten** wird geöffnet.
   * Die Berechtigung, die Sie im vorherigen Schritt ausgewählt haben, ist in der linken Spalte ausgewählt.
   * Die für die Zuweisung der Berechtigung verfügbaren Berechtigungselemente befinden sich in der mittleren Spalte **Verfügbare Berechtigungselemente**.
   * Die zugewiesenen Berechtigungselemente befinden sich in der rechten Spalte mit der Bezeichnung **Eingeschlossene Berechtigungselemente**.

   ![Berechtigungselemente bearbeiten](/help/assets/edit-permission-items.png)

1. Klicken Sie auf das Pluszeichen (`+`) neben dem Berechtigungselement, um dieses der Spalte **Eingeschlossene Berechtigungselemente** hinzuzufügen. Klicken Sie bei Bedarf auf das Symbol `i` neben einem Berechtigungselement, um mehr darüber zu erfahren.

1. Klicken Sie oben in der Spalte **Verfügbare Berechtigungen** auf **Alle hinzufügen**, um alle Berechtigungen hinzuzufügen. Klicken Sie auf **Alle entfernen**, um alle zuvor ausgewählten Berechtigungen zu entfernen.

1. Klicken Sie auf **Speichern**, wenn Sie die Berechtigungselemente für Ihr neues Produktprofil definiert haben.

Ihr neues Produktprofil wird jetzt mit den benutzerdefinierten Berechtigungen gespeichert.

### Zuweisen von Benutzenden zum neuen Produktprofil {#assign-users}

Sie können dem neuen Produktprofil, das Sie mit benutzerdefinierten Berechtigungen erstellt haben, jetzt Benutzende zuweisen.

1. Klicken Sie in der Admin Console auf den Namen des [neuen Produktprofils, dem Sie soeben benutzerdefinierte Berechtigungen zugewiesen haben](#assign-permissions).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Benutzer**.

1. Klicken Sie auf die Schaltfläche **Benutzer hinzufügen** aus und weisen Sie Ihrem neuen Produktprofil Benutzende mit benutzerdefinierten Berechtigungen zu.

Weitere Informationen zum Verwenden der Admin Console finden Sie im Abschnitt **Hinzufügen von Benutzenden und Benutzergruppen zu einem Produktprofil** des Dokuments [Verwalten von Produktprofilen für Unternehmensbenutzende](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html).

## Konfigurierbare Berechtigungen {#configurable-permissions}

Zum Erstellen benutzerdefinierter Profile stehen folgende Berechtigungen zur Verfügung.

| Berechtigung | Beschreibung |
| --- | --- |
| `Program Access` | Benutzenden den Zugriff auf Programme gewähren |
| `Program Edit` | Benutzenden erlauben, Programme zu bearbeiten |
| `Pipeline Create` | Benutzenden erlauben, neue Pipelines zu erstellen |
| `Pipeline Delete` | Benutzenden erlauben, Pipelines zu löschen |
| `Pipeline Edit` | Benutzenden erlauben, Pipelines zu bearbeiten |
| `Production Deployments Approve/Reject` | Benutzenden erlauben, einen Produktionsbereitstellungsschritt zu genehmigen oder abzulehnen |
| `Pipeline Executions Cancel` | Benutzenden erlauben, Pipeline-Ausführungen abzubrechen |
| `Pipeline Executions Start` | Benutzenden erlauben, neue Pipeline-Ausführungen zu starten |
| `Override/Reject Important Metric Failures` | Benutzenden erlauben, wichtige Metrikfehler zu überschreiben/abzulehnen |
| `Production Deployments Schedule` | Benutzenden erlauben, einen Produktionsbereitstellungsschritt zu planen |
| `Repository Info Access` | Benutzenden erlauben, auf Repository-Informationen zuzugreifen und ein Kennwort für den Zugriff zu erstellen |
| `Repository Create` | Benutzenden erlauben, neue Git-Repositorys zu erstellen |
| `Repository Delete` | Benutzenden erlauben, Git-Repositorys zu löschen |
| `Repository Edit` | Benutzenden erlauben, Git-Repositorys zu bearbeiten |
| `Repository Code Generate` | Benutzenden erlauben, Projekte aus einem Archetyp zu generieren |
| `Content Copy Manage` | Benutzenden erlauben, Vorgänge zum Kopieren von Inhalten zu verwalten |

### Berechtigungen auf Unternehmensebene {#organization-level}

Berechtigungen auf Unternehmensebene werden immer auf alle Programme in einem Unternehmen angewendet.

Ein Beispiel für eine Berechtigung auf Unternehmensebene in Cloud Manager ist **Zugriff auf Repository-Informationen**. Mit dieser Berechtigung können Benutzende Benutzernamen, Kennwort und Repository-URL generieren, um auf Kundenprojekte zuzugreifen und zu diesen beizutragen. Während Benutzername und Kennwort für alle Repositorys im Unternehmen gleich bleiben, verfügt jedes Programm über eine eindeutige Repository-URL.

Weitere Informationen finden Sie im Dokument [Quell-Code-Repository](/help/requirements/source-code-repository.md).

## Begriffe {#terms}

Folgende Begriffe werden beim Erstellen und Verwalten benutzerdefinierter Berechtigungen und vordefinierter Rollen verwendet.

| Begriff | Beschreibung |
| --- | --- |
| Vordefinierte Berechtigungen | Vordefinierte Rollen wie **Geschäftseigentümer** und **Bereitstellungs-Manager**. zur Steuerung verschiedener Cloud Manager-Funktionen. Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [Rollenbasierte Berechtigungen.](/help/requirements/role-based-permissions.md). |
| Benutzerdefinierte Berechtigungen | Cloud Manager-Funktionen, mit denen Benutzende Berechtigungsprofile erstellen können, um Rollen zur Verwaltung unterstützter Cloud Manager-Funktionen zu definieren |
| Berechtigungsprofil | Wird in der Admin Console zur Verwaltung konfigurierbarer Berechtigungen erstellt, die für Benutzende gelten, die Teil des Berechtigungsprofils sind |
| Konfigurierbare Berechtigung | Cloud Manager-Berechtigungen, die im Berechtigungsprofil konfiguriert werden können |
| Berechtigungselement | Eine Programm-, Umgebungs- oder Pipeline-Ressource, auf die eine Berechtigung angewendet werden kann |

Berechtigungselemente beziehen sich auf den Anwendungsumfang der Berechtigungen. In der Regel handelt es sich um Folgendes.

| Berechtigungselementtyp | Beispiel | Beschreibung |
| --- | --- | --- |
| Unternehmen | Unternehmen:FirmaA | Alle anwendbaren Ressourcen eines Unternehmens. Eine Ressource kann ein Programm, eine Umgebung oder eine Pipeline sein. Wenn Benutzende ein Unternehmen für eine Berechtigung hinzufügen, erhalten auch alle neuen Ressourcen in diesem Unternehmen diese Berechtigung. |
| Programm | Programm A | Alle anwendbaren Ressourcen eines Programms. |
| Umgebung | Programm A : Umgebung | In einer bestimmten Umgebung anwendbar. |
| Pipeline | Programm A : Pipeline | Gilt für eine bestimmte Pipeline. |

## Einschränkungen {#limitations}

Beachten Sie bei der Verwendung benutzerdefinierter Berechtigungen die folgenden Einschränkungen:

* Zur Erstellung benutzerdefinierter Profile ist ein [begrenzter Satz an Berechtigungen verfügbar](#configurable-permissions).
* Bei Ressourcen wie Programm, Umgebung, Pipeline usw., die in Cloud Manager erstellt wurden, kann es bis zu zwei Minuten dauern, bis die Admin Console zur Berechtigungskonfiguration angezeigt wird.
* In seltenen Fällen, in denen ein benutzerdefinierter Berechtigungsdienst nicht reagiert, sind vordefinierte Profile weiterhin verfügbar und Benutzende in vordefinierten Profilen haben weiterhin darauf Zugriff.

## Häufig gestellte Fragen {#faq}

### Welche Berechtigungsprofile sind vordefinierte Berechtigungsprofile?

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwicklerin oder Entwickler

Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [Rollenbasierte Berechtigungen.](/help/requirements/role-based-permissions.md).

### Was passiert mit vordefinierten Berechtigungsprofilen bei der Einführung in benutzerdefinierte Profile?

Die standardmäßigen Produktprofile und Cloud Manager-Rollen funktionieren weiterhin wie zuvor.

### Kann ich vordefinierte Berechtigungsprofile bearbeiten?

Nein, Standardprofile können nicht bearbeitet werden. Sie können keine Berechtigungen zum standardmäßigen Berechtigungsprofil hinzufügen oder welche daraus entfernen. Sie können nur Benutzende zu vordefinierten Profilen hinzufügen oder daraus entfernen.

### Sollte ich vordefinierte Berechtigungsprofile löschen, wenn benutzerdefinierte Profile verfügbar sind?

Vordefinierte Berechtigungsprofile dürfen nicht aus der Admin Console gelöscht werden.

### Kann ich Benutzende zu mehreren Berechtigungsprofilen hinzufügen?

Ja, eine Person kann Teil mehrerer Profile sein, einschließlich vordefinierter und benutzerdefinierter Berechtigungsprofile. Wenn eine Person mehreren Profilen zugewiesen wird, stehen ihr die kombinierten Berechtigungen aus allen zugewiesenen Berechtigungsprofilen zur Verfügung.

### Was passiert, wenn eine Person berechtigt ist, eine Umgebung/Pipeline zu bearbeiten, aber keinen Zugriff auf ein Programm hat, das die Umgebung/Pipeline enthält?

In diesem Szenario kann die Person nicht auf die Umgebung oder Pipeline zugreifen, wenn sie nicht über die Berechtigungen für den **Programmzugriff** auf die Umgebung oder Pipeline verfügt.

### Was passiert, wenn ich sowohl AEM as a Cloud Service als auch AMS-Programme in derselben IMS-Organisation habe? Kann ich Berechtigungen von einem Profil aus verwalten? {#ams-and-aemaacs}

Erstellen Sie ein separates Profil für jeden Produkttyp. Das heißt, eines für AEM as a Cloud Service und eines für Adobe Managed Services oder AMS.
