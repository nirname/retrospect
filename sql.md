# SQL

## Выбрать все последовательности и обновить id в таблицах

```sql
  SELECT c.relname FROM pg_class c WHERE c.relkind = 'S';
  SELECT setval('topics_id_seq', (SELECT MAX(id) FROM topics));
```

## IN != NOT IN

```sql
select id from (select 1 as id union select 2 union select 3) as t where id in (1,2,null);
```

```text
 id
----
  1
  2
```

```sql
select id from (select 1 as id union select 2 union select 3) as t where id not in (1,2,null);
```

```text
 id
----
(0 rows)
```
