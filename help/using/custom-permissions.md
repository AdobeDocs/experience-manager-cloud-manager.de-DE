---
title: Benutzerdefinierte Berechtigungen
description: Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.
exl-id: a81eda9f-aa89-40ea-8e4c-52367a0a6aba
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 51%

---

# Benutzerdefinierte Berechtigungen {#custom-permissions}

Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.

## Einführung {#introduction}

Cloud Manager verfügt über eine Reihe vordefinierter Rollen, die den Zugriff auf verschiedene Cloud Manager-Funktionen steuern:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

Mit benutzerdefinierten Berechtigungen können Benutzende neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um für Cloud Manager-Benutzende den Zugriff auf Programme, Pipelines und Umgebungen zu beschränken.

>[!TIP]
>
>Weitere Informationen zu vordefinierten Rollen finden Sie unter [Rollenbasierte Berechtigungen](/help/requirements/role-based-permissions.md).

## Verwenden benutzerdefinierter Berechtigungen {#using}

Die Erstellung und Verwendung eigener benutzerdefinierter Berechtigungen erfordert die folgenden drei Schritte:

1. [Erstellen Sie ein neues Produktprofil](#create).
1. [Weisen Sie dem neuen Produktprofil benutzerdefinierte Berechtigungen zu.](#assign-permissions)
1. [Weisen Sie dem neuen Produktprofil Benutzer zu](#assign-users).

In diesem Abschnitt werden diese Schritte beschrieben. Möglicherweise ist es nützlich, die Abschnitte [Begriffe](#terms) und [Konfigurierbare Berechtigungen](#configurable-permissions) anzuzeigen, wenn Sie eigene benutzerdefinierte Berechtigungen erstellen.

>[!NOTE]
>
>Sie müssen über Produktadministratorrechte in der Admin Console verfügen, um neue Profile zu erstellen und Berechtigungen für Cloud Manager zu verwalten.

### Neues Produktprofil erstellen {#create}

Erstellen Sie zunächst ein neues Produktprofil, dem Sie benutzerdefinierte Berechtigungen zuweisen können.

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an.

1. Wählen Sie das Produkt **AEM Managed Services** aus.

1. Suchen Sie nach und Instanz mit dem Namen, der dem Muster `*-cloud-manager` entspricht, und klicken Sie auf , um Benutzer und Berechtigungen zu verwalten.

1. Sie werden zur Registerkarte **Produkte** der Admin Console weitergeleitet, wo Sie Benutzer und Berechtigungen für Cloud Manager verwalten können. Klicken Sie in der Admin Console auf **Neues Profil**.

![Schaltfläche „Neues Profil“](/help/assets/admin-console-new-profile.png)

1. Geben Sie die allgemeinen Details zum Profil an.

   * **Name des Produktprofils** – Ein aussagekräftiger Name des Profils
   * **Anzeigename** - Ein abgekürzter Name, der in der Benutzeroberfläche angezeigt wird (Optionen)
   * **Beschreibung**: Eine informative Beschreibung des Profils, das seinen Zweck erklärt (optional)
   * **Benutzer per E-Mail benachrichtigen** - Wenn ausgewählt, benachrichtigt das System Benutzer per E-Mail, wenn sie diesem Profil hinzugefügt oder daraus entfernt werden.

1. Klicken Sie auf **Speichern**.

Das neue Produktprofil wird gespeichert und ist in der Liste der Produktprofile in der Admin Console sichtbar.

### Weisen Sie dem neuen Produktprofil benutzerdefinierte Berechtigungen zu {#assign-permissions}

Nachdem Sie ein neues Produktprofil erstellt haben, können Sie ihm benutzerdefinierte Berechtigungen zuweisen.

1. Klicken Sie in der Admin Console auf den Namen des soeben erstellten [neuen Produktprofils](#create).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Berechtigungen**, um eine Liste bearbeitbarer Berechtigungen anzuzeigen.

   ![Bearbeitbare Berechtigungen](/help/assets/permissions-tab.png)

1. Klicken Sie auf den Link **Bearbeiten** , um die Berechtigung zum Bearbeiten zu erhalten.

1. Das Fenster **Berechtigungen bearbeiten** wird geöffnet.
   * Die Berechtigung, die Sie im vorherigen Schritt ausgewählt haben, ist in der linken Spalte ausgewählt.
   * Die für die Zuweisung der Berechtigung verfügbaren Berechtigungselemente befinden sich in der mittleren Spalte **Verfügbare Berechtigungselemente**.
   * Die zugewiesenen Berechtigungselemente befinden sich in der rechten Spalte mit der Bezeichnung **Eingeschlossene Berechtigungselemente**.

   ![Berechtigungselemente bearbeiten](/help/assets/edit-permission-items.png)

1. Klicken Sie auf das Pluszeichen (`+`) neben dem Berechtigungselement, um es zur Spalte **Eingeschlossene Berechtigungselemente** hinzuzufügen. Klicken Sie bei Bedarf auf das Symbol `i` neben einem Berechtigungselement, um mehr darüber zu erfahren.

1. Klicken Sie oben in der Spalte **Verfügbare Berechtigungen** auf **Alle hinzufügen** , um alle Berechtigungen hinzuzufügen. Klicken Sie auf **Alle entfernen** , um alle zuvor ausgewählten Berechtigungen zu entfernen.

1. Wenn Sie mit der Definition der Berechtigungselemente für Ihr neues Produktprofil fertig sind, klicken Sie auf **Speichern**.

Ihr neues Produktprofil wird jetzt mit den benutzerdefinierten Berechtigungen gespeichert.

### Benutzer dem neuen Produktprofil zuweisen {#assign-users}

Sie können dem neuen Produktprofil, das Sie mit benutzerdefinierten Berechtigungen erstellt haben, jetzt Benutzende zuweisen.

1. Klicken Sie in der Admin Console auf den Namen des [neuen Produktprofils, dem Sie soeben benutzerdefinierte Berechtigungen zugewiesen haben](#assign-permissions).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Benutzer**.

1. Klicken Sie auf **Benutzer hinzufügen** und weisen Sie Ihrem neuen Produktprofil Benutzer mit benutzerdefinierten Berechtigungen zu.

Weitere Informationen zur Verwendung der Admin Console finden Sie unter **Hinzufügen von Benutzern und Benutzergruppen zu einem Produktprofil** des Dokuments [Verwalten von Produktprofilen für Unternehmensbenutzer](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html) .

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
| Zugriff auf Repository-Informationen | Erlauben Sie Benutzern, auf Repository-Informationen zuzugreifen und ein Kennwort für den Zugriff zu generieren |
| Repository erstellen | Benutzern das Erstellen neuer Git-Repositorys ermöglichen |
| Repository löschen | Löschen von Git-Repositorys durch Benutzer zulassen |
| Repository bearbeiten | Benutzern erlauben, Git-Repositorys zu bearbeiten |
| Repository-Code-Generierung | Benutzenden erlauben, Projekte aus einem Archetyp zu generieren |
| Inhaltskopie verwalten | Benutzenden erlauben, Vorgänge zum Kopieren von Inhalten zu verwalten |

### Berechtigungen auf Organisationsebene {#organization-level}

Berechtigungen auf Organisationsebene werden immer für alle Programme innerhalb einer Organisation angewendet.

Ein Beispiel für eine Berechtigung auf Organisationsebene in Cloud Manager ist **Zugriff auf Repository-Informationen**. Mit dieser Berechtigung können Benutzer einen Benutzernamen, ein Kennwort und eine Repository-URL generieren, um auf Kundenprojekte zuzugreifen und zu diesen beizutragen. Während Benutzername und Kennwort für alle Repositorys in der Organisation konsistent bleiben, verfügt jedes Programm über eine eindeutige Repository-URL.

Weitere Informationen finden Sie im [Source Code-Repository](/help/requirements/source-code-repository.md) .

## Begriffe {#terms}

Folgende Begriffe werden beim Erstellen und Verwalten benutzerdefinierter Berechtigungen und vordefinierter Rollen verwendet.

| Begriff | Beschreibung |
|---|---|
| Vordefinierte Berechtigungen | Vordefinierte Rollen wie **Business Owner**, **Deployment Manager** usw. zur Steuerung verschiedener Cloud Manager-Funktionen. Weitere Informationen zu vordefinierten Rollen finden Sie unter [Rollenbasierte Berechtigungen](/help/requirements/role-based-permissions.md). |
| Benutzerdefinierte Berechtigungen | Cloud Manager-Funktionen, mit denen Benutzer Berechtigungsprofile erstellen können, um Rollen für unterstützte Funktionen von Cloud Manager zu definieren |
| Berechtigungsprofil | Wird in der Admin Console zur Verwaltung konfigurierbarer Berechtigungen erstellt, die für Benutzende gelten, die Teil des Berechtigungsprofils sind |
| Konfigurierbare Berechtigung | Cloud Manager-Berechtigungen können im Berechtigungsprofil konfiguriert werden |
| Berechtigungselement | Eine Programm-, Umgebungs- oder Pipeline-Ressource, auf die eine Berechtigung angewendet werden kann |

Berechtigungselemente beziehen sich auf den Umfang, in dem Berechtigungen angewendet werden. In der Regel handelt es sich um Folgendes.

| Berechtigungselementtyp | Beispiel | Beschreibung |
|---|---|---|
| Unternehmen | Unternehmen:FirmaA | Alle anwendbaren Ressourcen eines Unternehmens. Eine Ressource kann ein Programm, eine Umgebung oder eine Pipeline sein. Wenn Benutzende ein Unternehmen für eine Berechtigung hinzufügen, erhalten auch alle neuen Ressourcen in diesem Unternehmen diese Berechtigung. |
| Programm | Programm A | Alle anwendbaren Ressourcen eines Programms |
| Umgebung | Programm A : Umgebung | In einer bestimmten Umgebung anwendbar |
| Pipeline | Programm A : Pipeline | Anwendbar für eine bestimmte Pipeline |

## Einschränkungen {#limitations}

Beachten Sie bei der Verwendung benutzerdefinierter Berechtigungen die folgenden Einschränkungen:

* Zur Erstellung benutzerdefinierter Profile ist ein [begrenzter Satz an Berechtigungen verfügbar](#configurable-permissions).
* Bei Ressourcen wie Programm, Umgebung, Pipeline usw., die in Cloud Manager erstellt wurden, kann es bis zu zwei Minuten dauern, bis die Admin Console zur Berechtigungskonfiguration angezeigt wird.
* In seltenen Fällen, in denen ein benutzerdefinierter Berechtigungsdienst nicht reagiert, sind vordefinierte Profile weiterhin verfügbar und Benutzer in vordefinierten Profilen haben weiterhin den entsprechenden Zugriff.

## Häufig gestellte Fragen {#faq}

### Welche Berechtigungsprofile sind vordefinierte Berechtigungsprofile?

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

Weitere Informationen zu vordefinierten Rollen finden Sie unter [Rollenbasierte Berechtigungen](/help/requirements/role-based-permissions.md).

### Was passiert mit vordefinierten Berechtigungsprofilen bei der Einführung in benutzerdefinierte Profile?

Standardproduktprofile und Cloud Manager-Rollen funktionieren weiterhin wie zuvor.

### Kann ich vordefinierte Berechtigungsprofile bearbeiten?

Nein, Standardprofile können nicht bearbeitet werden. Sie können dem standardmäßigen Berechtigungsprofil keine Berechtigungen hinzufügen oder entfernen. Sie können nur Benutzende zu vordefinierten Profilen hinzufügen oder daraus entfernen.

### Sollte ich vordefinierte Berechtigungsprofile löschen, wenn benutzerdefinierte Profile verfügbar sind?

Vordefinierte Berechtigungsprofile dürfen nicht aus der Admin Console gelöscht werden.

### Kann ich Benutzende zu mehreren Berechtigungsprofilen hinzufügen?

Ja, eine Person kann Teil mehrerer Profile sein, einschließlich vordefinierter und benutzerdefinierter Berechtigungsprofile. Wenn eine Person mehreren Profilen zugewiesen wird, stehen ihr die kombinierten Berechtigungen aus allen zugewiesenen Berechtigungsprofilen zur Verfügung.

### Was passiert, wenn ein Benutzer berechtigt ist, eine Umgebung/Pipeline zu bearbeiten, aber keinen Zugriff auf ein Programm hat, das die Umgebung/Pipeline enthält?

In diesem Szenario kann der Benutzer nicht auf die Umgebung oder Pipeline zugreifen, wenn er nicht über die **Programmzugriffsberechtigungen** verfügt, die die Umgebung oder Pipeline enthalten.

### Was passiert, wenn ich sowohl AEM as a Cloud Service als auch AMS-Programme in derselben IMS-Organisation habe? Kann ich Berechtigungen von einem Profil aus verwalten? {#ams-and-aemaacs}

Erstellen Sie für jeden Produkttyp ein eigenes Profil. Das heißt, eine für AEM als Cloud Service und eine für Adobe Managed Services oder AMS.
