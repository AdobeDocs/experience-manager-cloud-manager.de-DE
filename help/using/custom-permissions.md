---
title: Benutzerdefinierte Berechtigungen
description: Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: 16eef51d86647ae4f2515f3f3c4cb2d15e948854
workflow-type: tm+mt
source-wordcount: '1474'
ht-degree: 100%

---

# Benutzerdefinierte Berechtigungen {#custom-permissions}

Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.

## Einführung {#introduction}

Cloud Manager bietet eine Reihe vordefinierter Rollen, die den Zugriff auf verschiedene Cloud Manager-Funktionen steuern:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

Mit benutzerdefinierten Berechtigungen können Benutzende neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.

>[!TIP]
>
>Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [Rollenbasierte Berechtigungen.](/help/requirements/role-based-permissions.md)

## Verwenden benutzerdefinierter Berechtigungen {#using}

Um eigene, benutzerdefinierte Berechtigungen zu erstellen und zu verwenden, sind drei Schritte erforderlich:

1. [Ein neues Produktprofil erstellen.](#create)
1. [Dem neuen Produktprofil benutzerdefinierte Berechtigungen zuweisen.](#assign-permissions)
1. [Dem neuen Produktprofil Benutzende zuweisen.](#assign-users)

In diesem Abschnitt werden diese Schritte beschrieben. Möglicherweise helfen Ihnen die Informationen unter [Begriffe](#terms) und [Konfigurierbare Berechtigungen](#configurable-permissions) bei der Erstellung Ihrer eigenen benutzerdefinierten Berechtigungen.

>[!NOTE]
>
>Sie müssen über Produktadministrator-Berechtigungen in Admin Console verfügen, um neue Profile erstellen und Cloud Manager-Berechtigungen verwalten zu können.

### Erstellen eines neuen Produktprofils {#create}

Sie müssen zunächst ein neues Produktprofil erstellen, bevor Sie benutzerdefinierte Berechtigungen zuweisen können.

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an.

1. Wählen Sie das Produkt **AEM Managed Services** aus.

1. Suchen Sie nach einer Instanz, deren Name dem Muster `*-cloud-manager` entspricht, und tippen oder klicken Sie darauf, um Benutzende und Berechtigungen zu verwalten.

1. Sie werden zur Registerkarte **Produkte** der Admin Console geleitet, auf der Sie Cloud Manager-Benutzende und Berechtigungen verwalten können. Tippen oder klicken Sie in der Admin Console auf **Neues Profil**.

![Schaltfläche „Neues Profil“](/help/assets/admin-console-new-profile.png)

1. Geben Sie die allgemeinen Details zum Profil an.

   * **Name des Produktprofils** – Ein aussagekräftiger Name des Profils
   * **Anzeigename** – Ein abgekürzter Name, der auf der Benutzeroberfläche angezeigt wird (Optionen)
   * **Beschreibung** – Eine informative Beschreibung des Profils, das seinen Zweck erklärt (optional)
   * **Benutzer per E-Mail benachrichtigen** – Wenn diese Option aktiviert ist, werden Benutzende per E-Mail benachrichtigt, wenn sie zu diesem Profil hinzugefügt oder daraus entfernt werden.

1. Tippen oder klicken Sie auf **Speichern**, wenn Sie den Vorgang abgeschlossen haben.

Das neue Produktprofil wird gespeichert und ist in der Liste der Produktprofile in der Admin Console sichtbar.

### Zuweisen benutzerdefinierter Berechtigungen zum Profil {#assign-permissions}

Nachdem Sie ein neues Produktprofil erstellt haben, können Sie ihm benutzerdefinierte Berechtigungen zuweisen.

1. Tippen oder klicken Sie in der Admin Console auf den Namen des [neuen Produktprofils, das Sie soeben erstellt haben](#create).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Berechtigungen**, um eine Liste bearbeitbarer Berechtigungen anzuzeigen.

   ![Bearbeitbare Berechtigungen](/help/assets/permissions-tab.png)

1. Tippen oder klicken Sie auf den Link **Bearbeiten** einer Berechtigung, um sie zu bearbeiten.

1. Es öffnet sich das Fenster **Berechtigungen bearbeiten**.
   * Die Berechtigung, die Sie im vorherigen Schritt ausgewählt haben, ist in der linken Spalte ausgewählt.
   * Die für die Zuweisung der Berechtigung verfügbaren Berechtigungselemente befinden sich in der mittleren Spalte **Verfügbare Berechtigungselemente**.
   * Die zugewiesenen Berechtigungselemente befinden sich in der rechten Spalte mit der Bezeichnung **Eingeschlossene Berechtigungselemente**.

   ![Berechtigungselemente bearbeiten](/help/assets/edit-permission-items.png)

1. Tippen oder klicken Sie auf das Pluszeichen (`+`) neben dem Berechtigungselement, um dieses der Spalte **Eingeschlossene Berechtigungselemente** hinzuzufügen.

   * Tippen oder klicken Sie auf das Symbol `i` neben einem Berechtigungselement, um mehr darüber zu erfahren.

1. Tippen oder klicken Sie auf **Alle hinzufügen** oben in der Spalte **Verfügbare Berechtigungen**, um alle Berechtigungen hinzuzufügen. Tippen oder klicken Sie auf **Alle entfernen**, um alle zuvor ausgewählten Berechtigungen zu entfernen.

1. Tippen oder klicken Sie auf **Speichern**, wenn Sie die Berechtigungselemente für Ihr neues Produktprofil definiert haben.

Ihr neues Produktprofil wird jetzt mit den benutzerdefinierten Berechtigungen gespeichert.

### Zuweisen von Benutzenden zu den benutzerdefinierten Berechtigungen {#assign-users}

Sie können dem neuen Produktprofil, das Sie mit benutzerdefinierten Berechtigungen erstellt haben, jetzt Benutzende zuweisen.

1. Tippen oder klicken Sie dazu in der Admin Console auf den Namen des [neuen Produktprofils, dem Sie soeben benutzerdefinierte Berechtigungen zugewiesen haben](#assign-permissions).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Benutzer**.

1. Tippen oder klicken Sie auf **Benutzer hinzufügen** und weisen Sie Ihrem neuen Produktprofil Benutzende mit benutzerdefinierten Berechtigungen zu.

Weitere Informationen zum Arbeiten mit der Admin Console finden Sie im Abschnitt **Hinzufügen von Benutzenden und Benutzergruppen zu einem Produktprofil** des Dokuments [Verwalten von Produktprofilen für Unternehmensbenutzende](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html).

## Konfigurierbare Berechtigungen {#configurable-permissions}

Zum Erstellen benutzerdefinierter Profile stehen folgende Berechtigungen zur Verfügung.

| Berechtigung | Beschreibung |
|---|---|
| Programmzugriff | Benutzenden den Zugriff auf Programme gewähren |
| Programmbearbeitung | Benutzenden erlauben, Programme zu bearbeiten |
| Pipeline erstellen | Benutzenden erlauben, neue Pipelines zu erstellen |
| Pipeline löschen | Benutzenden erlauben, Pipelines zu löschen |
| Pipeline-Bearbeitung | Benutzenden erlauben, Pipelines zu bearbeiten |
| Genehmigung/Ablehnung von Produktionsbereitstellungen | Benutzenden erlauben, einen Produktionsbereitstellungsschritt zu genehmigen oder abzulehnen |
| Pipeline-Ausführungen abbrechen | Benutzenden erlauben, Pipeline-Ausführungen abzubrechen |
| Pipeline-Ausführungen starten | Benutzenden erlauben, neue Pipeline-Ausführungen zu starten |
| Wichtige Metrikfehler überschreiben/ablehnen | Benutzenden erlauben, wichtige Metrikfehler zu überschreiben/abzulehnen |
| Produktionsbereitstellungs-Zeitplan | Benutzenden erlauben, einen Produktionsbereitstellungsschritt zu planen |
| Zugriff auf Repository-Informationen | Benutzenden erlauben, auf Repository-Informationen zuzugreifen und ein Passwort für den Zugriff zu erstellen |
| Repository – Erstellen | Benutzenden erlauben, neue Git-Repositorys zu erstellen |
| Repository – Löschen | Benutzenden erlauben, Git-Repositorys zu löschen |
| Repository – Bearbeiten | Benutzenden erlauben, Git-Repositorys zu bearbeiten |
| Repository – Code generieren | Benutzenden erlauben, ein Projekt aus einem Archetyp zu generieren |
| Inhaltskopien – Verwalten | Benutzenden erlauben, Inhaltskopiervorgänge zu verwalten |

### Berechtigungen auf Unternehmensebene {#organization-level}

Berechtigungen auf Unternehmensebene beziehen sich auf Berechtigungen, die immer für alle Programme in einem Unternehmen gewährt werden.

Folgende Berechtigungen sind Berechtigungen auf Unternehmensebene:

* **Zugriff auf Repository-Informationen** Mit dieser Berechtigung auf Mandanten-/Unternehmensebene können Benutzende Benutzernamen, Passwort und Repository-URL generieren, um auf das Kundenprojekt zuzugreifen und zu diesem beizutragen.
   * Benutzername und Passwort für den Repository-Zugriff sind für alle Repositorys des Unternehmens gleich, die Repository-URL ist jedoch für jedes Programm eindeutig.
   * Weitere Informationen finden Sie im Dokument [Quell-Code-Repository](/help/requirements/source-code-repository.md).

## Begriffe {#terms}

Folgende Begriffe werden beim Erstellen und Verwalten benutzerdefinierter Berechtigungen und vordefinierter Rollen verwendet.

| Begriff | Beschreibung |
|---|---|
| Vordefinierte Berechtigungen | Vordefinierte Rollen wie **Geschäftseigentümer**, **Bereitstellungsmanager**, usw. zur Steuerung verschiedener Cloud Manager-Funktionen. Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [Rollenbasierte Berechtigungen.](/help/requirements/role-based-permissions.md) |
| Benutzerdefinierte Berechtigungen | Cloud Manager-Funktionen, mit denen Benutzende Berechtigungsprofile erstellen können, um Rollen zur Verwaltung unterstützter Cloud Manager-Funktionen zu definieren |
| Berechtigungsprofil | Werden in der Admin Console zur Verwaltung konfigurierbarer Berechtigungen erstellt, die für Benutzende gelten, die Teil des Berechtigungsprofils sind |
| Konfigurierbare Berechtigung | Cloud Manager-Berechtigungen, die im Berechtigungsprofil konfiguriert werden können |
| Berechtigungselement | Eine Programm-, Umgebungs- oder Pipeline-Ressource, auf die eine Berechtigung angewendet werden kann |

Berechtigungselemente beziehen sich auf den Anwendungsumfang der Berechtigung. In der Regel ist dies eines der folgenden Elemente.

| Berechtigungselementtyp | Beispiel | Beschreibung |
|---|---|---|
| Unternehmen | Unternehmen:FirmaA | Alle anwendbaren Ressourcen eines Unternehmens. Eine Ressource kann ein Programm, eine Umgebung oder eine Pipeline sein. Wenn Benutzende ein Unternehmen für eine Berechtigung hinzufügen, erhalten auch alle neuen Ressourcen in diesem Unternehmen diese Berechtigung. |
| Programm | Programm A | Alle anwendbaren Ressourcen eines Programms |
| Umgebung | Programm A : Umgebung | Anwendbar für eine bestimmte Umgebung |
| Pipeline | Programm A : Pipeline | Anwendbar für eine bestimmte Pipeline |

## Einschränkungen {#limitations}

Beachten Sie bei der Verwendung benutzerdefinierter Berechtigungen die folgenden Einschränkungen.

* Zur Erstellung benutzerdefinierter Profile ist ein [begrenzter Satz an Berechtigungen verfügbar](#configurable-permissions).
* Bei Ressourcen wie Programm, Umgebung, Pipeline usw., die in Cloud Manager erstellt wurden, kann es bis zu zwei Minuten dauern, bis die Admin Console zur Berechtigungskonfiguration angezeigt wird.
* In seltenen Fällen, in denen der benutzerdefinierte Berechtigungsdienst nicht reagiert, sind vordefinierte Profile weiterhin verfügbar und Benutzende in vordefinierten Profilen haben weiterhin darauf Zugriff.

## Häufig gestellte Fragen {#faq}

### Welche Berechtigungsprofile sind vordefinierte Berechtigungsprofile?

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [Rollenbasierte Berechtigungen.](/help/requirements/role-based-permissions.md)

### Was passiert mit vordefinierten Berechtigungsprofilen bei der Einführung in benutzerdefinierte Profile?

Die standardmäßigen Produktprofile und Cloud Manager-Rollen funktionieren weiterhin wie zuvor.

### Kann ich vordefinierte Berechtigungsprofile bearbeiten?

Nein, Standardprofile können nicht bearbeitet werden. Sie können keine Berechtigungen zum standardmäßigen Berechtigungsprofil hinzufügen oder welche daraus entfernen. Sie können nur Benutzende zu vordefinierten Profilen hinzufügen oder daraus entfernen.

### Sollte ich vordefinierte Berechtigungsprofile löschen, wenn benutzerdefinierte Profile verfügbar sind?

Vordefinierte Berechtigungsprofile dürfen nicht aus der Admin Console gelöscht werden.

### Kann ich Benutzende zu mehreren Berechtigungsprofilen hinzufügen?

Ja, eine Person kann Teil mehrerer Profile sein, einschließlich vordefinierter und benutzerdefinierter Berechtigungsprofile. Wenn eine Person mehreren Profilen zugewiesen wird, stehen ihr die kombinierten Berechtigungen aus allen zugewiesenen Berechtigungsprofilen zur Verfügung.

### Was passiert, wenn eine Person berechtigt ist, eine Umgebung/Pipeline zu bearbeiten, aber keinen Zugriff auf ein Programm hat, das die Umgebung/Pipeline enthält?

In diesem Fall kann die Person nicht auf die Umgebung oder Pipeline zugreifen, wenn sie nicht über die Berechtigungen für den **Programmzugriff** auf die Umgebung oder Pipeline verfügt.

### Was passiert, wenn ich sowohl AEM as a Cloud Service als auch AMS-Programme in derselben IMS-Organisation habe? Kann ich Berechtigungen von einem Profil aus verwalten? {#ams-and-aemaacs}

Sie sollten für jeden Produkttyp ein eigenes Profil erstellen (d. h. eines für AEM als Cloud Service und eines für Adobe Managed Services oder AMS).
