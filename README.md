# MySQL Cheat Sheet

> Help with SQL commands to interact with a MySQL database

## What is MySQL?
* **Open Source**: MySQL is open-source and free
* **Scalability**: MySQL is ideal for both small and large applications
* **Performance**: MySQL is very fast, reliable, scalable, and easy to use
* **Cross-Platform**: MySQL is platform-independent, and it can run on various operating systems such as Windows, Linux, macOS, and others.
* **Relational Database Management System (RDBMS)**: MySQL is based on a relational model, organizing data into tables with rows and columns. 

## Who Uses MySQL?
* Huge websites like Facebook, Twitter, Airbnb, Booking.com, Uber, GitHub, YouTube, etc.
* Content Management Systems like WordPress, Drupal, Joomla!, Contao, etc.
* A very large number of web developers around the world

## What is RDBMS?
* RDBMS stands for Relational Database Management System.
* RDBMS is a program used to maintain a relational database.
* RDBMS uses SQL queries to access the data in the database.
* RDBMS is the basis for all modern database systems such as MySQL, Microsoft SQL Server, Oracle, and Microsoft Access.

## What is a Database Table?
* A table is a collection of related data entries, and it consists of columns and rows.
* A column holds specific information about every record in the table.
* A record (or row) is each individual entry that exists in a table.

## What is SQL?
* SQL is the standard language for dealing with Relational Databases.
* SQL is used to insert, search, update, and delete database records.

## Keep in Mind That...
* SQL keywords are NOT case sensitive: select is the same as SELECT
* It is better  all SQL keywords in upper-case.

## Semicolon after SQL Statements?
* Some database systems require a semicolon at the end of each SQL statement.
* Semicolon is the standard way to separate each SQL statement in database systems that allow more than one SQL statement to be executed in the same call to the server.

## Some of The Most Important SQL Commands
* **SELECT** - extracts data from a database
* **UPDATE** - updates data in a database
* **DELETE** - deletes data from a database
* **INSERT INTO** - inserts new data into a database
* **CREATE DATABASE** - creates a new database
* **ALTER DATABASE** - modifies a database
* **CREATE TABLE** - creates a new table
* **ALTER TABLE** - modifies a table
* **DROP TABLE** - deletes a table
* **CREATE INDEX** - creates an index (search key)
* **DROP INDEX** - deletes an index

## SQL Statements

### Data Definition Language (DDL)
* CREATE TABLE
* ALTER TABLE
* DROP TABLE
* TRUNCATE TABLE

### Data Manipulation Language (DML)
* INSERT
* UPDATE
* DELETE
* SELECT



## MySQL Locations
* Mac             */usr/local/mysql/bin*
* Windows         */Program Files/MySQL/MySQL _version_/bin*

## Show Databases

```sql
SHOW DATABASES
```

## Create Database

```sql
CREATE DATABASE acme;
```

## Delete Database

```sql
DROP DATABASE acme;
```

## Select Database

```sql
USE acme;
```
## Create Table

```sql
CREATE TABLE users;
```

```sql
CREATE TABLE IF NOT EXISTS
```

## Create Table

```sql
CREATE TABLE users(
id INT AUTO_INCREMENT,
   first_name VARCHAR(100),
   last_name VARCHAR(100),
   email VARCHAR(50),
   password VARCHAR(20),
   location VARCHAR(100),
   dept VARCHAR(100),
   is_admin TINYINT(1),
   register_date DATETIME,
   PRIMARY KEY(id)
);
```

##  Table includes different data types
```sql
CREATE TABLE example_table (
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    varchar_column VARCHAR(255),
    int_column INT,
    float_column FLOAT,
    double_column DOUBLE,
    boolean_column BOOLEAN,
    date_column DATE,
    datetime_column DATETIME,
    timestamp_column TIMESTAMP,
    char_column CHAR(10),
    text_column TEXT,
    enum_column ENUM('Option1', 'Option2', 'Option3'),
    set_column SET('Value1', 'Value2', 'Value3')
);

```

## Delete / Drop Table

```sql
DROP TABLE tablename;
```
```sql
DROP TABLE IF EXISTS tablename;
```
## Show Tables

```sql
SHOW TABLES;
```


## Select

```sql
SELECT * FROM users;
SELECT first_name, last_name FROM users;
```

## Where Clause

```sql
SELECT * FROM users WHERE location = 'Massachusetts';
SELECT * FROM users WHERE location = 'Massachusetts' AND dept = 'sales';
SELECT * FROM users WHERE is_admin = 1;
SELECT * FROM users WHERE is_admin > 0;

-- Using `!=`
SELECT * FROM users WHERE location != 'Massachusetts';

-- Using `<>`
SELECT * FROM users WHERE location <> 'Massachusetts';

SELECT * FROM users WHERE location LIKE 'Mas%';
SELECT * FROM users WHERE location IN ('Massachusetts', 'New York', 'California');
SELECT * FROM users WHERE is_admin BETWEEN 1 AND 5;

```

