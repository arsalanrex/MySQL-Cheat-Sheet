# MySQL-Cheat-Sheat
A basic guide to the workings of MySQL
<hr>
We'll be seeing the working examples of several basic commands on MariaDB:
<hr>
//Starting the mysql.exe
<br><br>
C:ARSALAN\xampp\mysql\bin>mysql.exe -u root <br>
Welcome to the MariaDB monitor. Commands end with ; or \g.<br>
Your MariaDB connection id is 2<br>
Server version: 10.1.31-MariaDB mariadb.org binary distribution<br>
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.<br>
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.<br>
<hr>
//Create database
<br><br>
MariaDB [(none)]> create database student;<br>
Query OK, 1 row affected (0.02 sec)<br>
<hr>
//Use the database<br>
//Create a table student with student_name(sname), student_id(sid) and average_marks(avgmarks)
<br><br>
MariaDB [(none)]> use student;<br>
Database changed<br>
MariaDB [student]> create table topperlist(sname varchar(10),sid int(5),avgmarks int(3));<br>
Query OK, 0 rows affected (0.10 sec)<br>
<hr>
//Insert three distinct values in the table
<br><br>
MariaDB [student]> insert into topperlist values("abs",001,73);<br>
Query OK, 1 row affected (0.01 sec)<br>
MariaDB [student]> insert into topperlist values("bcd",002,73);<br>
Query OK, 1 row affected (0.00 sec)<br>
MariaDB [student]> insert into topperlist values("cde",003,82);<br>
Query OK, 1 row affected (0.01 sec)<br>
<hr>
//To see the description of the table and its contents
<br><br>
MariaDB [student]> desc topperlist;<br>
+--------------------+--------------------------+------------+----------+------------------+--------------+<br>
&nbsp;|
&nbsp;Field&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;Type&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;Null&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;Key&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;Default&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;Extra&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|<br>
+--------------------+--------------------------+------------+----------+------------------+--------------+<br>
&nbsp;|&nbsp;sname&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;varchar(10)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;YES&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;NULL&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|<br>
&nbsp;|
&nbsp;sid&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;int(5)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;YES&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;NULL&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|<br>
&nbsp;|
&nbsp;avgmarks&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;int(3)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;YES&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;NULL&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|<br>
+--------------------+--------------------------+------------+----------+------------------+--------------+<br>
3 rows in set (0.10 sec)<br>
MariaDB [student]> select * from topperlist;<br>
+--------------+------------+--------------------+<br>
&nbsp;|&nbsp;sname&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;sid&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;avgmarks&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|<br>
+--------------+------------+--------------------+<br>
&nbsp;|&nbsp;abs&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;73&nbsp;|<br>
&nbsp;|&nbsp;bcd&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;73&nbsp;|<br>
&nbsp;|&nbsp;cde&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3&nbsp;|
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;82&nbsp;|<br>
+--------------+------------+--------------------+<br>
3 rows in set (0.00 sec)<br>
<hr>
