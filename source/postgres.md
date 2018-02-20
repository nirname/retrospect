# Postgres

## Installation

Check out [installation guide](https://access.redhat.com/site/documentation/en-US/JBoss_Operations_Network/2.1/html/Installation_Guide/Installation_Guide-Database-PostgreSQL_Quick_Start_Installation.html)

### Ubuntu

    sudo apt-get install libpq-dev

### OS X

    brew update
    brew doctor
    brew install postgres

## Using with Ruby

Add to Gemfile

```ruby
gem 'pg'
```

Run this before `bundle install`

    bundle config build.pg --with-pg-config=/usr/pgsql-9.3/bin/pg_config

Without `bundle`

    gem install pg -- --with-pg-config=/usr/pgsql-9.3/bin/pg_config

## Running

Starting and stopping database server

    service postgresql-9.3
      initdb
      start
      stop
      restart

Autostart for OS X

    mkdir -p ~/Library/LaunchAgents
    ln -sfv /usr/local/opt/postgresql/*.plist ~/Library/LaunchAgents
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

Login as `postgres` user

    sudo su - postgres

Manage database user

    createuser -P -s -e username
    dropuser username

Change a role's password:

    ALTER ROLE davide WITH PASSWORD 'hu8jmn3';

Remove a role's password:

    ALTER ROLE davide WITH PASSWORD NULL;

Manage database

    createdb -O username databasename
    dropdb dbname

Database console

```bash
psql # open console
\du # list of users
\q # quit
\l # all schemas
```

Select triggers

```sql
select * from pg_trigger;
```

Check out version

```bash
psql --version;
```

```sql
select version();
```

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

    # -Fc - custom format

    pg_dump -Fc -U user database > path/to/dump # dump
    psql dbname < path/to/dump # restore
    pg_restore -U user -d database filename # restore

    # restore sql

    psql -U user database < dump

PostGIS

    sudo apt-get install postgis*

    CREATE EXTENSION postgis;
    SELECT postgis_full_version();

For ansible

    sudo apt-get install python-psycopg2

Check out listen addresses

    sudo netstat -pant | grep postgres
    find / -name postgresql.conf 2> /dev/null
    listen_addresses = '*'

Database config example

```yaml
production:
  adapter: postgresql
  encoding: unicode
  database: my_database
  host: 1.2.3.4
  port: 5432
  pool: 10
  username: my_user
  password: password
```
