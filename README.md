# MySQL-Cheat-Sheet
A basic guide to the workings of MySQL
<hr>
We'll be seeing the working examples of several basic commands on MariaDB:
<hr>

## DDL (Data definition language)
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

#### //Adding a tuple rank in the table
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

#### //Modify Command to change datatype of rank
```
MariaDB [student]> alter table topperlist MODIFY rank varchar(3);
Query OK, 3 rows affected (0.32 sec)
Records: 3 Duplicates: 0 Warnings: 0
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
| rank     | varchar(3)  | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)
```
<hr>

## DML (Data Manipulation Language)
<hr>

#### //Use update
```
MariaDB [student]> update topperlist set sname="abc" where sid=1;
Query OK, 1 row affected (0.02 sec)
Rows matched: 1 Changed: 1 Warnings: 0

MariaDB [student]> select * from topperlist;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
| bcd   |    2 |       73 | NULL |
| cde   |    3 |       82 | NULL |
+-------+------+----------+------+
3 rows in set (0.00 sec)
```
<hr>

#### //Apply conditional delete
```
MariaDB [student]> delete from topperlist where sid=3;
Query OK, 1 row affected (0.01 sec)

MariaDB [student]> select * from topperlist;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
| bcd   |    2 |       73 | NULL |
+-------+------+----------+------+
2 rows in set (0.00 sec)
```
<hr>

#### //Insert into the table
```
MariaDB [student]> insert into topperlist(sname,sid,avgmarks)
values("cde",003,82);
Query OK, 1 row affected (0.01 sec)

MariaDB [student]> select * from topperlist;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
| bcd   |    2 |       73 | NULL |
| cde   |    3 |       82 | NULL |
+-------+------+----------+------+
3 rows in set (0.00 sec)

MariaDB [student]> insert into topperlist(sname,sid,avgmarks)
values("cde",004,86);
Query OK, 1 row affected (0.01 sec)

MariaDB [student]> select * from topperlist;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
| bcd   |    2 |       73 | NULL |
| cde   |    3 |       82 | NULL |
| cde   |    4 |       86 | NULL |
+-------+------+----------+------+
4 rows in set (0.00 sec)
```
<hr>

## DQL (Data Query Language)
<hr>

#### //Select distinct elements

```
MariaDB [student]> select distinct sname from topperlist;
+-------+
| sname |
+-------+
| abc   |
| bcd   |
| cde   |
+-------+
3 rows in set (0.01 sec)
```
<hr>

#### //Select particular column
```
MariaDB [student]> select sname from topperlist;
+-------+
| sname |
+-------+
| abc   |
| bcd   |
| cde   |
| cde   |
+-------+
4 rows in set (0.00 sec)
```
<hr>

#### //Select with constraints
```
MariaDB [student]> select * from topperlist where avgmarks=73;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
| bcd   |    2 |       73 | NULL |
+-------+------+----------+------+
2 rows in set (0.01 sec)
```
<hr>

#### //Select using Order By
```
MariaDB [student]> select * from topperlist order by sid;
+-------+------+----------+------+
| sname | sid | avgmarks | rank |
+-------+------+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| cde   |   4 |       86 | NULL |
+-------+------+----------+------+
4 rows in set (0.01 sec)
```
<hr>

#### //Select with multiple constraints using AND
```
MariaDB [student]> select * from topperlist where sname="cde" AND sid=3;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| cde   |    3 |       82 | NULL |
+-------+------+----------+------+
1 row in set (0.01 sec)
```
<hr>

#### //Select with multiple constraints using OR
```
MariaDB [student]> select * from topperlist where sname="cde" OR sid=3;
+-------+------+----------+------+
| sname | sid | avgmarks | rank |
+-------+------+----------+------+
| cde   |   3 |       82 | NULL |
| cde   |   4 |       86 | NULL |
+-------+------+----------+------+
2 rows in set (0.00 sec)
```
<hr>

#### //Select with constraints using NOT
```
MariaDB [student]> select * from topperlist where NOT sname="cde";
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
| bcd   |    2 |       73 | NULL |
+-------+------+----------+------+
2 rows in set (0.00 sec)
```
<hr>

#### //Select with constraints using BETWEEN
```
MariaDB [student]> select * from topperlist where sid BETWEEN 2 AND 4;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| bcd   |    2 |       73 | NULL |
| cde   |    3 |       82 | NULL |
| cde   |    4 |       86 | NULL |
+-------+------+----------+------+
3 rows in set (0.00 sec)
```
<hr>

