---

[//]: # (@formatter:off)
layout: page
title: Postgres Installation
permalink: /docs/dev/postgres-installation
parent: Developer
grand_parent: Tips & Tricks
nav_order: 1
last_modified_date: Dec 28 2022 17:58
---
[//]: # (@formatter:on)

# Postgres Installation

## Install postgres from binaries

[Download binaries from here!](https://www.enterprisedb.com/download-postgresql-binaries)

## Install postgres from source

- [Download sources from here!](https://www.postgresql.org/ftp/source/)
  ```shell
  # Extract the source
  tar -xvzf postgresql-<VERSION>.tar.gz
  cd postgresql-<VERSION>
  ```
- Clone from git, [check tags here!](https://git.postgresql.org/gitweb/?p=postgresql.git;a=tags)
  ```shell
  # Clone the repo
  git clone --depth 1 -b <TAG> https://git.postgresql.org/git/postgresql.git
  cd postgresql
  ```
- Make and Install
  ```shell
  # Check openssl
  which openssl
  
  # Configure the build
  ./configure --with-openssl \
    --with-includes=/usr/local/opt/openssl/include \
    --with-libraries=/usr/local/opt/openssl/lib 
    --prefix $HOME/dev/postgres/pgsql
  
  # Make
  make world
  
  # Install
  make install-world 
  ```

## Configure

### env variables and aliases

```shell
# Postgres config
export PG_HOME="$HOME/dev/postgres"
export PG_LOG_FILE="$PG_HOME/postgres.log"
export PG_DATA="$PG_HOME/pgdata"

export PATH="$PG_HOME/pgsql/bin:$PATH"

alias start_postgres="pg_ctl -D ${PG_DATA} -l ${PG_LOG_FILE} start"
alias stop_postgres="pg_ctl -D ${PG_DATA} -l ${PG_LOG_FILE} stop"
```

### InitDB (create database folder structure)

```shell
initdb ${PG_DATA}
```

### Create user/role

```shell
createuser --interactive --pwprompt
```

### Create database

```shell
createdb -O <user_name> <db_name>
```

### Login to database

```shell
psql -U <user_name> -d <database> [-h <host>] [-p <port>] -a
```
