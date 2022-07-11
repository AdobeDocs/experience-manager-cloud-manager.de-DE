---
title: Arbeiten mit mehreren Git-Repositorys
description: Erfahren Sie, wie Sie statt direkt mit dem Git-Repository von Cloud Manager mit Ihrem eigenen Git-Repository oder mehreren Git-Repositorys arbeiten können.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: da9dff997a277c207e2c48207217cb30325f3c0d
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 14%

---

# Arbeiten mit Git-Repositorys aus mehreren Quellen {#working-with-multiple-source-git-repos}

Erfahren Sie, wie Sie statt direkt mit dem Git-Repository von Cloud Manager mit Ihrem eigenen Git-Repository oder mehreren Git-Repositorys arbeiten können.

## Synchronisieren von kundenverwalteten Git-Repositorys {#syncing-customer-managed-git-repositories}

Wenn Sie mit Ihrem eigenen Repository oder Ihren eigenen Repositorys arbeiten möchten, sollte ein automatisierter Synchronisierungsprozess eingerichtet werden, um sicherzustellen, dass das Git-Repository von Cloud Manager immer auf dem neuesten Stand gehalten wird.

Je nachdem, wo Ihr Git-Repository gehostet wird, kann eine GitHub-Aktion oder eine kontinuierliche Integrationslösung wie Jenkins zum Einrichten der Automatisierung verwendet werden. Mit einer vorhandenen Automatisierung kann jeder Push an Ihr eigenes Repository automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Eine solche Automatisierung für ein einzelnes kundeneigenes Git-Repository ist zwar einfach, doch erfordert die Konfiguration dieser Funktion für mehrere Repositorys eine umfassendere Ersteinrichtung. Die Inhalte aus mehreren Git-Repositorys müssen verschiedenen Ordnern innerhalb eines einzelnen Git-Repositorys von Cloud Manager zugeordnet werden. Das Git-Repository von Cloud Manager muss mit einem Maven-Stamm bereitgestellt werden `pom.xml`, in der die verschiedenen Unterprojekte im Modulabschnitt aufgelistet werden

Nachfolgend finden Sie ein Beispiel `pom.xml` für zwei kundeneigene Git-Repositorys. Das erste Projekt wird in das Verzeichnis namens `project-a`, wird das zweite Projekt in das Verzeichnis mit dem Namen `project-b`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
  
    <groupId>customer.group.id</groupId>
    <artifactId>customer-reactor</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>pom</packaging>
  
    <modules>
        <module>project-a</module>
        <module>project-b</module>
    </modules>
  
</project>
```

Diese Wurzel `pom.xml` wird in eine Verzweigung im Git-Repository von Cloud Manager gepusht. Anschließend müssen die beiden Projekte so eingerichtet sein, dass Änderungen automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Beispielsweise kann eine GitHub-Aktion durch einen Push an eine Verzweigung in Projekt A ausgelöst werden. Die Aktion checkt Projekt A und das Cloud Manager-Git-Repository aus und kopiert alle Inhalte aus Projekt A in den Ordner . `project-a` in das Git-Repository von Cloud Manager ein und die Änderung dann per Commit-Push übernehmen.

Beispielsweise eine Änderung der `main` Verzweigung in Projekt A wird automatisch an die `main` -Verzweigung im Git-Repository von Cloud Manager. Natürlich kann es eine Zuordnung zwischen Verzweigungen geben, wie eine Push-Benachrichtigung zu einer Verzweigung mit dem Namen `dev` in Projekt A an eine Verzweigung mit dem Namen `development` im Git-Repository von Cloud Manager. Ähnliche Schritte sind für Projekt B erforderlich.

Je nach Verzweigungsstrategie und Workflows kann die Synchronisierung für verschiedene Verzweigungen konfiguriert werden. Wenn das verwendete Git-Repository kein Konzept bereitstellt, das GitHub-Aktionen ähnelt, ist auch eine Integration über Jenkins (oder Ähnliches) möglich. In diesem Fall löst ein Webhook einen Jenkins-Auftrag aus, der die Aufgabe ausführt.

Gehen Sie wie folgt vor, um eine neue (dritte) Quelle oder ein neues Repository hinzuzufügen:

1. Fügen Sie dem neuen Repository eine neue GitHub-Aktion hinzu, die Änderungen von diesem Repository in das Git-Repository von Cloud Manager überträgt.
1. Führen Sie diese Aktion mindestens einmal aus, um sicherzustellen, dass sich der Projekt-Code im Git-Repository von Cloud Manager befindet.
1. Fügen Sie im Maven-Stammordner einen Verweis zum neuen Ordner hinzu. `pom.xml` im Git-Repository von Cloud Manager.

## GitHub-Beispielaktion {#sample-github-action}

Dies ist eine GitHub-Beispielaktion, die durch einen Push an die `main` Verzweigung und dann Push in ein Unterverzeichnis des Git-Repositorys von Cloud Manager. Die GitHub-Aktionen müssen mit zwei Geheimnissen versehen werden: `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung zum Git-Repository von Cloud Manager herstellen und pushen zu können.

