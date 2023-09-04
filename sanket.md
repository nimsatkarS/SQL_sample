Enter password: *******
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.32 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases
    -> ;
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
| tution             |
+--------------------+
10 rows in set (0.03 sec)

mysql> use data;
Database changed
mysql> create table ithub(name varchar(30),corse varchar(20),fees int(20),paid int(20),contact int(10));
Query OK, 0 rows affected, 3 warnings (0.03 sec)

mysql> desc ithub;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| name    | varchar(30) | YES  |     | NULL    |       |
| corse   | varchar(20) | YES  |     | NULL    |       |
| fees    | int         | YES  |     | NULL    |       |
| paid    | int         | YES  |     | NULL    |       |
| contact | int         | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
5 rows in set (0.01 sec)
```sql
mysql> insert into ithub values('sanket','python','5000','3000','9823415986'),('mayur','java','4000','2000','9874563210'),('rohit','c/c++','3500','1000','9632587419'),('mahesh','c#','8000','000','7538691248'),('dheraj','webd','1200','6000','9512364785');
ERROR 1264 (22003): Out of range value for column 'contact' at row 1
mysql> insert into ithub values('sanket','python','5000','3000','9823415986'),('mayur','java','4000','2000','9874563210'),('rohit','c/c++','3500','1000','9632587419'),('mahesh','c#','8000','000','7538691248'),('dheraj','webd','1200','6000','9512364785');
ERROR 1264 (22003): Out of range value for column 'contact' at row 1
```
mysql> insert into ithub values('sanket','python','5000','3000','982341'),('mayur','java','4000','2000','987456'),('rohit','c/c++','3500','1000','963258'),('mahesh','c#','8000','000','753869'),('dheraj','webd','1200','6000','951236');
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> desc ithub;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| name    | varchar(30) | YES  |     | NULL    |       |
| corse   | varchar(20) | YES  |     | NULL    |       |
| fees    | int         | YES  |     | NULL    |       |
| paid    | int         | YES  |     | NULL    |       |
| contact | int         | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
5 rows in set (0.00 sec)
```sql
mysql> show table * from ithub;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '* from ithub' at line 1
mysql> show table from * ithub;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'from * ithub' at line 1
```
mysql> select * from ithub;
+--------+--------+------+------+---------+
| name   | corse  | fees | paid | contact |
+--------+--------+------+------+---------+
| sanket | python | 5000 | 3000 |  982341 |
| mayur  | java   | 4000 | 2000 |  987456 |
| rohit  | c/c++  | 3500 | 1000 |  963258 |
| mahesh | c#     | 8000 |    0 |  753869 |
| dheraj | webd   | 1200 | 6000 |  951236 |
+--------+--------+------+------+---------+
5 rows in set (0.00 sec)

mysql> select corse,fees from ithub;
+--------+------+
| corse  | fees |
+--------+------+
| python | 5000 |
| java   | 4000 |
| c/c++  | 3500 |
| c#     | 8000 |
| webd   | 1200 |
+--------+------+
5 rows in set (0.00 sec)
```sql
mysql> select name,contact,corse,from ithub;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'from ithub' at line 1
```
mysql> select name,contact from ithub;
+--------+---------+
| name   | contact |
+--------+---------+
| sanket |  982341 |
| mayur  |  987456 |
| rohit  |  963258 |
| mahesh |  753869 |
| dheraj |  951236 |
+--------+---------+
5 rows in set (0.00 sec)

mysql> select distinct corse from ithub;
+--------+
| corse  |
+--------+
| python |
| java   |
| c/c++  |
| c#     |
| webd   |
+--------+
5 rows in set (0.00 sec)

mysql> select count(distinct paid) from ithub;
+----------------------+
| count(distinct paid) |
+----------------------+
|                    5 |
+----------------------+
1 row in set (0.00 sec)

mysql> select count(distinct contact) from ithub;
+-------------------------+
| count(distinct contact) |
+-------------------------+
|                       5 |
+-------------------------+
1 row in set (0.00 sec)
```sql
mysql> select count(*) as distinctcontact from(select distinct name from ithub);
ERROR 1248 (42000): Every derived table must have its own alias
mysql> select * from ithub where corse;
Empty set, 4 warnings (0.01 sec)
```
mysql> select * from ithub where corse=1;
Empty set, 4 warnings (0.00 sec)

mysql> select * from ithub order by corse;
+--------+--------+------+------+---------+
| name   | corse  | fees | paid | contact |
+--------+--------+------+------+---------+
| rohit  | c/c++  | 3500 | 1000 |  963258 |
| mahesh | c#     | 8000 |    0 |  753869 |
| mayur  | java   | 4000 | 2000 |  987456 |
| sanket | python | 5000 | 3000 |  982341 |
| dheraj | webd   | 1200 | 6000 |  951236 |
+--------+--------+------+------+---------+
5 rows in set (0.00 sec)

mysql> select * from ithub order by paid,fees;
+--------+--------+------+------+---------+
| name   | corse  | fees | paid | contact |
+--------+--------+------+------+---------+
| mahesh | c#     | 8000 |    0 |  753869 |
| rohit  | c/c++  | 3500 | 1000 |  963258 |
| mayur  | java   | 4000 | 2000 |  987456 |
| sanket | python | 5000 | 3000 |  982341 |
| dheraj | webd   | 1200 | 6000 |  951236 |
+--------+--------+------+------+---------+
5 rows in set (0.00 sec)
```sql
mysql> select * from ithub where name = 'sanket' and corse = 'python' and fees > 5000;
Empty set (0.00 sec)

mysql>  ```
