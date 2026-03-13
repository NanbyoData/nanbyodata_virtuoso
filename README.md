# nanbyodata_updater

## Overview

* This repository contains tools for updating the **MySQL database** and **NANDO ontology** used in NanbyoData.
* For the NanbyoData Virtuoso update tool, please refer to [this link](https://github.com/NanbyoData/nanbyodata_virtuoso_updater).

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
Virtuoso の管理ユーザー dba のパスワードを指定します。

#### `PWD`
(default: Current working directory)
${PWD} は docker compose を実行したディレクトリのパスを表します。
通常は docker-compose.yml が配置されているディレクトリになります。

Virtuoso のデータは ${PWD}/database に保存されます。
別の場所に保存したい場合は、${PWD} を 任意のホストディレクトリのパスに変更してください。

#### `ENDPOINT_PORT`
(default: 8890)
Virtuoso の SPARQL エンドポイントを公開するホスト側ポート番号を指定します。



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