```java
name: SYNC
env:
  # Username/email used to commit to Cloud Manager's Git repository
  USER_NAME: <NAME>
  USER_EMAIL: <EMAIL>
  # Directory within the Cloud Manager Git repository
  PROJECT_DIR: project-a
  # Cloud Manager's Git repository
  MAIN_REPOSITORY: https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
  # The branch in Cloud Manager's Git repository to push to
  MAIN_BRANCH : <BRANCH_NAME>
 
# Only run on a push to this branch
on:
  push:
     branches: [ main ]
 
jobs:
  build:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout this project into a sub folder
      - uses: actions/checkout@v2
        with:
          path: sub
      # Cleanup sub project
      - name: Clean project
        run: |
          git -C sub log --format="%an : %s" -n 1 > commit.txt
          rm -rf sub/.git
          rm -rf sub/.github
      # Set global git configuration
      - name: Set git config
        run: |
          git config --global credential.helper cache
          git config --global user.email ${USER_EMAIL}
          git config --global user.name ${USER_NAME}
      # Checkout the main project
      - name: Checkout main project
        run:
          git clone -b ${MAIN_BRANCH} https://${{ secrets.PAT }}@github.com/${MAIN_REPOSITORY}.git main 
      # Move sub project
      - name: Move project to main project
        run: |
          rm -rf main/${PROJECT_DIR} 
          mv sub main/${PROJECT_DIR}
      - name: Commit Changes
        run: |
          git -C main add -f ${PROJECT_DIR}
          git -C main commit -F ../commit.txt
          git -C main push
```

Wie oben gezeigt, ist die Verwendung einer GitHub-Aktion sehr flexibel. Jede Zuordnung zwischen Zweigen der Git-Repositorys sowie jede Zuordnung der einzelnen Git-Projekte zum Verzeichnis-Layout des Hauptprojekts können durchgeführt werden.

>[!NOTE]
>
>Das obige Skript verwendet `git add` , um das Repository zu aktualisieren, bei dem davon ausgegangen wird, dass Entfernungen enthalten sind. Abhängig von der Standardkonfiguration von Git muss dies möglicherweise durch `git add --all`.

## Jenkins-Beispielauftrag {#sample-jenkins-job}

Hierbei handelt es sich um ein Beispielskript, das in einem Jenkins-Auftrag oder einem ähnlichem Auftrag verwendet werden kann. Sie wird durch eine Änderung in einem Git-Repository ausgelöst. Der Jenkins-Auftrag überprüft den neuesten Status des Projekts oder der Verzweigung und löst dann dieses Skript aus.

Dieses Skript checkt wiederum das Git-Repository von Cloud Manager aus und übergibt den Projekt-Code in ein Unterverzeichnis.

Der Jenkins-Job muss mit zwei Geheimnissen ausgestattet werden, `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung zum Git-Repository von Cloud Manager herstellen und pushen zu können.

```java
# Username/email used to commit to Cloud Manager's Git repository
export USER_NAME=<NAME>
export USER_EMAIL=<EMAIL>
# Directory within the Cloud Manager Git repository
export PROJECT_DIR=project-a
# Cloud Manager's Git repository
export MAIN_REPOSITORY=https://$MAIN_USER:$MAIN_PASSWORD@git.cloudmanager.adobe.com/<PATH>
# The branch in Cloud Manager's Git repository to push to
export MAIN_BRANCH=<BRANCH_NAME>
 
# clean up and init
rm -rf target
mkdir target
 
# mv project to sub folder
mkdir target/sub
for f in .* *
do
    if [ "$f" != "." -a "$f" != ".." -a "$f" != "target" ]
    then
        mv "$f" target/sub
    fi
done
cd target
 
# capture log and remove git info
cd sub
git log --format="%an : %s" -n 1 > ../commit.txt
rm -rf .git
rm -rf .github
cd ..
 
# checkout main repository
git clone -b $MAIN_BRANCH $MAIN_REPOSITORY main
cd main
 
# configure main repository
git config credential.helper cache
git config user.email $USER_EMAIL
git config user.name $USER_NAME
 
# update project in main
rm -rf $PROJECT_DIR
mv ../sub $PROJECT_DIR
 
# commit changes to main
git add -f $PROJECT_DIR
git commit -F ../commit.txt
git push
```

Wie oben gezeigt, ist die Verwendung eines Jenkins-Auftrags sehr flexibel. Jede Zuordnung zwischen Zweigen der Git-Repositorys sowie jede Zuordnung der einzelnen Git-Projekte zum Verzeichnis-Layout des Hauptprojekts können durchgeführt werden.

>[!NOTE]
>
>Das obige Skript verwendet `git add` Um das Repository zu aktualisieren, bei dem davon ausgegangen wird, dass Entfernungen enthalten sind. Abhängig von der Standardkonfiguration von Git muss dies möglicherweise durch `git add --all`.
