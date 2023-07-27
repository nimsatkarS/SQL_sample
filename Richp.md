# Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 12
Server version: 8.0.32 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```sql
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| data               |
| information_schema |
| item               |
| menagerie          |
| mysql              |
| performance_schema |
| sanket             |
| sys                |
| testdb             |
+--------------------+
9 rows in set (0.00 sec)
```
```sql
mysql> use data;
Database changed
mysql> create table  Richp(Name varchar(40),Networth int(100),Companies varchar(150),Shaires int(50),Score int(5));
Query OK, 0 rows affected, 3 warnings (0.01 sec)
```
mysql> insert into Richp values('Elon Musk','24 240','Tesla Specix','75p','4'),('Jef Bezos','15 150','Amazon','85p','4.5'),('Bil Geats','12 070','Microsoft','67p','5'),('Ambani','8910','Relance','80p','4.3');
ERROR 1265 (01000): Data truncated for column 'Networth' at row 1
mysql>  insert into Richp values('Elon Musk','24240','Tesla Specix','75p','4'),('Jef Bezos','15150','Amazon','85p','4.5'),('Bil Geats','12070','Microsoft','
67p','5'),('Ambani','8910','Relance','80p','4.3');
ERROR 1265 (01000): Data truncated for column 'Shaires' at row 1
mysql>  insert into Richp values('Elon Musk','24 240','Tesla Specix','75','4'),('Jef Bezos','15 150','Amazon','85','4.5'),('Bil Geats','12 070','Microsoft',
'67','5'),('Ambani','8910','Relance','80','4.3');
ERROR 1265 (01000): Data truncated for column 'Networth' at row 1
mysql> insert into Richp values('Elon Musk','24240','Tesla Specix','75p','4'),('Jef Bezos','15150','Amazon','85p','4.5'),('Bil Geats','12070','Microsoft','
    '> 67p','5'),('Ambani','8910','Relance','80p','4.3');^C
mysql> ^C
mysql> insert into Richp values('Elon Musk','24240','Tesla Specix','75p','4'),('Jef Bezos','15150','Amazon','85p','4.5'),('Bil Geats','12070','Microsoft','
    '> insert into Richp values('Elon Musk','24240','Tesla Specix','75p','4'),('Jef Bezos','15150','Amazon','85p','4.5'),('Bil Geats','12070','Microsoft','
    ->
    ->
    ->
    ->
    ->
    ->
    ->
    -> ^C
    ```sql
mysql>  insert into Richp values('Elon Musk','24240','Tesla Specix','75','4'),('Jef Bezos','15150','Amazon','85','4.5'),('Bil Geats','12070','Microsoft','67
','5'),('Ambani','8910','Relance','80','4.3');
Query OK, 4 rows affected (0.00 sec)
Records: 4  Duplicates: 0  Warnings: 0
```
mysql> select from * Richp;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'from * Richp' at line 1
```sql
mysql> select * from Richp;
+-----------+----------+--------------+---------+-------+
| Name      | Networth | Companies    | Shaires | Score |
+-----------+----------+--------------+---------+-------+
| Elon Musk |    24240 | Tesla Specix |      75 |     4 |
| Jef Bezos |    15150 | Amazon       |      85 |     5 |
| Bil Geats |    12070 | Microsoft    |      67 |     5 |
| Ambani    |     8910 | Relance      |      80 |     4 |
+-----------+----------+--------------+---------+-------+
4 rows in set (0.00 sec)
```
mysql> select * from Networth;
ERROR 1146 (42S02): Table 'data.networth' doesn't exist
mysql> select Networth from Richp
    ->
    -> ^C
mysql> select Netwirth from Richp;
ERROR 1054 (42S22): Unknown column 'Netwirth' in 'field list'
```sql
mysql> select Networth from Richp;
+----------+
| Networth |
+----------+
|    24240 |
|    15150 |
|    12070 |
|     8910 |
+----------+
4 rows in set (0.00 sec)
```
```sql
mysql> select Shaires from Richp;
+---------+
| Shaires |
+---------+
|      75 |
|      85 |
|      67 |
|      80 |
+---------+
4 rows in set (0.00 sec)
```
```sql
mysql> select * from Richp where Score='5';
+-----------+----------+-----------+---------+-------+
| Name      | Networth | Companies | Shaires | Score |
+-----------+----------+-----------+---------+-------+
| Jef Bezos |    15150 | Amazon    |      85 |     5 |
| Bil Geats |    12070 | Microsoft |      67 |     5 |
+-----------+----------+-----------+---------+-------+
2 rows in set (0.00 sec)

mysql> select * from Richp where shaires='67';
+-----------+----------+-----------+---------+-------+
| Name      | Networth | Companies | Shaires | Score |
+-----------+----------+-----------+---------+-------+
| Bil Geats |    12070 | Microsoft |      67 |     5 |
+-----------+----------+-----------+---------+-------+
1 row in set (0.00 sec)

mysql> select * from Richp where Companies='amazon';
+-----------+----------+-----------+---------+-------+
| Name      | Networth | Companies | Shaires | Score |
+-----------+----------+-----------+---------+-------+
| Jef Bezos |    15150 | Amazon    |      85 |     5 |
+-----------+----------+-----------+---------+-------+
1 row in set (0.00 sec)
```
mysql> select * from Richp Name='ambani';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '='ambani'' at line 1
```sql
mysql> select * from Richp Where Name='ambani';
+--------+----------+-----------+---------+-------+
| Name   | Networth | Companies | Shaires | Score |
+--------+----------+-----------+---------+-------+
| Ambani |     8910 | Relance   |      80 |     4 |
+--------+----------+-----------+---------+-------+
1 row in set (0.00 sec)

mysql> SELECT * FROM Richp where Networth > 12070;
+-----------+----------+--------------+---------+-------+
| Name      | Networth | Companies    | Shaires | Score |
+-----------+----------+--------------+---------+-------+
| Elon Musk |    24240 | Tesla Specix |      75 |     4 |
| Jef Bezos |    15150 | Amazon       |      85 |     5 |
+-----------+----------+--------------+---------+-------+
2 rows in set (0.00 sec)

mysql> select * from Richp where networth < 12070;
+--------+----------+-----------+---------+-------+
| Name   | Networth | Companies | Shaires | Score |
+--------+----------+-----------+---------+-------+
| Ambani |     8910 | Relance   |      80 |     4 |
+--------+----------+-----------+---------+-------+
1 row in set (0.00 sec)

mysql> select * from Richp where networth >= 8910;
+-----------+----------+--------------+---------+-------+
| Name      | Networth | Companies    | Shaires | Score |
+-----------+----------+--------------+---------+-------+
| Elon Musk |    24240 | Tesla Specix |      75 |     4 |
| Jef Bezos |    15150 | Amazon       |      85 |     5 |
| Bil Geats |    12070 | Microsoft    |      67 |     5 |
| Ambani    |     8910 | Relance      |      80 |     4 |
+-----------+----------+--------------+---------+-------+
4 rows in set (0.00 sec)
```
mysql> select * ffrom richp where networth <> 12070;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ffrom richp where networth <> 12070' at line 1
```sql
mysql> select * from richp where networth <> 12070;
+-----------+----------+--------------+---------+-------+
| Name      | Networth | Companies    | Shaires | Score |
+-----------+----------+--------------+---------+-------+
| Elon Musk |    24240 | Tesla Specix |      75 |     4 |
| Jef Bezos |    15150 | Amazon       |      85 |     5 |
| Ambani    |     8910 | Relance      |      80 |     4 |
+-----------+----------+--------------+---------+-------+
3 rows in set (0.00 sec)
```
mysql>
