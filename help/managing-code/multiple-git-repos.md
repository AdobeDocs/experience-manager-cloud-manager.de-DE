---
title: Arbeiten mit mehreren Git-Repositorys
description: Anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten, erfahren Sie, wie Sie mit Ihrem eigenen Git-Repository oder mehreren Git-Repositorys arbeiten können.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 9%

---

# Arbeiten mit mehreren Quell-Git-Repositorys {#working-with-multiple-source-git-repos}

Anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten, erfahren Sie, wie Sie mit Ihrem eigenen Git-Repository oder mehreren Git-Repositorys arbeiten können.

## Synchronisieren von kundenverwalteten Git-Repositorys {#syncing-customer-managed-git-repositories}

Um das Git-Repository von Cloud Manager auf dem neuesten Stand zu halten, richten Sie einen automatisierten Synchronisierungsprozess ein, wenn Sie Ihr eigenes Repository oder Ihre eigenen Repositorys verwenden.

Je nachdem, wo Ihr Git-Repository gehostet wird, kann zur Einrichtung der Automatisierung eine GitHub-Aktion oder eine kontinuierliche Integrationslösung wie Jenkins verwendet werden. Mit einer vorhandenen Automatisierung kann jeder Push an Ihr eigenes Repository automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Eine solche Automatisierung für ein einzelnes kundeneigenes Git-Repository ist zwar einfach, doch erfordert die Konfiguration für mehrere Repositorys eine umfassendere Ersteinrichtung. Die Inhalte aus mehreren Git-Repositorys müssen verschiedenen Ordnern in einem einzelnen Git-Repository von Cloud Manager zugeordnet werden. Das Git-Repository von Cloud Manager muss mit einem Maven-Stamm `pom.xml` bereitgestellt werden, in dem die verschiedenen Unterprojekte im Modulabschnitt aufgelistet werden.

Nachfolgend finden Sie ein Beispiel für `pom.xml` für zwei kundeneigene Git-Repositorys. Das erste Projekt wird in den Ordner &quot;`project-a`&quot; eingefügt und das zweite Projekt in den Ordner &quot;`project-b`&quot;.

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

Ein solcher Stamm `pom.xml` wird in eine Verzweigung im Git-Repository von Cloud Manager gepusht. Anschließend müssen die beiden Projekte so eingerichtet sein, dass Änderungen automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Beispielsweise kann eine Push-Benachrichtigung an eine Verzweigung in Projekt A eine GitHub-Aktion Trigger werden. Bei der Aktion werden Projekt A und das Cloud Manager-Git-Repository ausgecheckt. Es kopiert alle Inhalte aus Projekt A in das Verzeichnis `project-a` des Git-Repositorys von Cloud Manager. Dann wird die Änderung übernommen und übergeben.

Beispielsweise wird eine Änderung der Verzweigung `main` in Projekt A automatisch in die Verzweigung `main` im Git-Repository von Cloud Manager verschoben. Natürlich kann es eine Zuordnung zwischen Verzweigungen geben, z. B. wenn eine Push-Benachrichtigung an eine Verzweigung mit dem Namen `dev` in Projekt A an eine Verzweigung mit dem Namen `development` im Git-Repository von Cloud Manager gesendet wird. Ähnliche Schritte sind für Projekt B erforderlich.

Je nach Verzweigungsstrategie und Workflows kann die Synchronisierung für verschiedene Verzweigungen konfiguriert werden. Wenn das verwendete Git-Repository kein Konzept bereitstellt, das GitHub-Aktionen ähnelt, ist auch eine Integration über Jenkins (oder Ähnliches) möglich. In diesem Fall Trigger ein Webhook einen Jenkins-Job, der die Arbeit ausführt.

Gehen Sie wie folgt vor, um eine neue (dritte) Quelle oder ein neues Repository hinzuzufügen:

1. Fügen Sie dem neuen Repository eine neue GitHub-Aktion hinzu, die Änderungen von diesem Repository an das Git-Repository von Cloud Manager überträgt.
1. Führen Sie diese Aktion mindestens einmal aus, um sicherzustellen, dass sich der Projektcode im Git-Repository von Cloud Manager befindet.
1. Fügen Sie im Stammordner Maven `pom.xml` des Cloud Manager Git-Repositorys einen Verweis auf den neuen Ordner hinzu.

## Beispielaktion für GitHub {#sample-github-action}

Durch einen Push an die `main`-Verzweigung wird diese GitHub-Beispielaktion Trigger, die dann in ein Unterverzeichnis des Git-Repositorys von Cloud Manager gepusht wird. Die GitHub-Aktionen müssen mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung zum Git-Repository von Cloud Manager herstellen und pushen zu können.

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

Wie oben gezeigt, ist die Verwendung einer GitHub-Aktion flexibel. Jede Zuordnung zwischen Zweigen der Git-Repositorys kann durchgeführt werden und jede Zuordnung der einzelnen Git-Projekte zum Verzeichnis-Layout des Hauptprojekts.

>[!NOTE]
>
>Das obige Skript verwendet `git add`, um das Repository zu aktualisieren. Dabei wird davon ausgegangen, dass Entfernungen enthalten sind. Abhängig von der Standardkonfiguration von Git muss diese Anforderung möglicherweise durch `git add --all` ersetzt werden.

## Jenkins-Beispielauftrag {#sample-jenkins-job}

Dieses Skript ist ein Beispiel, das in einem Jenkins-Auftrag oder ähnlichen Aufgaben verwendet werden kann. Eine Änderung in einem Git-Repository Trigger sie. Der Jenkins-Auftrag überprüft den neuesten Status des Projekts oder der Verzweigung und löst dann dieses Skript aus.

Dieses Skript checkt wiederum das Git-Repository von Cloud Manager aus und übergibt den Projektcode in ein Unterverzeichnis.

Der Jenkins-Auftrag muss mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung herstellen und zum Git-Repository von Cloud Manager übertragen werden zu können.

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

Wie oben gezeigt, ist die Verwendung eines Jenkins-Auftrags sehr flexibel. Jede Zuordnung zwischen Zweigen der Git-Repositorys kann durchgeführt werden und jede Zuordnung der einzelnen Git-Projekte zum Verzeichnis-Layout des Hauptprojekts.

>[!NOTE]
>
>Das obige Skript verwendet `git add`, um das Repository zu aktualisieren. Dabei wird davon ausgegangen, dass Entfernungen enthalten sind. Abhängig von der Standardkonfiguration von Git muss `git add` möglicherweise durch `git add --all` ersetzt werden.
