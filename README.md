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

## Section 4 : 

### Clauses : 

    The sql clauses can help filter out the data according to the users' needs. 

    - Where
    - Distinct
    - Order By
    - Limit
    - Like

### Relational Operators :

<img src="./assets/Pic-3.png"/>

**Task 1 :** Creating New Table
```sql
CREATE TABLE employees (
  emp_id SERIAL PRIMARY KEY,
  fname VARCHAR(50) NOT NULL,
  lname VARCHAR(50) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  dept VARCHAR(50),
  salary DECIMAL(10,2) DEFAULT 30000.00,
  hire_date DATE NOT NULL DEFAULT CURRENT_DATE
);
```

```sql
INSERT INTO employees (emp_id, fname, lname, email, dept, salary, hire_date)
 VALUES
(1, 'Raj', 'Sharma', 'raj.sharma@example.com', 'IT', 50000.00, '2020-01-15'),
(2, 'Priya', 'Singh', 'priya.singh@example.com', 'HR', 45000.00, '2019-03-22'),
(3, 'Arjun', 'Verma', 'arjun.verma@example.com', 'IT', 55000.00, '2021-06-01'),
(4, 'Suman', 'Patel', 'suman.patel@example.com', 'Finance', 60000.00, '2018-07-30'),
(5, 'Kavita', 'Rao', 'kavita.rao@example.com', 'HR', 47000.00, '2020-11-10'),
(6, 'Amit', 'Gupta', 'amit.gupta@example.com', 'Marketing', 52000.00, '2020-09-25'),
(7, 'Neha', 'Desai', 'neha.desai@example.com', 'IT', 48000.00, '2019-05-18'),
(8, 'Rahul', 'Kumar', 'rahul.kumar@example.com', 'IT', 53000.00, '2021-02-14'),
(9, 'Anjali', 'Mehta', 'anjali.mehta@example.com', 'Finance', 61000.00, '2018-12-03'),
(10, 'Vijay', 'Nair', 'vijay.nair@example.com', 'Marketing', 50000.00, '2020-04-19');
```

**Task 2 :** Find employees whose salary is more than
65000
```sql
SELECT * FROM <table_name>
WHERE salary > 65000.00;
```

**Task 3 :** Find employees whose salary is more than
40000 and Less than 65000
```sql
SELECT * FROM employees
WHERE salary >=40000 AND salary <=65000;
```

### Logical Operators :
- **AND** : When both the conditions are true.
```sql
SELECT * FROM employe
WHERE salary > 50000 AND dept='IT';
```
- **OR** : When either of the condition is true.
```sql
SELECT * FROM employees
    WHERE dept = 'IT'
    OR dept = 'HR'
    OR dept = 'Finance';
```
- **NOT**

- **IN**
```sql
SELECT * FROM employees
WHERE dept = 'IT'
OR dept = 'HR'
OR dept = 'Finance';

-- Instead use this : 
SELECT * FROM employees
WHERE dept IN ('IT' ,'HR','Finance');
```
### Clauses : 

- **BETWEEN**
```sql
SELECT * FROM employees
WHERE salary BETWEEN 40000 AND 65000;
```

- **DISTINCT** : Returns the Unique(Not repeated) first names.
```sql
SELECT DISTINCT fname FROM employe;
```

- **ORDER BY** : For sorting
```sql
-- Ascending order
SELECT * FROM employees ORDER BY fname;

-- Descending order 
SELECT * FROM employees ORDER BY fname DESC; 
```

- **LIMIT** : To set the limit on the data you receive.
```sql
SELECT * FROM employees LIMIT 3;
```

- **LIKE** : To search from data using specific keyword.
```sql
-- To find the name that starts with "Am".
SELECT * FROM employe
    WHERE fname LIKE 'Am%';

-- To find the name that ends with "a".
SELECT * FROM employe
    WHERE fname LIKE '%a';

-- To find the name which has "i" letter in between.
SELECT * FROM employe
    WHERE fname LIKE '%i%';
```
**NOTE :** 
1) Starts with 'A': LIKE 'A%'
2) Ends with 'A': LIKE '%A'
3) Contains 'A': LIKE '%A%'
4) Second character is 'A': LIKE '_A%'
5) Case-insensitive contains 'john': ILIKE '%john%'
6) Department containing 2 letters : '__'

## Section 5 : 

### Aggrigate functions : 

- COUNT
```sql
SELECT COUNT(*) FROM employees;

-- OR

SELECT COUNT(fname) FROM employees;
```

- SUM
```sql
SELECT SUM(salary) FROM employees;
```

- AVG
```sql
SELECT AVG(salary) FROM employees;
```

- MIN
```sql
SELECT Min(salary) FROM employe;
```

