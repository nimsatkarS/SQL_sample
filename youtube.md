Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
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
mysql> use data;
Database changed
mysql> create table youtube(ChainelName varchar(20),Suscriber int(10),Videos int(10),TotalLike int(15),Playlist int(10));
Query OK, 0 rows affected, 4 warnings (0.02 sec)

mysql> insert into youtube value('Code With Harry','1.3m','200','12m','32'),('MrIndian Hacker','4m','21m','56','34'),('Carry Minety','1.5m','340','6m','7'),('Asmr','5m','400','50m','43');
ERROR 1265 (01000): Data truncated for column 'Suscriber' at row 1
mysql> ^C
mysql> insert into youtube value('Code With Harry','1.3','200','12','32'),('MrIndian Hacker','4','287','56','20'),('Carry Minety','1.5','340','6','7'),('Asmr','5','400','50','43');
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0
```sql
```
mysql> select * from youtube;
+-----------------+-----------+--------+-----------+----------+
| ChainelName     | Suscriber | Videos | TotalLike | Playlist |
+-----------------+-----------+--------+-----------+----------+
| Code With Harry |         1 |    200 |        12 |       32 |
| MrIndian Hacker |         4 |    287 |        56 |       20 |
| Carry Minety    |         2 |    340 |         6 |        7 |
| Asmr            |         5 |    400 |        50 |       43 |
+-----------------+-----------+--------+-----------+----------+
4 rows in set (0.00 sec)
```sql
```
mysql> select suscriber from youtube;
+-----------+
| suscriber |
+-----------+
|         1 |
|         4 |
|         2 |
|         5 |
+-----------+
4 rows in set (0.00 sec)

mysql> select chainelName from youtube;
+-----------------+
| chainelName     |
+-----------------+
| Code With Harry |
| MrIndian Hacker |
| Carry Minety    |
| Asmr            |
+-----------------+
4 rows in set (0.00 sec)

mysql> select * from youtube where playlist='7';
+--------------+-----------+--------+-----------+----------+
| ChainelName  | Suscriber | Videos | TotalLike | Playlist |
+--------------+-----------+--------+-----------+----------+
| Carry Minety |         2 |    340 |         6 |        7 |
+--------------+-----------+--------+-----------+----------+
1 row in set (0.04 sec)

mysql> select * from youtube where videos>200;
+-----------------+-----------+--------+-----------+----------+
| ChainelName     | Suscriber | Videos | TotalLike | Playlist |
+-----------------+-----------+--------+-----------+----------+
| MrIndian Hacker |         4 |    287 |        56 |       20 |
| Carry Minety    |         2 |    340 |         6 |        7 |
| Asmr            |         5 |    400 |        50 |       43 |
+-----------------+-----------+--------+-----------+----------+
3 rows in set (0.01 sec)
```sql
```
mysql> select min(TotalLike)as smallestTotalLike from youtube;
+-------------------+
| smallestTotalLike |
+-------------------+
|                 6 |
+-------------------+
1 row in set (0.01 sec)
```sql
mysql> select max(suscriber) from youtube where biggestSuscriber;
ERROR 1054 (42S22): Unknown column 'biggestSuscriber' in 'where clause'
```
mysql> select max(suscriber)as biggestSuscriber from youtube;
+------------------+
| biggestSuscriber |
+------------------+
|                5 |
+------------------+
1 row in set (0.00 sec)

mysql> select max(suscriber)as mideSuscriber from youtube;
+---------------+
| mideSuscriber |
+---------------+
|             5 |
+---------------+
1 row in set (0.00 sec)
```sql
```
mysql>  select * from youtube where ChainelName='Asmr' or Suscriber='4';
+-----------------+-----------+--------+-----------+----------+
| ChainelName     | Suscriber | Videos | TotalLike | Playlist |
+-----------------+-----------+--------+-----------+----------+
| MrIndian Hacker |         4 |    287 |        56 |       20 |
| Asmr            |         5 |    400 |        50 |       43 |
+-----------------+-----------+--------+-----------+----------+
2 rows in set (0.00 sec)

mysql>  select * from youtube where Videos='400' or TotalLike='56';
+-----------------+-----------+--------+-----------+----------+
| ChainelName     | Suscriber | Videos | TotalLike | Playlist |
+-----------------+-----------+--------+-----------+----------+
| MrIndian Hacker |         4 |    287 |        56 |       20 |
| Asmr            |         5 |    400 |        50 |       43 |
+-----------------+-----------+--------+-----------+----------+
2 rows in set (0.00 sec)

mysql> select * from youtube order by videos,suscriber desc;
+-----------------+-----------+--------+-----------+----------+
| ChainelName     | Suscriber | Videos | TotalLike | Playlist |
+-----------------+-----------+--------+-----------+----------+
| Code With Harry |         1 |    200 |        12 |       32 |
| MrIndian Hacker |         4 |    287 |        56 |       20 |
| Carry Minety    |         2 |    340 |         6 |        7 |
| Asmr            |         5 |    400 |        50 |       43 |
+-----------------+-----------+--------+-----------+----------+
4 rows in set (0.00 sec)
```sql