### **Note**: The WHERE clause is not only used in SELECT statements, it is also used in UPDATE, DELETE, etc.!


Operators in The WHERE Clause
The following operators can be used in the WHERE clause:

### Operator		
* **=**	        Equal	
* **>**	        Greater than	
* **<**	        Less than	
* **>=**        Greater than or equal	
* **<=**	Less than or equal	
* **<>**	Not equal. Note: In some versions of SQL this operator may be written as !=	
* **BETWEEN**	Between a certain range	
* **LIKE**	Search for a pattern	
* **IN**	To specify multiple possible values for a column

## MySQL AND, OR and NOT Operators

### AND Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

### OR Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

### NOT Syntax
```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```


## ORDER BY (Sort)

### ORDER BY Syntax
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```
### Example
```sql
SELECT * FROM users ORDER BY last_name ASC;
SELECT * FROM users ORDER BY last_name DESC;
```

## Insert Data Only in Specified Columns

### INSERT INTO Syntax (1)
```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

### INSERT INTO Syntax (2)
```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```
## Insert Row / Record

```sql
INSERT INTO users (first_name, last_name, email, password, location, dept, is_admin, register_date) values ('Brad', 'Traversy', 'brad@gmail.com', '123456','Massachusetts', 'development', 1, now());
```

## Insert Multiple Rows

```sql
INSERT INTO users (first_name, last_name, email, password, location, dept,  is_admin, register_date) values ('Fred', 'Smith', 'fred@gmail.com', '123456', 'New York', 'design', 0, now()), ('Sara', 'Watson', 'sara@gmail.com', '123456', 'New York', 'design', 0, now()),('Will', 'Jackson', 'will@yahoo.com', '123456', 'Rhode Island', 'development', 1, now()),('Paula', 'Johnson', 'paula@yahoo.com', '123456', 'Massachusetts', 'sales', 0, now()),('Tom', 'Spears', 'tom@yahoo.com', '123456', 'Massachusetts', 'sales', 0, now());
```
### Example
```sql
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');
```


## NULL Values
### IS NULL Syntax
```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL;
```

### **Tip**: Always use IS NULL to look for NULL values.

### IS NOT NULL Syntax
```sql
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;
```

### Example
```sql
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NOT NULL;
```

## UPDATE Row

### UPDATE Syntax

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

```
### Example

```sql
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City = 'Frankfurt'
WHERE CustomerID = 1;

```

### **Note**: Be careful when updating records in a table! Notice the **WHERE** clause in the **UPDATE** statement. The **WHERE** clause specifies which record(s) that should be updated. If you omit the **WHERE** clause, all records in the table will be updated!

## DELETE Row

### DELETE Syntax

```sql
DELETE FROM table_name WHERE condition;
```
### Example

```sql
DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
```

### **Note**: Be careful when deleting records in a table! Notice the **WHERE** clause in the **DELETE** statement. The **WHERE** clause specifies which record(s) should be deleted. If you omit the **WHERE** clause, all records in the table will be deleted!

## LIMIT Clause

* The LIMIT clause is used to specify the number of records to return.

* The LIMIT clause is useful on large tables with thousands of records. Returning a large number of records can impact performance.

### LIMIT Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
LIMIT number;
```
### Example

```sql
SELECT * FROM Customers
LIMIT 3;
```


## ADD New Column

```sql
ALTER TABLE users ADD col_name col_definition;
```

## MODIFY Column

```sql
ALTER TABLE users MODIFY col_name col_definition;
```
## DROP Column

```sql
ALTER TABLE users DROP col_name;
```

## RENAME Column

```sql
ALTER TABLE users RENAME old_col to new_col;
```

## Concatenate Columns

```sql
SELECT CONCAT(first_name, ' ', last_name) AS 'Name', dept FROM users;

```

## SELECT DISTINCT Rows

```sql
SELECT DISTINCT location FROM users;

```

## BETWEEN (Select Range)

The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.

The BETWEEN operator is inclusive: begin and end values are included.

```sql
SELECT * FROM users WHERE age BETWEEN 20 AND 25;
```

## LIKE (Searching)

The LIKE operator is used in a WHERE clause to search for a specified pattern in a column.

There are two wildcards often used in conjunction with the LIKE operator:

* The percent sign (%) represents zero, one, or multiple characters
* The underscore sign (_) represents one, single character

```sql
SELECT * FROM users WHERE dept LIKE 'd%';
SELECT * FROM users WHERE dept LIKE 'dev%';
SELECT * FROM users WHERE dept LIKE '%t';
SELECT * FROM users WHERE dept LIKE '%e%';
```

## NOT LIKE

```sql
SELECT * FROM users WHERE dept NOT LIKE 'd%';
```

### **Tip**: You can also combine any number of conditions using AND or OR operators.



## IN

