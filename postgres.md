# Postgres

Add to Gemfile

    gem 'pg'

Install libraries

    sudo apt-get install libpq-dev


Run this before `bundle install`

    bundle config build.pg --with-pg-config=/usr/pgsql-9.3/bin/pg_config

Without `bundle`

    gem install pg -- --with-pg-config=/usr/pgsql-9.3/bin/pg_config

Check out [installation guide](https://access.redhat.com/site/documentation/en-US/JBoss_Operations_Network/2.1/html/Installation_Guide/Installation_Guide-Database-PostgreSQL_Quick_Start_Installation.html)

Starting and stopping database server

    service postgresql-9.3
      initdb
      start
      stop
      restart

Login as `postgres` user

    sudo su - postgres

Manage database user

    createuser -P -s -e username
    dropuser username

Manage database

    createdb -O username databasename
    dropdb dbname

Database console

    psql # open console
    \du # list of users
    \q # quit
    \l # all schemas

    select * from pg_trigger; # select triggers

Check out version

    psql --version;
    select version();

Find configuration file

    locate pg_hba.conf
    vi /var/lib/pgsql/9.3/data/pg_hba.conf

Upgrade from 9.1 to 9.3

    sudo service postgresql stop
    sudo pg_dropcluster --stop 9.3 main
    sudo pg_upgradecluster 9.1 main
    sudo service postgresql start 9.3
    pg_dropcluster --stop 9.1 main

Dump and restore database

    pg_dump -Fc -U user database > path/to/dump # dump
    psql dbname < path/to/dump # restore
    pg_restore -U user -d database filename # restore

For ansible

    sudo apt-get install python-psycopg2

Check out listen addresses

    sudo netstat -pant | grep postgres
    find / -name postgresql.conf 2> /dev/null
    listen_addresses = '*'

Database config example

    production:
      adapter: postgresql
      encoding: unicode
      database: my_database
      host: 1.2.3.4
      port: 5432
      pool: 10
      username: my_user
      password: password
