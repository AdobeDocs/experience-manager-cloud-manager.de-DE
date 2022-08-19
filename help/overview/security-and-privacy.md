---
title: Sicherheit und Datenschutz
description: Erfahren Sie mehr über die Sicherheit und den Datenschutz von Code- und Artefakt-Assets in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: d7751757c1d3bda3d60406a1d39cb41c61f5c863
workflow-type: ht
source-wordcount: '205'
ht-degree: 100%

---


# Sicherheit und Datenschutz {#security-and-privacy}

Erfahren Sie mehr über die Sicherheit und den Datenschutz von Code- und Artefakt-Assets in Cloud Manager.

## Rollen und Berechtigungen {#roles}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen.

Informationen zu den möglichen Rollen, die Sie in der Admin Console und den Benutzerrollenberechtigungen zuweisen können, finden Sie unter [Rollenbasierte Berechtigungen](/help/requirements/role-based-permissions.md).

## Ressourcenisolation {#resource-isolation}

[!UICONTROL Cloud Manager]-Kunden benötigen ihre IMS-Anmeldedaten, um sich zu authentifizieren, da alle Berechtigungen, die an [!UICONTROL Cloud Manager] gebunden sind, an ihre IMS-Organisationen gebunden sind. Während des Onboarding-Prozesses stellt das Bereitstellung-Team sicher, dass die Ressourcenisolation in [!UICONTROL Cloud Manager] durchgesetzt wird.

## Datensicherheit {#data-security}

Code in [!UICONTROL Cloud Manager] wird während der Übertragung verschlüsselt. Von Cloud Manager erstellte Binärdateien werden ebenfalls während der Übertragung und beim Speichern verschlüsselt.

Jeder Kunde erhält ein eigenes Git-Repository. Sein Code ist sicher und wird nicht an andere Organisationen weitergegeben.

## Datenschutz {#data-privacy}

[!UICONTROL Cloud Manager] erfüllt die von Adobe definierten Datenschutzgrundsätze. Entwickler können Code dank HTTPS sicher per Push an Git-Repositorys übertragen.

Die Benutzeroberfläche von [!UICONTROL Cloud Manager] basiert auf Services, die einem gemeinsamen Kontroll-Framework von Adobe entsprechen. Die Benutzeroberfläche von [!UICONTROL Cloud Manager] nutzt sichere Services von verschiedenen Cloud-Anbietern.
