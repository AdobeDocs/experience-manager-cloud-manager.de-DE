---
title: Handhabung von Maven-Projektversionen
seo-title: Handhabung von Maven-Projektversionen
description: Erfahren Sie mehr über Maven Project Version Handling.
seo-description: Auf dieser Seite erfahren Sie mehr über Maven Project Version Handling
translation-type: tm+mt
source-git-commit: f5ff89820eb843b35b617d300dbbc07f19ca2c17

---


# Handhabung von Maven-Projektversionen {#project-version}

## Umgang mit Maven-Projektversionen {#understanding-project-version}

Für Bereitstellungen von Stage und Produktion generiert Cloud Manager eine eindeutige, inkrementierte Version.

Diese Version wird auf der Seite mit Details zur Pipelineausführung sowie auf der Aktivitätsseite angezeigt. Wenn ein Build ausgeführt wird, wird das Maven-Projekt aktualisiert, um diese Version zu verwenden, und im Git-Repository wird ein Tag mit dieser Version als Name erstellt.

Wenn die ursprüngliche Projektversion bestimmte Kriterien erfüllt, führt die aktualisierte Maven-Projektversion sowohl die ursprüngliche Projektversion als auch die von Cloud Manager generierte Version zusammen. Das Tag verwendet jedoch immer die generierte Version. Damit diese Zusammenführung erfolgt, muss die ursprüngliche Projektversion mit genau drei Versionssegmenten wie 1.0.0 oder 1.2.3, nicht jedoch 1.0 oder 1, und die Originalversion darf nicht in -SNAPSHOT enden.

Wenn die Originalversion diese Kriterien erfüllt, wird die generierte Version als neues Versionssegment an die Originalversion angehängt. Die generierte Version wird auch geringfügig geändert, um eine ordnungsgemäße Sortierung und Versionsverwaltung einzuschließen. Beispiel: Angenommen, eine generierte Version von 2019.926.121356.0000020490

| **Version** | **Version in pom.xml** | **Kommentar** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | Richtig geformte Originalversion |
| 1.0.0-SNAPSHOT | 2019.926.121356.0000020490 | Snapshot-Version, überschrieben |
| 1 | 2019.926.121356.0000020490 | Unvollständige Version, überschrieben |

>[!NOTE]
>
>Unabhängig davon, ob die Originalversion in die mit Cloud Manager initialisierte Version integriert wurde oder nicht, ist die Originalversion als Maven-Eigenschaft mit dem Namen *cloudManagerOriginalVersion verfügbar.*