```sql
SELECT * FROM users WHERE dept IN ('design', 'sales');
```
## Aliases
Aliases are used to give a table, or a column in a table, a temporary name.

Aliases are often used to make column names more readable.

An alias only exists for the duration of that query.

An alias is created with the AS keyword.

Aliases can be useful when:
* There are more than one table involved in a query
* Functions are used in the query
* Column names are big or not very readable
* Two or more columns are combined together

```sql
SELECT CustomerName AS Customer, ContactName AS "Contact Person"
FROM Customers;
```
## CONCAT_WS

```sql
SELECT CustomerName, CONCAT_WS(', ', Address, PostalCode, City, Country) AS Address
FROM Customers;
```



## Create & Remove Index

```sql
CREATE INDEX LIndex On users(location);
DROP INDEX LIndex ON users;
```

## New Table With Foreign Key (Posts)

```sql
CREATE TABLE posts(
id INT AUTO_INCREMENT,
   user_id INT,
   title VARCHAR(100),
   body TEXT,
   publish_date DATETIME DEFAULT CURRENT_TIMESTAMP,
   PRIMARY KEY(id),
   FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## Add Data to Posts Table

```sql
INSERT INTO posts(user_id, title, body) VALUES (1, 'Post One', 'This is post one'),(3, 'Post Two', 'This is post two'),(1, 'Post Three', 'This is post three'),(2, 'Post Four', 'This is post four'),(5, 'Post Five', 'This is post five'),(4, 'Post Six', 'This is post six'),(2, 'Post Seven', 'This is post seven'),(1, 'Post Eight', 'This is post eight'),(3, 'Post Nine', 'This is post none'),(4, 'Post Ten', 'This is post ten');
```

## INNER JOIN

```sql
SELECT
  users.first_name,
  users.last_name,
  posts.title,
  posts.publish_date
FROM users
INNER JOIN posts
ON users.id = posts.user_id
ORDER BY posts.title;
```

## New Table With 2 Foriegn Keys

```sql
CREATE TABLE comments(
	id INT AUTO_INCREMENT,
    post_id INT,
    user_id INT,
    body TEXT,
    publish_date DATETIME DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY(id),
    FOREIGN KEY(user_id) references users(id),
    FOREIGN KEY(post_id) references posts(id)
);
```

## Add Data to Comments Table

```sql
INSERT INTO comments(post_id, user_id, body) VALUES (1, 3, 'This is comment one'),(2, 1, 'This is comment two'),(5, 3, 'This is comment three'),(2, 4, 'This is comment four'),(1, 2, 'This is comment five'),(3, 1, 'This is comment six'),(3, 2, 'This is comment six'),(5, 4, 'This is comment seven'),(2, 3, 'This is comment seven');
```

## Left Join

```sql
SELECT
comments.body,
posts.title
FROM comments
LEFT JOIN posts ON posts.id = comments.post_id
ORDER BY posts.title;

```

## Join Multiple Tables

```sql
SELECT
comments.body,
posts.title,
users.first_name,
users.last_name
FROM comments
INNER JOIN posts on posts.id = comments.post_id
INNER JOIN users on users.id = comments.user_id
ORDER BY posts.title;

```

## Aggregate Functions

```sql
SELECT COUNT(id) FROM users;
SELECT MAX(age) FROM users;
SELECT MIN(age) FROM users;
SELECT SUM(age) FROM users;
SELECT UCASE(first_name), LCASE(last_name) FROM users;

```

## GROUP BY

```sql
SELECT age, COUNT(age) FROM users GROUP BY age;
SELECT age, COUNT(age) FROM users WHERE age > 20 GROUP BY age;
SELECT age, COUNT(age) FROM users GROUP BY age HAVING count(age) >=2;

```

## MySQL Comments

### Single Line Comments
```sql
-- Select all:
SELECT * FROM Customers;
```

### Multi-line Comments
```sql
/*Select all the columns
of all the records
in the Customers table:*/
SELECT * FROM Customers;
```

## MySQL Database Interview Questions

* [10 MySQL Database Interview Questions for Beginners and Intermediates](http://www.tecmint.com/10-mysql-database-interview-questions-for-beginners-and-intermediates/)
* [100 MySQL interview questions](http://www.careerride.com/MySQL-Interview-Questions.aspx)
* [15 Basic MySQL Interview Questions for Database Administrators](http://www.tecmint.com/basic-mysql-interview-questions-for-database-administrators/)
* [28 MySQL interview questions from JavaTPoint.com](http://www.javatpoint.com/mysql-interview-questions)
* [40 Basic MySQL Interview Questions with Answers](http://www.testingbrain.com/interview/mysql-interview-questions.html)
* [Top 50 MySQL Interview Questions & Answers from Career Guru](http://career.guru99.com/top-50-mysql-interview-questions-answers/)

### Contact
If you want to contact with me you can reach me at [Linkedin](https://www.linkedin.com/in/mahrous-gamal-044693218/).
