# Exercises

### Task 1 = "1:Raj:Sharma:IT"
```sql
SELECT CONCAT_WS(':', emp_id, fname, lname, dept) FROM employe WHERE emp_id=1;
```

### Task 2 = "1:Raju Sharma:IT:50000"
```sql
SELECT CONCAT_WS(':', emp_id, CONCAT_WS(' ', fname, lname), dept, salary) FROM employe WHERE emp_id=1;
```

### Task 3 = "4:Suman:FINANCE"
```sql
SELECT CONCAT_WS(':', emp_id, fname, UPPER(dept)) FROM employe WHERE emp_id=4;
```

### Task 4 = "Task4 I1 Raju H2 Priya"
```sql
SELECT CONCAT(SUBSTR(dept, 1, 1), emp_id), fname FROM employe;
```

### Task 5 = Find Different type of departments in database?
```sql
SELECT DISTINCT dept FROM employe;
```

### Task 6 = Display records with High to low(Ascending Order) salary
```sql
SELECT * FROM employe ORDER BY salary DESC;
```

### Task 7 = How to see only top 3 records from a table?
```sql
SELECT * FROM employe LIMIT 3;
```

### Task 8 = Show records where first name start with letter 'A'
```sql
SELECT * FROM employe WHERE fname LIKE 'A%';
```

### Task 9 = Show records where length of the lname is 4 characters
```sql
SELECT * FROM employe WHERE LENGTH(lname) = 4;
```

### Task 10 = Find Total no. of employees in database?
```sql
SELECT COUNT(emp_id) FROM employe;
```

### Task 11 = Find no. of employees in each department.
```sql
SELECT dept, COUNT(emp_id) FROM employe GROUP BY dept;
```

### Task 12 = Find lowest salary paying
```sql
SELECT MIN(salary) FROM employe;
```

### Task 13 = Find highest salary paying
```sql
SELECT MAX(salary) FROM employe;
```

### Task 14 =  Find total salary paying in Loan department?
```sql
SELECT SUM(salary) FROM employe WHERE dept='Finance';
```

### Task 15 = Average salary paying in each department
```sql
SELECT dept, AVG(salary) FROM employe GROUP BY dept;
```