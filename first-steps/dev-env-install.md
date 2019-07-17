This document describes the development environment installation for frontend and backend developers.

> **Note**
>
> This documentation has been tested for Ubuntu 16.04

# Apps List

1.  Mongo 3.2

2.  Postgres 9.5

3.  Neo4j 2.3.2

4.  Nodejs

5.  Gulp

6.  JDK 7

7.  Gradle 1.6

8.  Vert.x 2.1.6

9.  Git

10. SSH Key for github

> **Note**
>
> Code Editor software is up to developer’s choice

# Installation Guide

## 1. Mongo 3.2

Installation:

    $ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
    $ echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
    $ sudo apt-get update
    $ sudo apt-get install -y mongodb-org=3.2.12 mongodb-org-server=3.2.12 mongodb-org-shell=3.2.12 mongodb-org-mongos=3.2.12 mongodb-org-tools=3.2.12

Check version:

    $ mongod --version
    db version v3.2.12

Start service:

    $ sudo service mongod start

## 2. Postgres 9.5

Check candidate version is 9.5:

    $ apt-cache policy postgresql
    Candidate: 9.5+173

    $ sudo apt update
    $ sudo apt install postgresql postgresql-contrib

Create user : web-education / We\_1234

    $ sudo su - postgres
    $ psql
    $ create user "web-education" createdb createuser password 'We_1234';

Create databases ong and one:

    $ create database ong owner "web-education";
    $ create database one owner "web-education";

Start Service:

    $ sudo service postgresql start

## 3. Neo4j 3.1.6

Add package repository:

    $ wget -O - https://debian.neo4j.org/neotechnology.gpg.key | sudo apt-key add -
    $ echo 'deb https://debian.neo4j.org/repo stable/' | sudo tee /etc/apt/sources.list.d/neo4j.list
    $ sudo apt-get update

Installation:

    $ sudo apt-get install neo4j=3.1.6

Add configuration in **/etc/neo4j/neo4j.conf** :

    # Enable auto-indexing for nodes, default is false
    dbms.auto_index.nodes.enabled=true

    # The node property keys to be auto-indexed, if enabled
    dbms.auto_index.nodes.keys=name

    dbms.security.auth_enabled=false

    # Cypher language compatibility
    cypher.default_language_version=2.3

Start Service:

    $ sudo service neo4j start

> **Note**
>
> Neo4j http url <http://localhost:7474>

## 4. NodeJS

Download:

    $ mkdir ~/apps
    $ cd ~/apps
    $ wget https://nodejs.org/dist/v6.10.0/node-v6.10.0-linux-x64.tar.xz
    $ tar xf node-v6.10.0-linux-x64.tar.xz
    $ ln -s node-v6.10.0-linux-x64 node

Add binary to Path:

    $ echo PATH=\"\$HOME/apps/node/bin:\$PATH\" >> ~/.profile
    $ . ~/.profile

Check version:

    $ node -v
    v6.10.0

## 5. Gulp

Installation:

    $ npm install -g gulp

## 6. JDK 8

Installation:

    $ sudo add-apt-repository ppa:webupd8team/java
    $ sudo apt-get update
    $ sudo apt-get install oracle-java8-installer

Check installation:

    $ java -version
    java version "1.8.0_152"
    Java(TM) SE Runtime Environment (build 1.8.0_152-b16)
    Java HotSpot(TM) 64-Bit Server VM (build 25.152-b16, mixed mode)

## 7. Gradle 1.6

Installation:

    $ cd ~/apps
    $ wget https://services.gradle.org/distributions/gradle-1.6-bin.zip
    $ unzip gradle-1.6-bin.zip
    $ ln -s gradle-1.6 gradle
    $ rm gradle-1.6-bin.zip

Add binary to Path:

    $ echo PATH=\"\$HOME/apps/gradle/bin:\$PATH\" >> ~/.profile
    $ . ~/.profile

Check version:

    $ gradle -v
    Gradle 1.6

## 8. Vert.x 2.1.6

Download:

    $ cd ~/apps
    $ wget -O vert.x-2.1.6.tar.gz https://bintray.com/vertx/downloads/download_file?file_path=vert.x-2.1.6.tar.gz
    $ tar xf vert.x-2.1.6.tar.gz$ ssh-keygen -t rsa -b 4096 -C "viddouille.cc@gmail.com"
    $ ln -s vert.x-2.1.6 vert.x
    $ rm vert.x-2.1.6.tar.gz

Add binary to Path:

    $ echo PATH=\"\$HOME/apps/vert.x/bin:\$PATH\" >> ~/.profile
    $ . ~/.profile

Check version:

    $ vertx version

Add following line in the vertx configuration file **{VERTX\_HOME}/conf/repos.txt**:

    maven:http://maven.web-education.net/nexus/content/groups/public/

## 9. Git

Installation:

    $ sudo apt install git

## 10. SSH Key for github

To set SSH key for Github, please follow the reference documentation below:

-   <https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/>

-   <https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/>


