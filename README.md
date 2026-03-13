# nanbyodata_virtuoso

## Overview

* This repository manages the configuration settings for NanbyoData Virtuoso.
* For environment-specific values, please use a .env file or clone this repository to update your local settings as needed.
* ⚠️ **Note: Please handle sensitive information with extreme care.**

## Prerequisites

* **Docker** / **Docker Compose**

## Setup & Usage

### 1. Environment Configuration

Initialize your environment variables by copying the template file and editing it with your local settings.

```bash
cp template.env .env
vi .env
```

#### `UID`

(default: 0)

Host user id for the docker container. You can find your user id by `id -u`.

#### `DOCKER_GID`

(default: 0)

Host group id for the docker container. You can find your group id by `id -g`.

#### `DBA_PASSWORD_1`
(default: Node)
Please specify the password for the Virtuoso administrator user "dba".

#### `PWD`
(default: Current working directory)
Virtuoso data is stored in `${PWD}/database`.
By default, `${PWD}` refers to the directory where `docker compose` is executed, which is usually the directory containing `docker-compose.yml`.

If you want to store the data in a different location, change `${PWD}` to the path of your desired host directory.

#### `ENDPOINT_PORT`
(default: 8890)
Specify the host port number that exposes the Virtuoso SPARQL endpoint.



### 2. Building Containers  
Build the required Docker images for each environment. Note that the MySQL build requires local user IDs for volume permission consistency.

```bash
# Perl environment
docker compose build perl

# Python environment
docker compose build python

# ROBOT (Ontology processing)
docker compose build robot

# MySQL (Database)
docker compose build mysql
```

### 3. Execution and Operation  
Operational workflows are detailed in the following documentation:  

* [MySQL Update Procedure](https://docs.google.com/spreadsheets/d/12JjDHkd4k9oI5Xme_Isyg9nqUsHU1PZvmvz5DQPKNZc/edit?gid=1150718828#gid=1150718828)
* [NANDO Ontology Update Procedure](https://docs.google.com/spreadsheets/d/12JjDHkd4k9oI5Xme_Isyg9nqUsHU1PZvmvz5DQPKNZc/edit?gid=1914005581#gid=1914005581)  

[!IMPORTANT]  
If you are unable to access the documentation links above, please contact the DBCLS team.  
