C:\Users\Dell>cd/

C:\>cd xampp

C:\xampp>cd mysql

C:\xampp\mysql>cd bin

C:\xampp\mysql\bin>mysql.exe -u root
ERROR 2002 (HY000): Can't connect to MySQL server on 'localhost' (10061)

C:\xampp\mysql\bin>mysql.exe -u root
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 8
Server version: 10.4.28-MariaDB mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> create database company;
 Query OK, 1 row affected (0.003 sec)
MariaDB [(none)]> use company;
Database changed
MariaDB [company]> create table info(customerid int(10),customername varchar(20),orderid int(10),location varchar(10));
Query OK, 0 rows affected (0.051 sec)
MariaDB [company]> desc info;
+--------------+-------------+------+-----+---------+-------+
| Field        | Type        | Null | Key | Default | Extra |
+--------------+-------------+------+-----+---------+-------+
| customerid   | int(10)     | YES  |     | NULL    |       |
| customername | varchar(20) | YES  |     | NULL    |       |
| orderid      | int(10)     | YES  |     | NULL    |       |
| location     | varchar(10) | YES  |     | NULL    |       |
+--------------+-------------+------+-----+---------+-------+
4 rows in set (0.020 sec)

MariaDB [company]> create table information(Cust_Id int Not Null, Name varchar(20) Not Null, Country varchar(20) Not Null, City varchar(20));
Query OK, 0 rows affected (0.051 sec)
MariaDB [company]> desc information;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| Cust_Id | int(11)     | NO   |     | NULL    |       |
| Name    | varchar(20) | NO   |     | NULL    |       |
| Country | varchar(20) | NO   |     | NULL    |       |
| City    | varchar(20) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.029 sec)

MariaDB [company]> create table data (Cust_id int Not Null UNIQUE, Name varchar(20) Not Null, Country varchar(20) Not Null, City varchar(20));
Query OK, 0 rows affected (0.026 sec)

MariaDB [company]> desc data;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| Cust_id | int(11)     | NO   | PRI | NULL    |       |
| Name    | varchar(20) | NO   |     | NULL    |       |
| Country | varchar(20) | NO   |     | NULL    |       |
| City    | varchar(20) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.015 sec)

MariaDB [company]> create table personal_info (Cust_id int Not Null, Name varchar(20) Not Null, Country varchar(20) Not Null, City varchar(20), PRIMARY KEY (Cust_id));
Query OK, 0 rows affected (0.025 sec)

MariaDB [company]> desc personal_info;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| Cust_id | int(11)     | NO   | PRI | NULL    |       |
| Name    | varchar(20) | NO   |     | NULL    |       |
| Country | varchar(20) | NO   |     | NULL    |       |
| City    | varchar(20) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.022 sec)

MariaDB [company]> create table order_info (Order_id int NOT NULL, Order_num int NOT NULL, Cust_id int, PRIMARY KEY (Order_id), FOREIGN KEY (Cust_id) REFERENCES personal_info(Cust_id) );
Query OK, 0 rows affected (0.042 sec)

MariaDB [company]> desc order_info;
+-----------+---------+------+-----+---------+-------+
| Field     | Type    | Null | Key | Default | Extra |
+-----------+---------+------+-----+---------+-------+
| Order_id  | int(11) | NO   | PRI | NULL    |       |
| Order_num | int(11) | NO   |     | NULL    |       |
| Cust_id   | int(11) | YES  | MUL | NULL    |       |
+-----------+---------+------+-----+---------+-------+
3 rows in set (0.016 sec)

MariaDB [company]> show databases;
+--------------------+
| Database           |
+--------------------+
| company            |
| customerdata       |
| information_schema |
| mysql              |
| office             |
| performance_schema |
| phpmyadmin         |
| test               |
+--------------------+
8 rows in set (0.002 sec)

MariaDB [company]> use office;
Database changed
MariaDB [office]> create table data(id int primary key,name varchar(20),age int);
Query OK, 0 rows affected (0.023 sec)

MariaDB [office]> desc data;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int(11)     | NO   | PRI | NULL    |       |
| name  | varchar(20) | YES  |     | NULL    |       |
| age   | int(11)     | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.030 sec)

MariaDB [office]> insert into data(id,name,age)values(1001,'sai',18);
Query OK, 1 row affected (0.078 sec)

MariaDB [office]> insert into data(id,name,age)values(1092,'ram',21);
Query OK, 1 row affected (0.006 sec)

MariaDB [office]> insert into data(id,name,age)values(1023,'hari',19);
Query OK, 1 row affected (0.007 sec)

MariaDB [office]> insert into data(id,name,age)values(1011,'vani',19);
Query OK, 1 row affected (0.005 sec)

MariaDB [office]> select*from data;
+------+------+------+
| id   | name | age  |
+------+------+------+
| 1001 | sai  |   18 |
| 1011 | vani |   19 |
| 1023 | hari |   19 |
| 1092 | ram  |   21 |
+------+------+------+
4 rows in set (0.001 sec)

MariaDB [office]> select*from data where name like '%hello%';
Empty set (0.000 sec)

MariaDB [office]> select*from data where name like '%sai%';
+------+------+------+
| id   | name | age  |
+------+------+------+
| 1001 | sai  |   18 |
+------+------+------+
1 row in set (0.001 sec)

MariaDB [office]> select*from data where age in (15,16);
Empty set (0.001 sec)

MariaDB [office]> select*from data where age in (age>17);
Empty set (0.001 sec)

MariaDB [office]> select*from data where age in (age>18);
Empty set (0.000 sec)

MariaDB [office]> select*from data where age in (18,20);
+------+------+------+
| id   | name | age  |
+------+------+------+
| 1001 | sai  |   18 |
+------+------+------+
1 row in set (0.000 sec)

MariaDB [office]> select*from data where age=19;
+------+------+------+
| id   | name | age  |
+------+------+------+
| 1011 | vani |   19 |
| 1023 | hari |   19 |
+------+------+------+
2 rows in set (0.001 sec)

MariaDB [office]>
