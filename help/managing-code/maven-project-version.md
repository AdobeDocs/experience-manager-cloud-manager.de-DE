---
title: Umgang mit Maven-Projektversionen
description: Erfahren Sie, wie Maven die Projektversionierung in Cloud Manager handhabt.
exl-id: a1d676e0-27cc-4b0d-8799-527c0520946a
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 37%

---


# Umgang mit Maven-Projektversionen {#project-version}

Erfahren Sie, wie Maven die Projektversionierung in Cloud Manager handhabt.

## Verarbeitung von Projektversionen durch Maven {#how-maven}

Für Staging- und Produktionsbereitstellungen generiert Cloud Manager eine eindeutige, inkrementierende Version.

Diese Version wird auf der Seite mit Details zur Pipeline-Ausführung und auf der Aktivitätsseite angezeigt. Wenn ein Build ausgeführt wird, wird das Maven-Projekt aktualisiert, um diese Version zu verwenden. Ein Tag wird im Git-Repository mit dieser Version als Namen erstellt.

Wenn die Originalversion des Projekts bestimmte Kriterien erfüllt, führt die aktualisierte Maven-Projektversion sowohl die Originalversion des Projekts als auch die von Cloud Manager generierte Version zusammen. Das Tag verwendet jedoch immer die generierte Version. Für diese Zusammenführung muss die ursprüngliche Projektversion mit genau drei Versionssegmenten erstellt werden (z. B. `1.0.0` oder `1.2.3`, nicht jedoch `1.0` oder `1`) und die Originalversion darf nicht auf `-SNAPSHOT` enden.

>[!NOTE]
>
>Dieser Wert für die Originalversion des Projekts muss im Element `<version>` der obersten Ebene der Datei `pom.xml` in der Git-Repository-Verzweigung statisch festgelegt werden.

Wenn die Originalversion diese Kriterien erfüllt, wird die generierte Version als neues Versionssegment an die Originalversion angehängt. Die generierte Version wird auch geringfügig geändert, um eine ordnungsgemäße Sortierung und Versionsverwaltung einzuschließen. Nehmen wir als Beispiel eine generierte Version von `2019.926.121356.0000020490`:

| Version | Version in `pom.xml` | Kommentar |
| --- | --- | --- |
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | Richtig geformte Originalversion |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | Snapshot-Version, überschrieben |
| `1` | `2019.926.121356.0000020490` | Unvollständige Version, überschrieben |

>[!NOTE]
>
>Unabhängig davon, ob die Originalversion in die Cloud Manager-initialisierte Version integriert wurde oder nicht, ist sie weiterhin als Maven-Eigenschaft mit dem Namen `cloudManagerOriginalVersion` verfügbar.
