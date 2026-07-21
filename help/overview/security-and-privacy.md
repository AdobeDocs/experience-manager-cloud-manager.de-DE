---
title: Sicherheit und Datenschutz
description: Erfahren Sie mehr über die Sicherheit und den Datenschutz von Code- und Artefakt-Assets in Adobe Cloud Manager.
exl-id: 67df1987-8db7-40bd-9717-1bf194e957f7
TQID: https://experienceleague.adobe.com/mtWOzJnzV8k403LlyD9Fn9WSE5XTgjHzyVuA4j62MMg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: d5a34a9f6d050eaff241c0f42c9cf023cbc8036a
workflow-type: tm+mt
source-wordcount: 201
ht-degree: 26%

---

# Sicherheit und Datenschutz {#security-and-privacy}

Erfahren Sie mehr über die Sicherheit und den Datenschutz von Code- und Artefakt-Assets in Adobe Cloud Manager.

## Rollen und Berechtigungen {#roles}

Cloud Manager verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen.

Informationen zu den möglichen Rollen, die Sie in der Admin Console und in den Benutzerrollenberechtigungen zuweisen können, finden Sie unter [Rollenbasierte Berechtigungen](/help/requirements/role-based-permissions.md).

## Ressourcenisolation {#resource-isolation}

Cloud Manager-Kunden benötigen ihre IMS-Anmeldedaten, um sich zu authentifizieren, da alle Berechtigungen, die an Cloud Manager gebunden sind, an ihre IMS-Organisationen gebunden sind. Während des Onboarding-Prozesses stellt das Bereitstellungs-Team sicher, dass die Ressourcenisolation in Cloud Manager durchgesetzt wird.

## Datensicherheit {#data-security}

Cloud Manager-Code wird während der Übertragung verschlüsselt. Cloud Manager erstellt Binärdateien, die auch während der Übertragung verschlüsselt und in einem verschlüsselten Format gespeichert werden.

Jeder Kunde erhält ein eigenes Git-Repository, und der Code ist geschützt und wird nicht für andere Organisationen freigegeben.

## Datenschutz {#data-privacy}

Cloud Manager hält sich an die von Adobe definierten Datenschutzgrundsätze. Entwickelnde können Code dank HTTPS sicher per Push an Git-Repositorys übertragen.

Die Benutzeroberfläche von Cloud Manager nutzt Services, die dem Common Control Framework von Adobe entsprechen. Die Benutzeroberfläche von Cloud Manager nutzt sichere Services von verschiedenen Cloud-Anbietern.
