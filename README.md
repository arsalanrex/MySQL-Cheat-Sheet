# MySQL-Cheat-Sheat
A basic guide to the workings of MySQL
<hr>
We'll be seeing the working examples of several basic commands on MariaDB:
<hr>

#### //Starting mysql.exe

```
C:ARSALAN\xampp\mysql\bin>mysql.exe -u root 
Welcome to the MariaDB monitor. Commands end with ; or \g.
Your MariaDB connection id is 2
Server version: 10.1.31-MariaDB mariadb.org binary distribution
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

<hr>

#### //Create database

```
MariaDB [(none)]> create database student;
Query OK, 1 row affected (0.02 sec)
```
<hr>

#### //Use the database<br>

```
MariaDB [(none)]> use student;
Database changed
```
<hr>

#### //Create a table student with student_name(sname), student_id(sid) and average_marks(avgmarks)
```
MariaDB [student]> create table topperlist(sname varchar(10),sid int(5),avgmarks int(3));
Query OK, 0 rows affected (0.10 sec)
```
<hr>

#### //Insert three distinct values in the table

```
MariaDB [student]> insert into topperlist values("abs",001,73);
Query OK, 1 row affected (0.01 sec)
MariaDB [student]> insert into topperlist values("bcd",002,73);
Query OK, 1 row affected (0.00 sec)
MariaDB [student]> insert into topperlist values("cde",003,82);
Query OK, 1 row affected (0.01 sec)
```
<hr>

#### //To see the description of the table and its contents

```
MariaDB [student]> desc topperlist;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| sname    | varchar(10) | YES  |     | NULL    |       |
| sid      | int(5)      | YES  |     | NULL    |       |
| avgmarks | int(3)      | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
3 rows in set (0.10 sec)
```
<hr>

#### //To see the contents of the table

```
MariaDB [student]> select * from topperlist;
+-------+------+----------+
| sname | sid  | avgmarks |
+-------+------+----------+
| abs   |    1 |       73 |
| bcd   |    2 |       73 |
| cde   |    3 |       82 |
+-------+------+----------+
3 rows in set (0.00 sec)
```
<hr>

#### //Adding a tuple in the table
```
MariaDB [student]> alter table topperlist ADD(rank int(2));
Query OK, 0 rows affected (0.20 sec)
Records: 0 Duplicates: 0 Warnings: 0
```
#### //Results
```
MariaDB [student]> desc topperlist;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| sname    | varchar(10) | YES  |     | NULL    |       |
| sid      | int(5)      | YES  |     | NULL    |       |
| avgmarks | int(3)      | YES  |     | NULL    |       |
| rank     | int(2)      | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.05 sec)

MariaDB [student]> select * from topperlist;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abs   |    1 |       73 | NULL |
| bcd   |    2 |       73 | NULL |
| cde   |    3 |       82 | NULL |
+-------+------+----------+------+
3 rows in set (0.00 sec)
```
<hr>
