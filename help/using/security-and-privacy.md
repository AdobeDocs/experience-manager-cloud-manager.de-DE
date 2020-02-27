---
title: Sicherheit und Datenschutz
seo-title: Sicherheit und Datenschutz für AEM Cloud Manager
description: Auf dieser Seite erfahren Sie mehr zum Thema Sicherheit und Datenschutz von Assets (Code/Artefakten).
seo-description: Auf dieser Seite erfahren Sie mehr zum Thema Sicherheit und Datenschutz von Assets (Code/Artefakten) bei Verwendung von AEM Cloud Manager.
uuid: 68bc2330-a62c-4c2c-925c-daa6788b143a
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: introduction
discoiquuid: 67a54bae-99a9-4405-91e3-9a0a8b3ccc98
translation-type: tm+mt
source-git-commit: 7cbc42108a6ccc8f7303eb76fd8ca2e9027f49e0

---


# Sicherheit und Datenschutz {#security-and-privacy}

[!UICONTROL Cloud Manager] hat vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Dieser Abschnitt hebt die Sicherheit und den Datenschutz Ihrer Assets (Code/Artefakte) mit AEM Cloud Manager hervor. Additionally, [!UICONTROL Cloud Manager] has pre-configured roles with appropriate permissions.

Informationen zu den möglichen Rollen, die Sie in der Admin-Konsole und den Benutzerrollenberechtigungen zuweisen können, finden Sie unter [Rollenbasierte Berechtigungen](/help/using/role-based-permissions.md).


## Ressourcenisolation {#resource-isolation}

Kunden, die [!UICONTROL Cloud Manager] verwenden, benötigen ihre IMS-Anmeldeinformationen, um sich zu authentifizieren, da alle mit [!UICONTROL Cloud Manager] verbundenen Berechtigungen konfiguriert und an die IMS-Organisation gebunden werden. Während des Onboardingprozesses stellt das Bereitstellungsteam sicher, dass die Ressourcenisolation in [!UICONTROL Cloud Manager] durchgesetzt wird.

## Datensicherheit {#data-security}

Code in [!UICONTROL Cloud Manager] is encrypted in transit. Von Cloud Manager erstellte Binärdateien werden ebenfalls während der Übertragung und beim Speichern verschlüsselt.

Alle Kunden erhalten ein eigenes **Git-Repository**. Ihr Code ist sicher und wird nicht an andere **Organisationen** weitergegeben.

## Datenschutz {#data-privacy}

[!UICONTROL Cloud Manager] die Datenschutzgrundsätze von Adobe einhält. Entwickler können Code dank HTTPS sicher per Push an das **Git-Repository** übertragen.

Die [!DNL Benutzeroberfläche (User Interface, UI) für [!UICONTROL Cloud Manager]] basiert auf Diensten, die einem gemeinsamen, von Adobe definierten Steuerungsframework entsprechen. Die [!DNL Benutzeroberfläche (User Interface, UI) für [!UICONTROL Cloud Manager]] nutzt sichere Dienste verschiedener Cloudanbieter.
