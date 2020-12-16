---
title: Arbeiten mit mehreren Quell-Git-Repositorys
description: Arbeiten mit mehreren Quell-Git-Repositorys – Cloud Manager
translation-type: ht
source-git-commit: f5359dee907b32cefa2db2c4ad2baf8e337f6060
workflow-type: ht
source-wordcount: '747'
ht-degree: 100%

---


# Arbeiten mit mehreren Quell-Git-Repositorys {#working-with-multiple-source-git-repos}


## Synchronisieren von kundenverwalteten Git-Repositorys {#syncing-customer-managed-git-repositories}

Anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten, können Kunden mit ihrem eigenen Git-Repository oder mehreren eigenen Git-Repositorys arbeiten. In diesen Fällen sollte ein automatisierter Synchronisierungsprozess eingerichtet werden, um sicherzustellen, dass das Git-Repository von Cloud Manager stets auf dem neuesten Stand gehalten wird. Je nachdem, wo das Git-Repository des Kunden gehostet wird, kann eine GitHub-Aktion oder eine kontinuierliche Integrationslösung wie Jenkins zum Einrichten der Automatisierung verwendet werden. Bei einer bereits vorhandenen Automatisierung kann jeder Push an ein im Kundenbesitz befindliches Git-Repository automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Während eine solche Automatisierung für ein einzelnes kundeneigenes Git-Repository unkompliziert ist, erfordert die Einrichtung für mehrere Repositorys eine anfängliche Einrichtung. Die Inhalte der verschiedenen Git-Repositorys müssen verschiedenen Verzeichnissen im Git-Repository von Cloud Manager zugeordnet werden.  Für das Git-Repository von Cloud Manager muss ein Maven-Root-Pom bereitgestellt werden, in dem die verschiedenen Unterprojekte im Modulabschnitt aufgelistet werden.

Im Folgenden finden Sie ein Beispiel für zwei kundeneigene Git-Repositorys: das erste Projekt wird in das Verzeichnis mit dem Namen `project-a` gestellt und das zweite Projekt in das Verzeichnis mit dem Namen `project-b`.

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

Ein solches Root-Pom wird im Git-Repository von Cloud Manager in eine Verzweigung gepusht. Anschließend müssen die beiden Projekte so eingerichtet sein, dass Änderungen automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Beispielsweise kann eine GitHub-Aktion durch einen Push an eine Verzweigung in Projekt A ausgelöst werden. Die Aktion checkt Projekt A und das Cloud Manager-Git-Repository aus und kopiert und schreibt (commit-push) alle Inhalte aus Projekt A in das Verzeichnis `project-a` im Git-Repository von Cloud Manager. Beispielsweise wird eine Änderung in der Hauptverzweigung in Projekt A automatisch in die Hauptverzweigung im Git-Repository von Cloud Manager gepusht. Natürlich könnte es eine Zuordnung zwischen den Verzweigungen geben. Ein Push in eine Verzweigung „dev“ in Projekt A könnte in eine Verzweigung „development“ im Git-Repository von Cloud Manager gepusht werden. Ähnliche Schritte sind für Projekt B erforderlich.

Je nach Verzweigungsstrategie und Workflows kann die Synchronisierung für verschiedene Verzweigungen konfiguriert werden. Wenn das verwendete Git-Repository kein Konzept ähnlich den GitHub-Aktionen bietet, ist auch eine Integration über Jenkins o. ä. möglich. In diesem Fall löst ein Webhook einen Jenkins-Job aus, der die Arbeit ausführt.

Gehen Sie wie folgt vor, um eine neue (dritte) Quelle oder ein neues Repository hinzuzufügen:

1. Fügen Sie dem neuen Repository eine neue GitHub-Aktion hinzu, die Änderungen von diesem Repository in das Git-Repository von Cloud Manager überträgt.
1. Führen Sie diese Aktion mindestens einmal aus, um sicherzustellen, dass sich der Projekt-Code im Git-Repository von Cloud Manager befindet.
1. Fügen Sie einen Verweis auf das neue Verzeichnis im Maven-Root-POM im Git-Repository von Cloud Manager hinzu.


## Beispiel einer GitHub-Aktion {#sample-github-action}

Bei dem Beispiel handelt es sich um eine GitHub-Aktion, die durch einen Push in die Hauptverzweigung ausgelöst wird und dann in ein Unterverzeichnis des Git-Repositorys von Cloud Manager pusht. Die GitHub-Aktionen müssen mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung zum Git-Repository von Cloud Manager herstellen und pushen zu können.

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

Wie oben gezeigt, ist die Verwendung einer GitHub-Aktion sehr flexibel. Jede Zuordnung zwischen den Verzweigungen der Git-Repositorys sowie jede Zuordnung der einzelnen Git-Projekte zum Verzeichnis-Layout des Hauptprojekts ist möglich.

>[!NOTE]
>Das obige Skript verwendet `git add`, um das Repository zu aktualisieren. Dabei wird davon ausgegangen, dass Entfernungen enthalten sind. Abhängig von der Git-Standardkonfiguration muss dies durch `git add --all` ersetzt werden.

## Beispiel-Jenkins-Job {#sample-jenkins-job}

Bei dem Beispiel handelt es sich um ein Skript, das in einem Jenkins-Job o. ä. verwendet werden kann. Es wird durch eine Änderung in einem Git-Repository ausgelöst. Der Jenkins-Job überprüft den neuesten Status des Projekts oder der Verzweigung und löst dann dieses Skript aus.

Dieses Skript checkt wiederum das Git-Repository von Cloud Manager aus und schreibt den Projekt-Code in ein Unterverzeichnis.

Der Jenkins-Job muss mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, um eine Verbindung zum Git-Repository von Cloud Manager herstellen und pushen zu können.

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

Wie oben gezeigt, ist die Verwendung eines Jenkins-Jobs sehr flexibel. Jede Zuordnung zwischen den Verzweigungen der Git-Repositorys sowie jede Zuordnung der einzelnen Git-Projekte zum Verzeichnis-Layout des Hauptprojekts ist möglich.

>[!NOTE]
>Das obige Skript verwendet `git add`, um das Repository zu aktualisieren. Dabei wird davon ausgegangen, dass Entfernungen enthalten sind. Abhängig von der Git-Standardkonfiguration muss dies durch `git add --all` ersetzt werden.