
mysql> create database dbname;
Query OK, 1 row affected (0.07 sec)

mysql> use dbname;
Database changed

mysql> create table users(
    -> id int AUTO_INCREMENT PRIMARY KEY,
    -> name varchar(100)  NOT NULL,
    -> email varchar(100) UNIQUE NOT NULL,
    -> gender ENUM('male','female','other'),
    -> data_of_birth DATE,
    -> create_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> desc users;
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| Field         | Type                          | Null | Key | Default           | Extra             |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| id            | int                           | NO   | PRI | NULL              | auto_increment    |
| name          | varchar(100)                  | NO   |     | NULL              |                   |
| email         | varchar(100)                  | NO   | UNI | NULL              |                   |
| gender        | enum('male','female','other') | YES  |     | NULL              |                   |
| data_of_birth | date                          | YES  |     | NULL              |                   |
| create_at     | timestamp                     | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
6 rows in set (0.03 sec)


mysql> select id ,email from users;
Empty set (0.00 sec)

mysql> select *from users;
Empty set (0.01 sec)


mysql> drop database dbname;
Query OK, 1 row affected (0.02 sec)

mysql> create table users(id int AUTO_INCREMENT PRIMARY KEY,name varchar(100) NOT NULL, email varchar(100) UNIQUE NOT NULL, gender ENUM('male','female','other'),date_of_birth DATE,created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP);


mysql> rename table users to programmer;

mysql> rename table programmer to users;

// add column 
mysql> alter table users add column is_active boolean default true;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0
Query OK, 0 rows affected (0.03 sec)

// drop column
mysql> alter table users drop column is_active;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0


mysql> desc users;
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| Field         | Type                          | Null | Key | Default           | Extra             |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| id            | int                           | NO   | PRI | NULL              | auto_increment    |
| name          | varchar(100)                  | NO   |     | NULL              |                   |
| email         | varchar(100)                  | NO   | UNI | NULL              |                   |
| gender        | enum('male','female','other') | YES  |     | NULL              |                   |
| date_of_birth | date                          | YES  |     | NULL              |                   |
| created_at    | timestamp                     | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
6 rows in set (0.01 sec)

mysql> alter table users modify name varchar(255);
Query OK, 0 rows affected (0.06 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc users ;
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| Field         | Type                          | Null | Key | Default           | Extra             |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| id            | int                           | NO   | PRI | NULL              | auto_increment    |
| name          | varchar(255)                  | YES  |     | NULL              |                   |
| email         | varchar(100)                  | NO   | UNI | NULL              |                   |
| gender        | enum('male','female','other') | YES  |     | NULL              |                   |
| date_of_birth | date                          | YES  |     | NULL              |                   |
| created_at    | timestamp                     | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
6 rows in set (0.00 sec)



mysql> alter table users modify column email varchar(100) after id;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc users ;
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| Field         | Type                          | Null | Key | Default           | Extra             |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| id            | int                           | NO   | PRI | NULL              | auto_increment    |
| email         | varchar(100)                  | YES  | UNI | NULL              |                   |
| name          | varchar(255)                  | YES  |     | NULL              |                   |
| gender        | enum('male','female','other') | YES  |     | NULL              |                   |
| date_of_birth | date                          | YES  |     | NULL              |                   |
| created_at    | timestamp                     | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
6 rows in set (0.00 sec)



mysql> alter table users modify column date_of_birth DATETIME FIRST;
Query OK, 0 rows affected (0.07 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC USERS;
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| Field         | Type                          | Null | Key | Default           | Extra             |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
| date_of_birth | datetime                      | YES  |     | NULL              |                   |
| id            | int                           | NO   | PRI | NULL              | auto_increment    |
| email         | varchar(100)                  | YES  | UNI | NULL              |                   |
| name          | varchar(255)                  | YES  |     | NULL              |                   |
| gender        | enum('male','female','other') | YES  |     | NULL              |                   |
| created_at    | timestamp                     | YES  |     | CURRENT_TIMESTAMP | DEFAULT_GENERATED |
+---------------+-------------------------------+------+-----+-------------------+-------------------+
6 rows in set (0.00 sec)


mysql> insert into users values('2015-07-13',1,'nitesh@gmail.com','nitesh','male',DEFAULT);
Query OK, 1 row affected (0.02 sec)

mysql> select *from users;
+---------------------+----+------------------+--------+--------+---------------------+
| date_of_birth       | id | email            | name   | gender | created_at          |
+---------------------+----+------------------+--------+--------+---------------------+
| 2015-07-13 00:00:00 |  1 | nitesh@gmail.com | nitesh | male   | 2026-07-17 13:21:56 |
+---------------------+----+------------------+--------+--------+---------------------+
1 row in set (0.00 sec)


mysql> insert into users(date_of_birth,email,name,gender) values('2010-10-15','niraj@gmail.com','niraj','male');
Query OK, 1 row affected (0.00 sec)


mysql> select *from users;
+---------------------+----+------------------+--------+--------+---------------------+
| date_of_birth       | id | email            | name   | gender | created_at          |
+---------------------+----+------------------+--------+--------+---------------------+
| 2015-07-13 00:00:00 |  1 | nitesh@gmail.com | nitesh | male   | 2026-07-17 13:21:56 |
| 2010-10-15 00:00:00 |  2 | niraj@gmail.com  | niraj  | male   | 2026-07-17 13:32:09 |
+---------------------+----+------------------+--------+--------+---------------------+
2 rows in set (0.00 sec)

mysql> insert into users(name, email,gender,date_of_birth)values('bharat','bharat@gmail.com','male','2003-01-04'),('rishabh','rishabh@gmail.com','male','2000-03-01');
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql> select *from users;
+---------------------+----+-------------------+---------+--------+---------------------+
| date_of_birth       | id | email             | name    | gender | created_at          |
+---------------------+----+-------------------+---------+--------+---------------------+
| 2015-07-13 00:00:00 |  1 | nitesh@gmail.com  | nitesh  | male   | 2026-07-17 13:21:56 |
| 2010-10-15 00:00:00 |  2 | niraj@gmail.com   | niraj   | male   | 2026-07-17 13:32:09 |
| 2003-01-04 00:00:00 |  3 | bharat@gmail.com  | bharat  | male   | 2026-07-17 14:05:11 |
| 2000-03-01 00:00:00 |  4 | rishabh@gmail.com | rishabh | male   | 2026-07-17 14:05:11 |
+---------------------+----+-------------------+---------+--------+---------------------+
4 rows in set (0.00 sec)
