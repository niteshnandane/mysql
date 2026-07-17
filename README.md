
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
