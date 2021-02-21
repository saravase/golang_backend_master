# golang_backend_master

## Design DB Schema - dbdiagram.io

    https://dbdiagram.io/d/6030ff1efcdcb6230b20b439

## Install postgres - Docker

    $ docker pull postgres:12-alpine

    $ docker run --name postgres12 -p 5433:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=xxxxx -d postgres:12-alpine

    $ docker exec -it postgres2 psql -U root

        root=# select now();
        root=# \q
    
    $ docker logs postgres2

    $ history | grep "docker run"


## Migration - golang_migrate

    $  curl -s https://packagecloud.io/install/repositories/golang-migrate/migrate/script.deb.sh | sudo bash

    $ sudo apt-get install -y migrate

    $ migrate --help

    $ migrate -version

    $ migrate create -ext sql -dir db/migration -seq init_schema

## Create Makefile and Execute cmd:

    $ make postgres     -   Install postgres
    $ make createdb     -   Create database in postgres
    $ make dropdb       -   Remove database in postgres
    $ make migrateinit  -   Create migration up and down file
    $ make migrateup    -   Execute sql queries mentioned in up file
    $ make migratedown  -   Execute sql queries mentioned in down file

## Generate CRUD code - SQLC

    DATABASE/SQL:

        1.Very fast & straightforward
        2.Manual mapping SQL fields to variables
        3.Easy to make mistakes, not cought until runtime

    GORM:

        1.CRUD functions already implemented, very short production code
        2.Must learn to write queries using gorm's function
        3.Run slowly on high load

    SQLX:

        1.Quite fast & easy to use
        2.Fields mapping via query text & struct tags
        3.Failure won't occur until runtime

    SQLC:

        1.Very fast & easy to use
        2.Automatic code generation
        3.Catch SQL query errors before generating codes
        4.Full support Postgres, MySQL is experimental


    $ sudo snap install sqlc

    $ sqlc version

    $ sqlc help