# Postgres

## Estimate tables size

SELECT pg_size_pretty( pg_database_size('dbname') );
SELECT pg_size_pretty( pg_total_relation_size('tablename') );

## Select triggers

```sql
select * from pg_trigger;
```

## Check out version

```bash
psql --version;
```

```sql
select version();
```

## Find configuration file

    locate pg_hba.conf
    vi /var/lib/pgsql/9.3/data/pg_hba.conf

## Check out listen addresses

    sudo netstat -pant | grep postgres
    find / -name postgresql.conf 2> /dev/null
    listen_addresses = '*'

