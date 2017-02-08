# SQL

## Выбрать все последовательности и обновить id в таблицах

SELECT c.relname FROM pg_class c WHERE c.relkind = 'S';
SELECT setval('topics_id_seq', (SELECT MAX(id) FROM topics));