#### //Select with constraints using NOT BETWEEN
```
MariaDB [student]> select * from topperlist where sid NOT BETWEEN 2 AND 4;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
+-------+------+----------+------+
1 row in set (0.00 sec)
```
<hr>

#### //Select with constraints using LIKE
```
MariaDB [student]> select * from topperlist where sname LIKE 'a%';
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
+-------+------+----------+------+
1 row in set (0.00 sec)
```
<hr>

#### //Select with constraints using IN
```
MariaDB [student]> select * from topperlist where sid IN (2,4);
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| bcd   |    2 |       73 | NULL |
| cde   |    4 |       86 | NULL |
+-------+------+----------+------+
2 rows in set (0.00 sec)
```
<hr>

#### //Select with constraints using NOT IN
```
MariaDB [student]> select * from topperlist where sid NOT IN (2,4);
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
| cde   |    3 |       82 | NULL |
+-------+------+----------+------+
2 rows in set (0.00 sec)
```
<hr>

#### //Results
```
MariaDB [student]> desc topperlist;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| sname    | varchar(10) | YES  |     | NULL    |       |
| sid      | int(5)      | YES  |     | NULL    |       |
| avgmarks | int(3)      | YES  |     | NULL    |       |
| rank     | varchar(3)  | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.08 sec)

MariaDB [student]> select * from topperlist;
+-------+------+----------+------+
| sname | sid  | avgmarks | rank |
+-------+------+----------+------+
| abc   |    1 |       73 | NULL |
| bcd   |    2 |       73 | NULL |
| cde   |    3 |       82 | NULL |
| cde   |    4 |       86 | NULL |
+-------+------+----------+------+
4 rows in set (0.00 sec)
```
<hr>

### Constraints
<hr>

#### //UNIQUE
```
MariaDB [student]> alter table topperlist ADD unique(sid);
Query OK, 0 rows affected (0.07 sec)
Records: 0 Duplicates: 0 Warnings: 0

MariaDB [student]> desc topperlist;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| sname    | varchar(10) | YES  |     | NULL    |       |
| sid      | int(5)      | YES  | UNI | NULL    |       |
| avgmarks | int(3)      | YES  |     | NULL    |       |
| rank     | varchar(3)  | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.04 sec)
```
#### //PRIMARY KEY
```
MariaDB [student]> alter table topperlist ADD primary key(sid);
Query OK, 4 rows affected (0.25 sec)
Records: 4 Duplicates: 0 Warnings: 0

MariaDB [student]> desc topperlist;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| sname    | varchar(10) | YES  |     | NULL    |       |
| sid      | int(5)      | NO   | PRI | NULL    |       |
| avgmarks | int(3)      | YES  |     | NULL    |       |
| rank     | varchar(3)  | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.05 sec)

MariaDB [student]> update topperlist set sname="def" where sid=4;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1 Changed: 1 Warnings: 0

MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
+-------+-----+----------+------+
4 rows in set (0.00 sec)
```
#### //NOT NULL
```
MariaDB [student]> alter table topperlist MODIFY sname varchar(10) NOT NULL;
Query OK, 4 rows affected (0.25 sec)
Records: 4 Duplicates: 0 Warnings: 0

MariaDB [student]> desc topperlist;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| sname    | varchar(10) | NO   |     | NULL    |       |
| sid      | int(5)      | NO   | PRI | NULL    |       |
| avgmarks | int(3)      | YES  |     | NULL    |       |
| rank     | varchar(3)  | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.06 sec)
```
#### //NULL
```
MariaDB [student]> alter table topperlist MODIFY sname varchar(10) NULL;
Query OK, 0 rows affected (0.16 sec)
Records: 0 Duplicates: 0 Warnings: 0

MariaDB [student]> desc topperlist;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| sname    | varchar(10) | YES  |     | NULL    |       |
| sid      | int(5)      | NO   | PRI | NULL    |       |
| avgmarks | int(3)      | YES  |     | NULL    |       |
| rank     | varchar(3)  | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
4 rows in set (0.04 sec)
```
#### //DEFAULT VALUES
```
MariaDB [student]> alter table topperlist alter rank set default "1st";
Query OK, 0 rows affected (0.03 sec)
Records: 0 Duplicates: 0 Warnings: 0

MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
+-------+-----+----------+------+
4 rows in set (0.00 sec)

MariaDB [student]> insert into topperlist(sname,sid,avgmarks) values("efg",005,87);
Query OK, 1 row affected (0.01 sec)

MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
| efg   |   5 |       87 | 1st  |
+-------+-----+----------+------+
5 rows in set (0.00 sec)
```
#### //FOREIGN KEY
```
MariaDB [student]> create table teacher(tname varchar(10),tid int(5));
Query OK, 0 rows affected (0.09 sec)

MariaDB [student]> desc teacher;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| tname | varchar(10) | YES  |     | NULL    |       |
| tid   | int(5)      | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.05 sec)

MariaDB [student]> alter table teacher ADD foreign key(tid) references
topperlist(sid);
Query OK, 0 rows affected (0.25 sec)
Records: 0 Duplicates: 0 Warnings: 0

MariaDB [student]> desc teacher;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| tname | varchar(10) | YES  |     | NULL    |       |
| tid   | int(5)      | YES  | MUL | NULL    |       |
+-------+-------------+------+-----+---------+-------+
2 rows in set (0.06 sec)
```
<hr>

