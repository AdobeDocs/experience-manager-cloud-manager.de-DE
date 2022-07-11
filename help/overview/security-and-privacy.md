---
title: Sicherheit und Datenschutz
description: Erfahren Sie mehr über die Sicherheit und den Datenschutz von Code- und Artefakt-Assets in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 25%

---


# Sicherheit und Datenschutz {#security-and-privacy}

Erfahren Sie mehr über die Sicherheit und den Datenschutz von Code- und Artefakt-Assets in Cloud Manager.

## Rollen und Berechtigungen {#roles}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen.

Informationen zu den möglichen Rollen, die Sie in der Admin Console und den Benutzerrollenberechtigungen zuweisen können, finden Sie im Dokument . [Rollenbasierte Berechtigungen.](/help/requirements/role-based-permissions.md)

## Ressourcenisolation {#resource-isolation}

[!UICONTROL Cloud Manager] Kunden benötigen ihre IMS-Anmeldeinformationen, um sich zu authentifizieren, da alle Berechtigungen an [!UICONTROL Cloud Manager] sind an ihre IMS-Organisationen gebunden. Während des Onboarding-Prozesses stellt das Bereitstellungsteam sicher, dass die Ressourcenisolation in [!UICONTROL Cloud Manager].

## Datensicherheit {#data-security}

Code in [!UICONTROL Cloud Manager] wird während der Übertragung verschlüsselt. Von Cloud Manager erstellte Binärdateien werden ebenfalls während der Übertragung und beim Speichern verschlüsselt.

Jeder Kunde erhält sein eigenes Git-Repository und Code ist sicher und wird nicht für andere Organisationen freigegeben.

## Datenschutz {#data-privacy}

[!UICONTROL Cloud Manager] erfüllt die von Adobe definierten Datenschutzgrundsätze. Entwickler pushen Code sicher über HTTPS in Git-Repositorys.

[!UICONTROL Cloud Manager]Die -Benutzeroberfläche von basiert auf Diensten, die einem gemeinsamen Steuerungsframework der Adobe entsprechen, das dies ermöglicht. [!UICONTROL Cloud Manager]Die -Benutzeroberfläche von verwendet sichere Dienste verschiedener Cloud-Anbieter.
