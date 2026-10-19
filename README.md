# dbmss

Tab 1

1) Write and execute SQL queries to create a department table with Dept_Id as the Primary Key, Dept_Name, and Dept_Loc (all NOT NULL). Insert 3 department records (Civil in Mumbai, Comp in Kolkata, Mech in Pune) and display the table.

SQL

CREATE TABLE department (

        Dept_Id INT NOT NULL,

        Dept_Name VARCHAR(45) NOT NULL,

        Dept_Loc VARCHAR(45) NOT NULL,

        PRIMARY KEY (Dept_Id)

);

 

INSERT INTO department VALUES (4, 'Civil', 'Mumbai');

INSERT INTO department VALUES (5, 'Comp', 'Kolkata');

INSERT INTO department VALUES (6, 'Mech', 'Pune');

 

SELECT * FROM department;

 

 

 

2) Create an employee table (Emp_ID, Emp_Name, Emp_Age, Emp_Dept). Insert 4 employee records. Then: (1) Update the department of Emp_ID = 5 to 'marketing', (2) Delete the record where Emp_ID = 4, and (3) Display the updated table.

 

SQL

CREATE TABLE employee (

        Emp_ID INT PRIMARY KEY,

        Emp_Name VARCHAR(45) NOT NULL,

        Emp_Age INT NOT NULL,

        Emp_Dept VARCHAR(45) NOT NULL

);

 

INSERT INTO employee VALUES (1, 'Tom', 25, 'operation');

INSERT INTO employee VALUES (3, 'jerry', 12, 'phy');

INSERT INTO employee VALUES (4, 'anna', 34, 'developer');

INSERT INTO employee VALUES (5, 'kavya', 54, 'testing');

 

-- 1. Update specific row

UPDATE employee SET Emp_Dept = 'marketing' WHERE Emp_ID = 5;

 

-- 2. Delete specific row

DELETE FROM employee WHERE Emp_ID = 4;

 

-- 3. Verify final table

SELECT * FROM employee;

 


 

3) Create an employee table including a salary column and insert 4 records. Write queries to: (1) Display all employee names and departments in uppercase using string functions, and (2) Find the average, maximum, and total salary of all employees using aggregate functions.

 

SQL

CREATE TABLE employee (

        Emp_ID INT PRIMARY KEY,

        Emp_Name VARCHAR(45),

        Emp_Dept VARCHAR(45),

        salary INT

);

 

INSERT INTO employee VALUES (1, 'Tom', 'operation', 1250);

INSERT INTO employee VALUES (2, 'Emma', 'finance', 1234);

INSERT INTO employee VALUES (3, 'jerry', 'phy', 4321);

INSERT INTO employee VALUES (5, 'kavya', 'marketing', 1232);

 

-- 1. String Manipulation

SELECT Emp_ID, UPPER(Emp_Name) AS Name_Upper, UPPER(Emp_Dept) AS Dept_Upper FROM employee;

 

-- 2. Aggregate Functions

SELECT AVG(salary) AS Avg_Salary, MAX(salary) AS Max_Salary, SUM(salary) AS Total_Salary FROM employee;

 

 

4) Create an employee table with a salary column and insert 4 records. Write two nested subqueries: (1) Find the employee with the highest salary, and (2) Find the names and salaries of all employees earning more than the company's average salary.

 

SQL

CREATE TABLE employee (

        Emp_ID INT PRIMARY KEY,

        Emp_Name VARCHAR(45),

        Emp_Dept VARCHAR(45),

        salary INT

);

 

INSERT INTO employee VALUES (1, 'Tom', 'operation', 1250);

INSERT INTO employee VALUES (2, 'Emma', 'finance', 1234);

INSERT INTO employee VALUES (3, 'jerry', 'phy', 4321);

INSERT INTO employee VALUES (5, 'kavya', 'marketing', 1232);

 

-- 1. Employee with highest salary

SELECT * FROM employee WHERE salary = (SELECT MAX(salary) FROM employee);

 

-- 2. Employees earning above average salary

SELECT Emp_Name, salary FROM employee WHERE salary > (SELECT AVG(salary) FROM employee);


 

5) Create a Customers table (customer_id, first_name, last_name, age, country) and insert 3 customer records (at least two from 'USA' and one from 'UK' or 'India'). Create a View named US_Customers that displays only customers from 'USA', and run a SELECT query on the view to verify the output.

 

SQL

CREATE TABLE Customers (

        customer_id INT PRIMARY KEY,

        first_name VARCHAR(45),

        last_name VARCHAR(45),

        age INT,

        country VARCHAR(45)

);

 

INSERT INTO Customers VALUES (1, 'John', 'Doe', 31, 'USA');

INSERT INTO Customers VALUES (2, 'Robert', 'Luna', 22, 'USA');

INSERT INTO Customers VALUES (3, 'Kavya', 'Sharma', 24, 'India');

 

-- Create the View

CREATE VIEW US_Customers AS

SELECT customer_id, first_name, last_name, age

FROM Customers

WHERE country = 'USA';

 

-- Query the View

SELECT * FROM US_Customers;