- MAX
```sql
SELECT MAX(salary) FROM employe;
```

- GROUP BY : Use Case : No. of employees in each department
```sql
-- Normal Grouping
SELECT dept FROM employees GROUP BY dept;

--  No. of employees in each department
SELECT dept, COUNT(fname) FROM employees GROUP
BY dept;

SELECT dept, SUM(salary) FROM employees GROUP
BY dept;
```

## Section 6 : 

### String Functions : 

- **CONCAT**
```sql
SELECT CONCAT(first_col, sec_col)

-- OR
SELECT CONCAT(first_word, sec_word, ...)

-- OR
SELECT CONCAT(fname, lname) AS fullname FROM employe;
```
**NOTE :** Multiple conditions in a single query
```sql
SELECT emp_id, CONCAT(fname, lname) AS Fullname, dept FROM employe;
```

- **CONCAT_WS**
```sql
-- Normal way
SELECT CONCAT(fname, '-', lname) AS Fullname FROM employe;

-- CONCAT_WS way
SELECT CONCAT_WS(' ', fname, lname) AS Fullname FROM employe
```

- **SUB-STRING**
```sql
SELECT SUBSTRING(fname, 1, 2) FROM employe;

-- OR

SELECT SUBSTR(fname, 1, 2) FROM employe;
```

- **REPLACE**
```sql
-- REPLACE(str, from_str, to_str)

REPLACE('Hey Buddy','Hey','Hello')

SELECT REPLACE(dept, 'IT', 'TECH') FROM employe;
```

- **REVERSE**
```sql
SELECT REVERSE('Hello');

SELECT REVERSE(fname) FROM employe;
```

- **Length**
```sql
SELECT LENGTH(fname) FROM employe;
```

**TAKS :** Enter the query to all the information about the users, whose firstname's length is lesser than 5.
```sql
SELECT * FROM employe WHERE LENGTH(fname) <= 5;
```

- **UPPER CASE and LOWER CASE**
```sql
-- Upper Case : 
SELECT UPPER(fname) FROM employe;

-- Lower Case : 
SELECT LOWER(fname) FROM employe;
```

- **TRIM**
```sql
SELECT TRIM(' Alright! ');

-- SELECT LENGTH(TRIM('   Amith!   '));
```

- **Position**
```sql
SELECT POSITION('om' in ‘Thomas’);
```

## Section 7 : 

### Altering tables : 

- How to add a column ?
```sql
ALTER TABLE person
ADD COLUMN age INT;
```

- How to remove a column ?
```sql
ALTER TABLE person
DROP COLUMN city;
```

- How to rename a column name ?
```sql
ALTER TABLE person
RENAME COLUMN name To full_name;
```

- How to rename a table name ?
```sql
ALTER TABLE person
RENAME TO myPerson;

-- OR

RENAME TABLE person TO myPerson;
```

- How to add DEFAULT value to a column?
```sql
ALTER TABLE myPerson
ALTER COLUMN full_name
SET DATA TYPE VARCHAR(500);

-- AND
ALTER TABLE myPerson
ALTER COLUMN full_name
SET DEFAULT 'unknown';

-- AND
ALTER TABLE myPerson
ALTER COLUMN full_name
SET NOT NULL;
```

### Check Constraints : 
```sql
CREATE TABLE contacts(
    name VAECHAR(50),
    mob VARCHAR(15) UNIQUE CHECK (LENGTH(phone) >= 10)
);
```

### Add or Remove Constraints : 
```sql
-- Add Constraints 
ALTER TABLE contacts
DROP CONSTRAINT mob_no_less_than_10digits;

-- Remove Constraints
ALTER TABLE contacts
ADD CONSTRAINT mob_not_null CHECK(mob != null);
```

### Named Constraints : Throws error in the name we've chosen
```sql
CREATE TABLE contacts(
    name VAECHAR(50),
    mob VARCHAR(15) UNIQUE,
    CONSTRAINT phone_no_less_than_10digits CHECK (LENGTH(phone) >= 10)
);
```

### Case 

    Case in SQL is just like `if` statement in any other programming language.

**TASK 1** : Write the sql queries using cases to arrive to the solution given below
<img src="./assets/Pic-4.png" />

**Solution :**
```sql
SELECT fname, salary,
CASE
    WHEN salary >= 50000 THEN 'High'
    ELSE 'Low'
END AS sal_cat
FROM employees;
```

**NOTE :** We can also give multiple condition
```sql
SELECT fname, salary, 
	CASE
		WHEN salary > 50000 THEN 'High'
		WHEN salary BETWEEN 45000 AND 50000 THEN 'Mid'
		Else 'Low'
END AS salary_category
FROM employe;
```

**TASK 2** : Calculate the bonus upon the salary
<img src="./assets/Pic-5.png" />

