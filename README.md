# Postgres-SQL

### Database : 
    A collection of data that is stored electronically, such as words, numbers, images, videos, and files. The purpose of a database is to make information easily accessible for later use.

    A database is a logically modeled cluster of information [data] that is typically stored on a computer or other type of hardware that is easily accessible in various ways. 

    Example : Relational Databases, Schema flexibility, etc

### DBMS [Data Base Managemant Systems] : 
    A software program that allows users to access, interact with, and manipulate a database. A DBMS can perform functions such as storing, retrieving, and modifying data, managing access, and safeguarding against data loss. 

    A database management system is a computer program or other piece of software that allows one to access, interact with, and manipulate a database.

    Example : Relational database management systems (RDBMS), NoSQL DBMS, Object-Oriented Database Management Systems (OODBMS), etc

<img src="./assets/Pic-1.png" />

**NOTE :** A type of database system that stores data in structured tables (using rows and columns) and uses SQL for managing and querying data.

### SQL [Structured Query Language] :
    Which is used to talk to our databases.
    
    Example: SELECT * FROM person_db;

### Common jargons related to Database :

**Table :** A table is a collect ion of related data
held in a table format wi thin a database.
<img src="./assets/Pic-2.png" />

### Basics Queries : 
- \l --> list all databases
- \q --> quit
- \c db_name --> connect to database
- \dt --> To view all the existing tables.
- \d table_name --> desc a table
- \d+ table_name --> list all column
-  \\! cls --> clear screen

### Most Important/used navigation Queries : 

1) **List down existing databases** : 
```SQL
SELECT datname FROM pg_database;

OR

\l
```

2) **Creating a new Database** :
```SQL
CREATE DATABASE <db_name>;
```

3) **Change a Database** : 
```SQL
\c <db_name>;
```

4) **Deleting a Database** : 
```SQL
DROP DATABASE <db_name>;
```
### What CRUD operation means in SQL ?
- C - Creating a new table and Inserting the data.
- R - Reading data from tables.
- U - Modify/Update data from tables.
- D - Deleting data from tables. 


### Queries for CRUD operations

**1) Createing a new table :**
```sql
CREATE TABLE person (
    id INT,
    name VARCHAR(100),
    city VARCHAR(100)
);

CREATE TABLE person (
    id INT, 
    name ,
    VARCHAR(100), 
    city VARCHAR(50)
);
```

**Inserting the data** : 
```sql
INSERT INTO person(id, name, city)
VALUES (101, ‘Raju’, ‘Delhi’);
```

**2) Reading data from tables :**
```sql
SELECT * FROM <table_name>;

OR 

SELECT <column_name> from students;

OR

SELECT name, city FROM person;
```

**3) Update/Modify data from tables :**
```sql
UPDATE <table_name>
    SET city=’London’
    WHERE id=2;
```

**4) Deleting data from tables :**
```sql
DELETE FROM students
WHERE name='Raju';
```