---
title: Umgang mit Maven-Projektversionen
seo-title: Umgang mit Maven-Projektversionen
description: Erfahren Sie mehr über den Umgang mit Maven-Projektversionen.
seo-description: Auf dieser Seite erfahren Sie mehr über den Umgang mit Maven-Projektversionen.
translation-type: tm+mt
source-git-commit: e2187565e7f06d64841eb2af9b4b1a56feb5ebe4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Umgang mit Maven-Projektversionen {#project-version}

## Umgang mit Maven-Projektversionen {#understanding-project-version}

Für Staging- und Produktionsumgebungen generiert Cloud Manager eine eindeutige, inkrementierende Version.

Diese Version wird auf der Seite mit den Details zur Pipelineausführung sowie auf der Aktivitätsseite angezeigt. Wenn ein Build ausgeführt wird, wird das Maven-Projekt aktualisiert, um diese Version zu verwenden. Außerdem wird im Git-Repository ein Tag mit dieser Version als Name erstellt.

Wenn die Originalversion des Projekts bestimmte Kriterien erfüllt, führt die aktualisierte Maven-Projektversion sowohl die Originalversion des Projekts als auch die von Cloud Manager generierte Version zusammen. Das Tag verwendet jedoch immer die generierte Version. Für diese Zusammenführung muss die ursprüngliche Projektversion mit genau drei Versionssegmenten erstellt werden (z. B. 1.0.0 oder 1.2.3, nicht jedoch 1.0 oder 1) und darf die Originalversion nicht mit -SNAPSHOT enden.

Wenn die Originalversion diese Kriterien erfüllt, wird die generierte Version als neues Versionssegment an die Originalversion angehängt. Die generierte Version wird außerdem geringfügig geändert, um eine ordnungsgemäße Sortierung und Versionsverwaltung einzuschließen. Nehmen wir als Beispiel eine generierte Version von 2019.926.121356.0000020490:

| **Version** | **Version in pom.xml** | **Kommentar** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | Richtig geformte Originalversion |
| 1.0.0-SNAPSHOT | 2019.926.121356.0000020490 | Snapshot-Version, überschrieben |
| 1 | 2019.926.121356.0000020490 | Unvollständige Version, überschrieben |

>[!NOTE]
>
>Unabhängig davon, ob die Originalversion in die mit Cloud Manager initialisierte Version integriert wurde oder nicht, ist die Originalversion als Maven-Eigenschaft mit dem Namen *cloudManagerOriginalVersion* verfügbar.