## TCL (Transactional Control Language)
<hr>

#### //Current table state
```
MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
| efg   |   5 |       87 | 1st  |
+-------+-----+----------+------+
5 rows in set (0.00 sec)
```
<hr>

#### //Start transaction and create a Savepoint
```
MariaDB [student]> start transaction;
Query OK, 0 rows affected (0.00 sec)

MariaDB [student]> savepoint s1;
Query OK, 0 rows affected (0.00 sec)

MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
| efg   |   5 |       87 | 1st  |
+-------+-----+----------+------+
5 rows in set (0.00 sec)
```
<hr>

#### //Work on the table
```
MariaDB [student]> delete from topperlist where sid=5;
Query OK, 1 row affected (0.00 sec)

MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
+-------+-----+----------+------+
4 rows in set (0.00 sec)
```
<hr>

#### //Rollback to Savepoint and view table
```
MariaDB [student]> rollback to s1;
Query OK, 0 rows affected (0.01 sec)

MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
| efg   |   5 |       87 | 1st  |
+-------+-----+----------+------+
5 rows in set (0.00 sec)
```
<hr>

## //Built-in Functions
<hr>

### //Group Functions
<hr>

#### //Display the table
```
MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
| efg   |   5 |       87 | 1st  |
+-------+-----+----------+------+
5 rows in set (0.00 sec)
```
<hr>

#### //Select with AVG 
```
MariaDB [student]> select AVG(avgmarks) from topperlist;
+---------------+
| AVG(avgmarks) |
+---------------+
|       80.2000 |
+---------------+
1 row in set (0.01 sec)
```
<hr>

#### //Select with MAX
```
MariaDB [student]> select MAX(avgmarks) from topperlist;
+---------------+
| MAX(avgmarks) |
+---------------+
|            87 |
+---------------+
1 row in set (0.00 sec)
```
<hr>

#### //Select with SUM
```
MariaDB [student]> select SUM(avgmarks) from topperlist;
+---------------+
| SUM(avgmarks) |
+---------------+
|           401 |
+---------------+
1 row in set (0.00 sec)
```
<hr>

#### //Select with MIN
```
MariaDB [student]> select MIN(avgmarks) from topperlist;
+---------------+
| MIN(avgmarks) |
+---------------+
|            73 |
+---------------+
1 row in set (0.01 sec)
```
<hr>

#### //Select with COUNT
```
MariaDB [student]> select COUNT(avgmarks) from topperlist;
+-----------------+
| COUNT(avgmarks) |
+-----------------+
|               5 |
+-----------------+
1 row in set (0.00 sec)
```

<hr>

### //Character Functions
<hr>

#### //Display the table
```
MariaDB [student]> select * from topperlist;
+-------+-----+----------+------+
| sname | sid | avgmarks | rank |
+-------+-----+----------+------+
| abc   |   1 |       73 | NULL |
| bcd   |   2 |       73 | NULL |
| cde   |   3 |       82 | NULL |
| def   |   4 |       86 | NULL |
| efg   |   5 |       87 | 1st  |
+-------+-----+----------+------+
5 rows in set (0.00 sec)
```
<hr>

#### //Select with LOWER
```
MariaDB [student]> select LOWER('Example') from topperlist;
+------------------+
| LOWER('Example') |
+------------------+
| example          |
| example          |
| example          |
| example          |
| example          |
+------------------+
5 rows in set (0.00 sec)
```
<hr>

#### //Select with UPPER
```
MariaDB [student]> select UPPER('Example') from topperlist;
+------------------+
| UPPER('Example') |
+------------------+
| EXAMPLE          |
| EXAMPLE          |
| EXAMPLE          |
| EXAMPLE          |
| EXAMPLE          |
+------------------+
5 rows in set (0.00 sec)
```
<hr>
