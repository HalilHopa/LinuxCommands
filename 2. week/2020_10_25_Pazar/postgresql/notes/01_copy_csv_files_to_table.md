## List available databases
```
[train@localhost postgresql]$ psql -l
Password: Ankara06
                                   List of databases
    Name    |   Owner   | Encoding |   Collate   |    Ctype    |   Access privileges
------------+-----------+----------+-------------+-------------+-----------------------
 airflow    | airflow   | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 giteadb    | gitea     | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 homecredit | train     | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 metastore  | metastore | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 mlflow     | train     | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 postgres   | postgres  | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 template0  | postgres  | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =c/postgres          +
            |           |          |             |             | postgres=CTc/postgres
 template1  | postgres  | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =c/postgres          +
            |           |          |             |             | postgres=CTc/postgres
 traindb    | train     | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =Tc/train            +
            |           |          |             |             | train=CTc/train
(9 rows)
```

## Connection options
```
Connection options:
  -h, --host=HOSTNAME      database server host or socket directory (default: "local socket")
  -p, --port=PORT          database server port (default: "5432")
  -U, --username=USERNAME  database user name (default: "train")
  -w, --no-password        never prompt for password
  -W, --password           force password prompt (should happen automatically)
```

- Example connection to `traindb` database
```
[train@localhost postgresql]$ psql -h localhost -p 5432 -U train -d traindb -W
Password for user train:
psql (9.2.24, server 10.13)
WARNING: psql version 9.2, server version 10.0.
         Some psql features might not work.
Type "help" for help.

traindb=>
```
- list tables on selected database
```
traindb=> \dt
             List of relations
 Schema |      Name      | Type  |  Owner
--------+----------------+-------+----------
 public | books          | table | postgres
 public | books_spark    | table | train
 public | churn          | table | train
 public | world_classics | table | train
(4 rows)
```
- describe table 
```
SELECT 
   table_name, 
   column_name, 
   data_type 
FROM 
   information_schema.columns
WHERE 
   table_name = 'books';
```
Output:
```
 table_name |  column_name   |     data_type
------------+----------------+-------------------
 books      | id             | integer
 books      | book_name      | character varying
 books      | isbn           | bigint
 books      | book_id        | bigint
 books      | price          | double precision
 books      | price_currency | character varying
 books      | rating_count   | integer
 books      | author_id      | integer
 books      | publisher_id   | integer
(9 rows)
```

## copy data from file into table
```
traindb=> create table users(id int, name varchar(30), age int);
CREATE TABLE

traindb=> \q

[train@localhost postgresql]$ psql -h localhost -p 5432 -U train -d traindb -W -c "\copy users FROM 'users.txt' DELIMITERS ',' CSV HEADER;"
Password for user train:
```