**Solution :** 
```sql
SELECT fname, salary, 
	CASE
		WHEN salary > 0 THEN (salary * .10)
END AS bonus
FROM employe;
```

**TASK 3** : 
<img src="./assets/Pic-6.png" />

**Solution :**
```sql
SELECT 
	CASE
		WHEN salary > 50000 THEN 'High'
		WHEN salary BETWEEN 45000 AND 50000 THEN 'Mid'
		Else 'Low'
END AS salary_category, COUNT(emp_id)
FROM employe GROUP BY salary_category;
```

## Section 8 : Realations

Companies won't just have a single table, they'd have multiple tables. We have to define the relationship between each tables.

It's always easier to manage the relationship between the distributed data.

### Types of Relationships : 
- One to One
<img src="./assets/Pic-7.png" />
- One to Many
<img src="./assets/Pic-8.png" />
- Many to Many
<img src="./assets/Pic-9.png" />

**NOTE :** In most of the use cases `one to many` relationship is used.

### Let's Understand a Use-Case of 1:Many

- You have a client for whom you want to create the database as follows : 
<img src="./assets/Pic-10.png" />

- Regular solution : 
<img src="./assets/Pic-11.png" />

**NOTE :** The problem with the regular solution is that there are many duplicate entries.

- The real solution is that you create 2 seperate tables : 
<img src="./assets/Pic-12.png">

- And then define the relationship between the 2 tables
<img src="./assets/Pic-13.png">
<img src="./assets/Pic-14.png">

### Foreign Key :
    While using the primary key of one table in another table, that primary key becomes th foreign key in the table it is being used.
<img src="./assets/Pic-15.png" />

**TASK 1 :** Create 2 tables i.e "customers" and "orders" . 
```sql
CREATE TABLE customers (
    cust_id SERIAL PRIMARY KEY,
    cust_name VARCHAR(100) NOT NULL
);

CREATE TABLE orders (
    ord_id SERIAL PRIMARY KEY,
    ord_date DATE NOT NULL,
    price NUMERIC NOT NULL,
    cust_id INTEGER NOT NULL,
    FOREIGN KEY (cust_id) REFERENCES
    customers (cust_id)
);
```

**TASK 2 :** Insert values
```sql
-- customers table 
INSERT INTO customers (cust_name)
VALUES('Raju'), ('Sham'), ('Paul'), ('Alex');

-- orders
INSERT INTO orders (ord_date, cust_id, price)
VALUES
('2024-01-01', 1, 250.00),
('2024-01-15', 1, 300.00),
('2024-02-01', 2, 150.00),
('2024-03-01', 3, 450.00),
('2024-04-04', 2, 550.00);
```

### JOINS : 
    JOIN operation is used to combine rows from two or more tables based on a related column between them.

    Whenever we maintain relationship with 2 or more tables, we cannot read the data seperately, that's why we use joins.

### Types of JOIN :

1) Cross/Full Join :

        Every row from one table is combined with every row from another table.

```sql
SELECT * FROM customers CROSS JOIN orders;
```

2) Inner Join :

        Returns only the rows where there is a match between the specified columns in both the left (or first) and right (or second) tables.

<img src="./assets/Pic-16.png" />

```sql
SELECT * FROM customers c
INNER JOIN
orders o
ON c.cust_id=o.cust_id;

-- OR
SELECT * FROM customers INNER JOIN orders ON customers.cust_id=orders.cust_id;
```

**Inner Join with Group By**
```sql
SELECT c.cust_name, COUNT(o.ord_id) FROM customers c
INNER JOIN
orders o
ON c.cust_id=o.cust_id
GROUP BY cust_name;

-- 
SELECT c.cust_name, COUNT(o.price) FROM customers c
INNER JOIN
orders o
ON c.cust_id=o.cust_id
GROUP BY cust_name;
```
- Left Join

        Returns all rows from the left (or first) table
        and the matching rows from the right (or
        second) table.

<img src='./assets/Pic-17.png' />

```sql
SELECT * FROM customers c
LEFT JOIN
orders o
ON c.cust_id=o.cust_id;
```
- Right Join

        Returns all rows from the right (or second) table and the matching rows from the left (or first) table.

<img src="./assets/Pic-18.png" />

```sql
SELECT * FROM customers c
RIGHT JOIN
orders o
ON c.cust_id=o.cust_id;
```

### Joining Many-Many relationship tables : 

Let's Understand a Use-Case of Many : Many using the students and courses analogy

<img src="./assets/Pic-19.png" />

One student can enroll into multiple courses : 
<img src="./assets/Pic-20.png" />

And each courses can be enrolled by many other students :
<img src="./assets/Pic-21.png" />

