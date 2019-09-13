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
