
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
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
| information_schema |
| item               |
| menagerie          |
| mysql              |
| performance_schema |
| sanket             |
| sys                |
| testdb             |
+--------------------+
8 rows in set (0.01 sec)

mysql> use mysql;
Database changed
mysql> create table Result(StudentName varchar(50),RollNo int(20),Subject varchar(50),Pursentage int(10));
Query OK, 0 rows affected, 2 warnings (0.03 sec)

mysql> desc Result;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| StudentName | varchar(50) | YES  |     | NULL    |       |
| RollNo      | int         | YES  |     | NULL    |       |
| Subject     | varchar(50) | YES  |     | NULL    |       |
| Pursentage  | int         | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)
```
mysql> insert into Result values('Pankaj','64','Sub-7','68%'),('Kartik','75','Sub-5','78%'),('Aniket','12','Sub-8','55%'),('Krishna','23','Sub-7','83%'),('Jays','42','Sub-5','69%'),('Badal','54','Sub-8','49%');
ERROR 1265 (01000): Data truncated for column 'Pursentage' at row 1
mysql> ('Pankaj','64','Sub-7',68),('Kartik','75','Sub-5',78),('Aniket','12','Sub-8',55),('Krishna','23','Sub-7',83),('Jays','42','Sub-5',69),('Badal','54','
Sub-8',49);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''Pankaj','64','Sub-7',68),('Kartik','75','Sub-5',78),('Aniket','12','Sub-8',55),' at line 1
mysql> ('Pankaj','64','Sub-7','68'),('Kartik','75','Sub-5','78'),('Aniket','12','Sub-8','55'),('Krishna','23','Sub-7','83'),('Jays','42','Sub-5','69'),('Bad
al','54','Sub-8','49');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''Pankaj','64','Sub-7','68'),('Kartik','75','Sub-5','78'),('Aniket','12','Sub-8',' at line 1
mysql> ('Pankaj','64','Sub-7','68%'),('Kartik','75','Sub-5','78%'),('Aniket','12','Sub-8','55%');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''Pankaj','64','Sub-7','68%'),('Kartik','75','Sub-5','78%'),('Aniket','12','Sub-8' at line 1
mysql>  insert into Result values('Pankaj','64','Sub-7','68'),('Kartik','75','Sub-5','78'),('Aniket','12','Sub-8','55'),('Krishna','23','Sub-7','83'),('Jays','42','Sub-5','69'),('Bad
    '> al','54','Sub-8','49');
Query OK, 6 rows affected (0.01 sec)
Records: 6  Duplicates: 0  Warnings: 0
```sql
mysql> desc Result;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| StudentName | varchar(50) | YES  |     | NULL    |       |
| RollNo      | int         | YES  |     | NULL    |       |
| Subject     | varchar(50) | YES  |     | NULL    |       |
| Pursentage  | int         | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)
```
```sql
mysql> select * from Result;
+-------------+--------+---------+------------+
| StudentName | RollNo | Subject | Pursentage |
+-------------+--------+---------+------------+
| Pankaj      |     64 | Sub-7   |         68 |
| Kartik      |     75 | Sub-5   |         78 |
| Aniket      |     12 | Sub-8   |         55 |
| Krishna     |     23 | Sub-7   |         83 |
| Jays        |     42 | Sub-5   |         69 |
| Bad
al      |     54 | Sub-8   |         49 |
+-------------+--------+---------+------------+
6 rows in set (0.00 sec)
```
```sql
mysql> select RollNo from Result;
+--------+
| RollNo |
+--------+
|     64 |
|     75 |
|     12 |
|     23 |
|     42 |
|     54 |
+--------+
6 rows in set (0.00 sec)
```
mysql> select Puresntage from Result;
ERROR 1054 (42S22): Unknown column 'Puresntage' in 'field list'
```sql
mysql> select Pursentage from Result;
+------------+
| Pursentage |
+------------+
|         68 |
|         78 |
|         55 |
|         83 |
|         69 |
|         49 |
+------------+
6 rows in set (0.00 sec)
```
```sql
mysql> select StudentName from Result;
+-------------+
| StudentName |
+-------------+
| Pankaj      |
| Kartik      |
| Aniket      |
| Krishna     |
| Jays        |
| Bad
al      |
+-------------+
6 rows in set (0.00 sec)
```
mysql> SELECT DISTINCT Subject FROM Ressult;
ERROR 1146 (42S02): Table 'mysql.ressult' doesn't exist
mysql> select 12 * from Result;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'from Result' at line 1
mysql> seclect 12 from Result;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'seclect 12 from Result' at line 1
mysql> select 12 from RollNo;
ERROR 1146 (42S02): Table 'mysql.rollno' doesn't exist
mysql> select RollNo from 12;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '12' at line 1
mysql> SELECT * FROM Customers
    -> ^C
mysql> ^C
```sql
mysql> select * from Result
    -> where RollNO=12;
+-------------+--------+---------+------------+
| StudentName | RollNo | Subject | Pursentage |
+-------------+--------+---------+------------+
| Aniket      |     12 | Sub-8   |         55 |
+-------------+--------+---------+------------+
1 row in set (0.00 sec)
```
mysql> seclect * from Result where Pursentage=49;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'seclect * from Result where Pursentage=49' at line 1
mysql>  select * from Result
    ->     -> where StudentName=jays;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '-> where StudentName=jays' at line 2
mysql>  select * from Result
    ->     -> where RollNo=42;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '-> where RollNo=42' at line 2
```sql
mysql> select * from Result  where RollNO=42;
+-------------+--------+---------+------------+
| StudentName | RollNo | Subject | Pursentage |
+-------------+--------+---------+------------+
| Jays        |     42 | Sub-5   |         69 |
+-------------+--------+---------+------------+
1 row in set (0.00 sec)
```
mysql> select * from Result where RollNO=64,54;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ',54' at line 1
```sql
mysql>  select * from Result where RollNO=64;
+-------------+--------+---------+------------+
| StudentName | RollNo | Subject | Pursentage |
+-------------+--------+---------+------------+
| Pankaj      |     64 | Sub-7   |         68 |
+-------------+--------+---------+------------+
1 row in set (0.00 sec)
```
mysql>