So the tables would be structured this way : 
<img src="./assets/Pic-22.png" />

#### Creating tables and adding the data : 

**NOTE :** Before creating tables create a database named institute.

**Table Creation :**
```sql
-- students table :
CREATE TABLE students (
    s_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

-- courses table :
CREATE TABLE courses (
    c_id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    fee NUMERIC NOT NULL
);

-- enrollment table :
CREATE TABLE enrollment (
    enrollment_id SERIAL PRIMARY KEY,
    s_id INT NOT NULL,
    c_id INT NOT NULL,
    enrollment_date DATE NOT NULL,
    FOREIGN KEY (s_id) REFERENCES students(s_id),
    FOREIGN KEY (c_id) REFERENCES courses(c_id)
)
```

**Inserting the data :**
```sql
-- students data : 
INSERT INTO Students (name) VALUES
('Raju'),
('Sham'),
('Alex');

-- courses data : 
INSERT INTO courses (name, fee)
VALUES
('Mathematics', 500.00),
('Physics', 600.00),
('Chemistry', 700.00);

-- enrollment data : 
INSERT INTO enrollment (s_id, c_id, enrollment_date)
VALUES
(1, 1, '2024-01-01'), -- Raju enrolled in Mathematics
(1, 2, '2024-01-15'), -- Raju enrolled in Physics
(2, 1, '2024-02-01'), -- Sham enrolled in Mathematics
(2, 3, '2024-02-15'), -- Sham enrolled in Chemistry
(3, 3, '2024-03-25'); -- Alex enrolled in Chemistry
```

### Task : 

Create a one-to-many and many-to-many relationship in a
shopping store context using four tables:

- customers
- orders
- products
- order_items

Include a price column in the products table and display
the relationship between customers and their orders,
along with the details of the products in each order.

<img src="./assets/Pic-23.png" />

**Solution :** 

Create a fresh database named "projectdb".

**Creating Tables :**
```sql
-- customers
CREATE TABLE customers (
    cust_id SERIAL PRIMARY KEY,
    cust_name VARCHAR(100) NOT NULL
);

-- orders
CREATE TABLE orders (
    ord_id SERIAL PRIMARY KEY,
    ord_date DATE NOT NULL,
    cust_id INTEGER NOT NULL,
    FOREIGN KEY (cust_id) REFERENCES customers(cust_id)
);

-- order_items
CREATE TABLE order_items (
    item_id SERIAL PRIMARY KEY,
    ord_id INTEGER NOT NULL,
    p_id INTEGER NOT NULL,
    quantity INTEGER NOT NULL,
    FOREIGN KEY (ord_id) REFERENCES orders(ord_id),
    FOREIGN KEY (p_id) REFERENCES products(p_id)
);

-- products
CREATE TABLE products (
    p_id SERIAL PRIMARY KEY,
    p_name VARCHAR(100) NOT NULL,
    price NUMERIC NOT NULL
);
```

**Inserting data into Tables :**
```sql
-- customers
INSERT INTO customers (cust_name)
VALUES ('Raju'), ('Sham'), ('Paul'), ('Alex');

-- orders
INSERT INTO orders (ord_date, cust_id)
VALUES
    ('2024-01-01', 1),  -- Raju first order
    ('2024-02-01', 2),  -- Sham first order
    ('2024-03-01', 3),  -- Paul first order
    ('2024-04-04', 2);  -- Sham second order

-- order_items
INSERT INTO order_items (ord_id, p_id, quantity)
VALUES
    (1, 1, 1),  -- Raju ordered 1 Laptop
    (1, 4, 2),  -- Raju ordered 2 Cables
    (2, 1, 1),  -- Sham ordered 1 Laptop
    (3, 2, 1),  -- Paul ordered 1 Mouse
    (3, 4, 5),  -- Paul ordered 5 Cables
    (4, 3, 1);  -- Sham ordered 1 Keyboard

-- products
INSERT INTO products (p_name, price)
VALUES
    ('Laptop', 55000.00),
    ('Mouse', 500),
    ('Keyboard', 800.00),
    ('Cable', 250.00);
```

**Final Solution :**
```sql
SELECT 
	c.cust_name,
	o.ord_id,
	o.ord_date,
	p.p_name,
	oi.quantity,
	p.price,
	(oi.quantity * p.price) AS total_price
		FROM order_items oi
		JOIN
			products p ON oi.p_id=p.p_id
		JOIN
			orders o ON oi.ord_id=o.ord_id
		JOIN 
			customers c ON c.cust_id=o.cust_id;
```

### VIEWS : 
<img src="./assets/Pic-24.png" />

```sql
SELECT * FROM billing_info;
```

**NOTE :** Using the above query we'll get the same results as we got by running the query mentioned in the above image.