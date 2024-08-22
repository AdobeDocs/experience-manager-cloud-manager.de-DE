---
title: Sicherheit und Datenschutz
description: Erfahren Sie mehr über die Sicherheit und den Datenschutz von Code- und Artefakt-Assets in Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 60%

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

Jeder Kunde erhält sein eigenes Git-Repository. Der Code ist geschützt und wird nicht für andere Organisationen freigegeben.

## Datenschutz {#data-privacy}

[!UICONTROL Cloud Manager] erfüllt die von Adobe definierten Datenschutzgrundsätze. Entwickler pushen Code sicher über HTTPS in Git-Repositorys.

Die Benutzeroberfläche von [!UICONTROL Cloud Manager] basiert auf Diensten, die einem Adobe Common Control Framework entsprechen. Die Benutzeroberfläche von [!UICONTROL Cloud Manager] nutzt sichere Services von verschiedenen Cloud-Anbietern.
