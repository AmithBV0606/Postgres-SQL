# Postgres-SQL

## Section 1 : Theory
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

## Section 2 : CRUD Queries

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

CREATE TABLE students (
    id INT, 
    name  VARCHAR(100), 
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
<!-- ________________________________________________ -->

### Usage of "WHERE" keyword.

**Reading the data :** 
```sql
SELECT * FROM <table_name>
    WHERE   name = "Raju";
```

**Updating the data :** 
```sql
UPDATE <table_name> SET contact=1234 WHERE id=102;
```

**Deleting the data :** 
```sql
DELETE FROM <table_name> WHERE id=104;
```

## Section 3 : 
Official documentation : [Click Here](https://www.postgresql.org/docs/current/datatype.html)
### DataTypes
    An attribute that specifies the type of data in a column of our database - table.

### Most widely used are
- **Numeric** - INT, DOUBLE, FLOAT and DECIMAL
```txt
DECIMAL(5,2) 

5 => Represents Total Digits
2 => Represents Number of Digits after Decimal.

Example : 

Correct way
155.38
119.12
28.15

Incorrect way
1150.15
```
- **String** - VARCHAR
- **Date** - DATE
- **Boolean** - BOOLEAN

### Contraints 
    A constraint in PostgreSQL is a rule applied to a column.

### Commonly used constraints are : 

**Primary Key** : 

    The PRIMARY KEY constraint uniquely identifies each
    record in a table.

    Primary keys must contain UNIQUE values, and cannot
    contain NULL values.

    A table can have only ONE primary key.

**NOT NULL** : 
```sql
CREATE TABLE customers(
    id INT NOT NULL,
    name VARCHAR(100) NOT NULL
);
```

**Default** : 
```sql
CREATE TABLE customers(
    acc_no INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    acc_type VARCHAR(50) NOT NULL DEFAULT "Savings"
);
```

**Serial (Auto Increment)** : 
```sql
CREATE TABLE customers(
    id SERIAL NOT NULL,
);
```

**Unique** : 
```sql
CREATE TABLE customers(
    acc_no INT UNIQUE PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    acc_type VARCHAR(50) NOT NULL DEFAULT "Savings"
);
```