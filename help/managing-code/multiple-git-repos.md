---
title: Arbeiten mit mehreren Git-Repositorys
description: Erfahren Sie, wie Sie Ihre eigenen Git-Repository oder mehrere Git-Repositorys verwenden können, anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten.
exl-id: 53bf78bb-489a-4a83-8459-c361f532d54a
TQID: https://experienceleague.adobe.com/xKzqOfbi12A0POy-C7Gm7-n649DEBX9JP3LfXA5UC3Y
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: a07522b4a3c0619bb57b414de58633c65d9c7b5c
workflow-type: tm+mt
source-wordcount: 727
ht-degree: 60%

---

# Arbeiten mit Git-Repositorys aus mehreren Quellen {#working-with-multiple-source-git-repos}

Erfahren Sie, wie Sie Ihre eigenen Git-Repository oder mehrere Git-Repositorys verwenden können, anstatt direkt mit dem Git-Repository von Cloud Manager zu arbeiten.

## Synchronisieren von kundenverwalteten Git-Repositorys {#syncing-customer-managed-git-repositories}

Richten Sie einen automatisierten Synchronisierungsprozess ein, wenn Sie eigene Repositorys verwenden, um das Git-Repository von Cloud Manager auf dem neuesten Stand zu halten.

Je nachdem, wo Ihr Git-Repository gehostet wird, verwenden Sie eine GitHub-Aktion oder Continuous-Integration-Lösung wie Jenkins zum Einrichten der Automatisierung. Bei bestehender Automatisierung kann jeder Push an Ihr eigenes Repository automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Während diese Automatisierung für ein einzelnes kundeneigenes Git-Repository einfach ist, erfordert die Konfiguration für mehrere Repositorys eine aufwändigere Ersteinrichtung. Die Inhalte aus mehreren Git-Repositorys müssen verschiedenen Verzeichnissen in einem einzelnen Git-Repository von Cloud Manager zugeordnet werden. Das Git-Repository von Cloud Manager muss mit einem Maven-`pom.xml` bereitgestellt werden, in dem die verschiedenen Unterprojekte im Modulabschnitt aufgelistet werden

Nachfolgend finden Sie eine Beispiel-`pom.xml` für zwei kundeneigene Git-Repositorys. Das erste Projekt wird im Verzeichnis `project-a` abgelegt, das zweite Projekt im Verzeichnis `project-b`.

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

Eine solche Stamm-`pom.xml` wird per Push an eine Verzweigung im Git-Repository von Cloud Manager übergeben. Anschließend müssen die beiden Projekte so eingerichtet werden, dass Änderungen automatisch an das Git-Repository von Cloud Manager weitergeleitet werden.

Beispielsweise kann ein Push-Vorgang an eine Verzweigung in Projekt A eine GitHub-Aktion auslösen. Bei der Aktion werden Projekt A und das Cloud Manager-Git-Repository ausgecheckt. Dabei werden alle Inhalte aus Projekt A in das Verzeichnis `project-a` des Git-Repositorys von Cloud Manager kopiert. Anschließend wird die Änderung übernommen und per Push übergeben.

Eine Änderung an der Verzweigung `main` in Projekt A wird etwa automatisch per Push an die Verzweigung `main` im Git-Repository von Cloud Manager übergeben. Es könnte auch eine Zuordnung zwischen Verzweigungen geben, z. B. wenn ein Push zu einer Verzweigung namens `dev` in Projekt A zu einer Verzweigung mit der Bezeichnung `development` im Git-Repository von Cloud Manager verschoben wird. Ähnliche Schritte sind für Projekt B erforderlich.

Je nach Verzweigungsstrategie und Workflows kann die Synchronisierung für verschiedene Verzweigungen konfiguriert werden. Wenn das verwendete Git-Repository kein Konzept wie GitHub-Aktionen bereitstellt, ist auch eine Integration mit Jenkins (oder einer ähnlichen Lösung) möglich. In diesem Fall führt ein Webhook einen Jenkins-Auftrag aus, der die Aufgabe ausführt.

Gehen Sie wie folgt vor, um eine neue (dritte) Quelle oder ein neues Repository hinzuzufügen:

1. Fügen Sie eine neue GitHub-Aktion zum neuen Repository hinzu, um Änderungen von diesem Repository per Push an das Git-Repository von Cloud Manager zu übertragen.
1. Um sicherzustellen, dass sich der Projekt-Code im Git-Repository von Cloud Manager befindet, führen Sie diese Aktion mindestens einmal durch.
1. Fügen Sie einen Verweis auf das neue Verzeichnis in der Maven-Stamm-`pom.xml` im Git-Repository von Cloud Manager hinzu.

## GitHub-Beispielaktion {#sample-github-action}

Durch einen Push an die `main`-Verzweigung wird diese GitHub-Beispielaktion ausgelöst, die dann in ein Unterverzeichnis des Git-Repositorys von Cloud Manager gepusht wird. Die GitHub-Aktion muss mit zwei Geheimnissen versehen werden, `MAIN_USER` und `MAIN_PASSWORD`, damit eine Verbindung hergestellt werden kann und eine Übertragung zum Git-Repository von Cloud Manager möglich ist.

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

Wie oben gezeigt, sind GitHub-Aktionen flexibel einsetzbar. Es können alle Zuordnungen zwischen Verzweigungen der Git-Repositorys sowie alle Zuordnungen der separaten Git-Projekte in das Verzeichnis-Layout des Hauptprojekts durchgeführt werden.

>[!NOTE]
>
>Das obige Skript verwendet `git add`, um das Repository zu aktualisieren, wobei davon ausgegangen wird, dass dies auch Löschvorgänge umfasst. Ersetzen Sie diese Anforderung je nach Standardkonfiguration von Git durch `git add --all`.

## Jenkins-Beispielauftrag {#sample-jenkins-job}

Bei dem Beispiel handelt es sich um ein Skript, das in einem Jenkins-Auftrag o. Ä. verwendet werden kann. Eine Änderung in einem Git-Repository ist hierfür der Auslöser. Der Jenkins-Auftrag überprüft den neuesten Status des Projekts oder der Verzweigung und löst dann dieses Skript aus.

Dieses Skript überprüft das Git-Repository von Cloud Manager und übergibt den Projekt-Code an ein Unterverzeichnis.

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

Die Verwendung eines Jenkins-Auftrags ist flexibel. Es können alle Zuordnungen zwischen Verzweigungen der Git-Repositorys sowie alle Zuordnungen der separaten Git-Projekte in das Verzeichnis-Layout des Hauptprojekts durchgeführt werden.

>[!NOTE]
>
>Das obige Skript verwendet `git add`, um das Repository zu aktualisieren, wobei davon ausgegangen wird, dass dies auch Löschvorgänge umfasst. Ersetzen Sie je nach Standardkonfiguration von Git `git add` durch `git add --all`.
