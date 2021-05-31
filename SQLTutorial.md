#SQLTutorial

**What is SQL**

-   SQL stands for **Structured Query Language**.
-   It is designed for managing data in a relational database management system (RDBMS).
-   It is pronounced as S-Q-L or sometime **See-Qwell**.
-   SQL is a database language, it is used for database creation, deletion, fetching rows, and modifying rows, etc.
-   SQL is based on relational algebra and tuple relational calculus.

> All DBMS like MySQL, Oracle, MS Access, Sybase, Informix, PostgreSQL, and SQL Server use SQL as standard database language.

**Installing MySQL on Microsoft Windows**

> [Installing MySQL](https://dev.mysql.com/doc/refman/8.0/en/windows-installation.html)

**SQL Syntax**

SQL follows some unique set of rules and guidelines called syntax. Here, we are providing all the basic SQL syntax.

-   **SQL** is not case sensitive. Generally SQL keywords are written in uppercase.
-   SQL statements are dependent on text lines. We can place a single SQL statement on one or multiple text lines.
-   You can perform most of the action in a database with SQL statements.
-   SQL depends on relational algebra and tuple relational calculus.

Example of SQL statement:

    ```
    SELECT  _column1_, _column2, ..._ FROM  _table_name_;
    ```

Why semicolon is used after SQL statements:

Semicolon is used to separate SQL statements. 
It is a standard way to separate SQL statements in a database system in which more than one SQL statements are used in the same call.

**SQL commands and types**

![SQL Commands](https://d2h0cx97tjks2p.cloudfront.net/blogs/wp-content/uploads/sites/2/2018/08/SQL-Commands-and-Types.jpg)

**SQL Database**
Create Data base
```
mysql> CREATE DATABASE menagerie;
```
```
mysql> USE menagerie
Database changed
```
```
shell> mysql -h host -u user -p menagerie
Enter password: ********
```
```
DROP DATABASE databasename;
```
```
BACKUP DATABASE databasename
TO DISK = 'filepath';
```
```
RENAME DATABASE old_db_name TO new_db_name;  
```
**SQL Commands**

![SQL Commands](https://media.geeksforgeeks.org/wp-content/uploads/sql-commands.jpg)

**SQL Data Types**

Data types are used to represent the nature of the data that can be stored in the database table. For example, in a particular column of a table, if we want to store a string type of data then we will have to declare a string data type of this column.

Data types mainly classified into three categories for every database.

-   String Data types
-   Numeric Data types
-   Date and time Data types


![SQL Data Types](https://cf2.ppt-online.org/files2/slide/n/NOF0UoiGpuELYSmXPkW8wQRgdVM73JKH9qnIy51D6/slide-2.jpg)

SQL Data Types
[https://www.w3schools.com/sql/sql_datatypes.asp](https://www.w3schools.com/sql/sql_datatypes.asp)

**SQL Table**
What is Table ?
Table is a collection of data, organized in terms of rows and columns. In DBMS term, table is known as relation and row as tuple.

```
The tuple, row, and record terms are used interchangeably.
```

**DDL Commands**

SQL statements are started with any of the SQL commands/keywords like SELECT, INSERT, UPDATE, DELETE, ALTER, DROP etc. and the statement ends with a semicolon (;).

SQL CREATE TABLE
```
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
SQL DROP TABLE
```
DROP TABLE table_name;
```

SQL DELETE TABLE
```
DELETE FROM table_name [WHERE condition];  

DELETE FROM table_name;  
```
Difference between DELETE and TRUNCATE statements

```
The DELETE statement only deletes the rows from the table based on the condition defined by WHERE clause 

(or) 

Delete all the rows from the table when condition is not specified.

But it does not free the space containing by the table.

The TRUNCATE statement: it is used to delete all the rows from the table and free the containing space.
```
SQL RENAME TABLE
```
ALTER TABLE table_name  RENAME TO new_table_name; 
(or)
RENAME old_table _name To new_table_name;  
```
SQL TRUNCATE TABLE
```
TRUNCATE TABLE table_name;  
```
SQL COPY TABLE
```
CREATE TABLE TestTable AS
SELECT *
FROM trade;
```
SQL TEMP TABLE

The concept of temporary table is introduced by SQL server.

Temporary tables can be created at run-time and can do all kinds of operations that a normal table can do. These temporary tables are created inside tempdb database.

There are two types of temp tables based on the behavior and scope.

Local Temp Variable
Global Temp Variable

[Temporary tables](https://www.javatpoint.com/sql-temp-table)


```
CREATE TABLE #local temp table (  
User id int,  
Username varchar (50),  
User address varchar (150)  
)  

CREATE TABLE ##new global temp table (  
User id int,  
User name varchar (50),  
User address varchar (150)  
)  
```
SQL ALTER TABLE
```
ALTER TABLE table_name ADD column_name datatype;
ALTER TABLE Customers ADD Email varchar(255);
ALTER TABLE table_name DROP COLUMN column_name;

ALTER TABLE - ALTER/MODIFY COLUMN
Note: Syntax may vary for other database
```
**SQL Constraints**

SQL constraints are used to specify rules for the data in a table.

Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.

**Constraints can be column level or table level**. Column level constraints apply to a column, and table level constraints apply to the whole table.

The following constraints are commonly used in SQL:

```
NOT NULL - Ensures that a column cannot have a NULL value
UNIQUE - Ensures that all values in a column are different
PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
FOREIGN KEY - Prevents actions that would destroy links between tables
CHECK - Ensures that the values in a column satisfies a specific condition
DEFAULT - Sets a default value for a column if no value is specified
CREATE INDEX - Used to create and retrieve data from the database very quickly
```
NOT NULL

`CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);`

`ALTER TABLE Persons MODIFY Age int NOT NULL;`

UNIQUE

`CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    UNIQUE (ID)
);`

PRIMARY KEY

`CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);`

`ALTER TABLE Persons ADD PRIMARY KEY (ID);`

`ALTER TABLE Persons ADD CONSTRAINT PK_Person PRIMARY KEY (ID,LastName);`

`ALTER TABLE Persons DROP PRIMARY KEY;`

`ALTER TABLE Persons DROP CONSTRAINT PK_Person;`

FOREIGN KEY Constraint

`CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);`

`CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    CONSTRAINT FK_PersonOrder FOREIGN KEY (PersonID)
    REFERENCES Persons(PersonID)
);`

`ALTER TABLE Orders ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);`

`ALTER TABLE Orders ADD CONSTRAINT FK_PersonOrder FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);`

`ALTER TABLE Orders DROP FOREIGN KEY FK_PersonOrder;`

CHECK Constraint

`CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CHECK (Age>=18)
);`

`CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255),
    CONSTRAINT CHK_Person CHECK (Age>=18 AND City='Sandnes')
);`

DEFAULT Constraint

`CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Sandnes'
);`

`CREATE TABLE Orders (
    ID int NOT NULL,
    OrderNumber int NOT NULL,
    OrderDate date DEFAULT GETDATE()
);`

`ALTER TABLE Persons ALTER City SET DEFAULT 'Sandnes';`

`ALTER TABLE Persons ALTER City DROP DEFAULT;`

INDEX

`CREATE INDEX index_name ON table_name (column1, column2, ...);`

`CREATE UNIQUE INDEX index_name ON table_name (column1, column2, ...);`

`ALTER TABLE table_name DROP INDEX index_name;`

**SQL Operators**

SQL statements generally contain some reserved words or characters that are used to perform operations such as comparison and arithmetical operations etc. These reserved words or characters are known as operators.

Generally there are three types of operators in SQL:

1.  SQL Arithmetic Operators
2.  SQL Comparison Operators
3.  SQL Logical Operators

[SQL Arithmetic Operators](https://slideplayer.com/slide/3491691/)

**SQL Insert**

`INSERT INTO table_name (column1, column2, column3, ...)VALUES (value1, value2, value3, ...);`

`INSERT INTO table_name VALUES (value1, value2, value3, ...);`

`INSERT INTO table_name [(column1, column2, .... column)] SELECT column1, column2, .... Column N FROM table_name [WHERE condition];  `

**SQL Update**

`UPDATE table_name SET column1 = value1, column2 = value2, ... WHERE condition;`

```
Note: Be careful when updating records in a table! Notice the WHERE clause in the UPDATE statement. The WHERE clause specifies which record(s) that should be updated. If you omit the WHERE clause, all records in the table will be updated!
```

**SQL Delete**

`DELETE FROM table_name WHERE condition;`

```
Note: Be careful when deleting records in a table! Notice the WHERE clause in the DELETE statement. The WHERE clause specifies which record(s) should be deleted. If you omit the WHERE clause, all records in the table will be deleted!
```

**SQL Select**

`SELECT * FROM table_name;`

`SELECT column1, column2, ... FROM table_name;`

```
SELECT
    [ALL | DISTINCT | DISTINCTROW ]
    [HIGH_PRIORITY]
    [STRAIGHT_JOIN]
    [SQL_SMALL_RESULT] [SQL_BIG_RESULT] [SQL_BUFFER_RESULT]
    [SQL_NO_CACHE] [SQL_CALC_FOUND_ROWS]
    select_expr [, select_expr] ...
    [into_option]
    [FROM table_references
      [PARTITION partition_list]]
    [WHERE where_condition]
    [GROUP BY {col_name | expr | position}, ... [WITH ROLLUP]]
    [HAVING where_condition]
    [WINDOW window_name AS (window_spec)
        [, window_name AS (window_spec)] ...]
    [ORDER BY {col_name | expr | position}
      [ASC | DESC], ... [WITH ROLLUP]]
    [LIMIT {[offset,] row_count | row_count OFFSET offset}]
    [into_option]
    [FOR {UPDATE | SHARE}
        [OF tbl_name [, tbl_name] ...]
        [NOWAIT | SKIP LOCKED]
      | LOCK IN SHARE MODE]
    [into_option]

into_option: {
    INTO OUTFILE 'file_name'
        [CHARACTER SET charset_name]
        export_options
  | INTO DUMPFILE 'file_name'
  | INTO var_name [, var_name] ...
}
```


**SELECT UNIQUE**

`SELECT UNIQUE column_name FROM table_name; `

**SELECT DISTINCT**

`SELECT DISTINCT column_name ,column_name FROM  table_name;  `

**SELECT COUNT**

`SELECT COUNT(name) FROM employee_table;`

`SELECT COUNT(*) FROM employee_table; `

`SELECT COUNT(DISTINCT name) FROM employee_table;  `

**SELECT TOP**

`SELECT TOP 2 * FROM employee `

**SELECT FIRST**

`SELECT FIRST(customer_name) AS first_customer FROM customers;  `

**SELECT LAST**

`SELECT column_name FROM table_name ORDER BY column_name DESC LIMIT 1; `

**SELECT RANDOM**

`SELECT column FROM table ORDER BY RAND ( ) LIMIT 1  `

**SELECT AS**

`SELECT day_of_order AS "Date" Customer As "Client",  Product,  Quantity, FROM orders;  `

**SELECT IN**

`SELECT *  FROM students  WHERE students_name IN ( Amit , Raghav, Rajeev)  `

**SELECT Multiple**

`SELECT orders.order_id, suppliers.name  FROM suppliers INNER JOIN orders ON suppliers.supplier_id = orders.supplier_id ORDER BY order_id; `

**SELECT DATE**

`SELECT * FROM  table-name WHERE your date-column >= '2013-12-12'  `

`SELECT* FROM table-name where your date-column < '2013-12-13' and your date-column >= '2013-12-12'  `

`SELECT * FROM  table_name WHERE yourdate BETWEEN '2012-12-12' and '2013-12-12'  `

`SELECT* FROM  table_name WHERE cast (datediff (day, 0, yourdate) as datetime) = '2012-12-12' `

**SELECT SUM**

`SELECT SUM (salary) AS "Total Salary" FROM employees WHERE salary > 20000;  `

`SELECT SUM (DISTINCT salary) AS "Total Salary" FROM employees WHERE salary > 20000;`

`SELECT department, SUM (sales) AS "Total Sales" FROM order_details GROUP BY department; `

**SELECT NULL**

`SELECT SIR_NAME, NAME, MARKS FROM STUDENTS WHERE MARKS IS NULL `

`SELECT SIR_NAME, FIRSTNAME, MARKS FROM STUDENTS WHERE MARKS IS NOT NULL `

**Clause**
**WHERE**

`SELECT column1, column 2, ... column n FROM    table_name WHERE [conditions]  `

**AND**

`SELECT columns FROM tables WHERE condition 1 AND condition 2; `

`INSERT INTO suppliers (supplier_id, supplier_name) SELECT account_no, name FROM customers WHERE customer_name ='IBM'  AND employees =1000; `

`UPDATE suppliers SET supplier_name = 'HP' WHERE supplier_name = 'IBM' AND offices = 8; `

`DELETE FROM suppliers WHERE supplier_name = 'IBM' AND product = 'PC computers'; `

**OR**

`SELECT *   
FROM suppliers  
WHERE city = 'New York'  
OR available_products >= 250; `

`INSERT INTO suppliers(supplier_id, supplier_name)  
SELECT account_no, name  
FROM customers  
WHERE city = 'New Delhi'  
OR city = 'Ghaziabad';`

`UPDATE suppliers   
SET supplier_name = 'HP'  
WHERE supplier_name = 'IBM'  
OR available_product >36; `

`DELETE FROM suppliers  
WHERE supplier_name = 'IBM'  
OR employee <=100;`

**AS**
`SELECT day_of_order AS "Date"    
Customer As "Client",    
Product,    
Quantity,    
FROM orders;  `

**Order By**
**ORDER BY Clause**

`SELECT * FROM CUSTOMERS ORDER BY NAME, SALARY;  `

**ORDER BY ASC**

`SELECT * FROM CUSTOMERS ORDER BY NAME, SALARY;`

**ORDER BY DESC**

`SELECT * FROM CUSTOMERS ORDER BY NAME DESC; `

**ORDER BY RANDOM**

`SELECT column FROM table ORDER BY RAND () LIMIT 1  `

**ORDER BY LIMIT**

`SELECT name, age FROM  (SELECT name, age, ROWNUM r FROM  (SELECT name, age, FROM employee_data ORDER BY age DESC ) WHERE ROWNUM <=40 ) WHERE r >= 21; `

**ORDER BY Multiple Cols**

`SELECT * FROM customers ORDER BY country, Customer-Name;  `

**SQL Joins**


![SQL JOINS](https://i.stack.imgur.com/4zjxm.png)

```
If you want to access more than one table through a select statement.

If you want to combine two or more table then SQL JOIN statement is used .it combines rows of that tables in one table and one can retrieve the information by a SELECT statement.

The joining of two or more tables is based on common field between them.
```

Inner Join

`SELECT * 
FROM tableName1
INNER JOIN tableName2
ON tableName1.matchingColumn = tableName2.matchingColumn ;`

Left (Outer) Join

`SELECT * 
FROM tableName1
LEFT JOIN tableName2
ON tableName1.matchingColumn = tableName2.matchingColumn ;`

Right (Outer) Join

`SELECT * 
FROM tableName1
RIGHT JOIN tableName2
ON tableName1.matchingColumn = tableName2.matchingColumn ;`

Full (Outer) Join

`SELECT * 
FROM tableName1
RIGHT JOIN tableName2
ON tableName1.matchingColumn = tableName2.matchingColumn ;`

Cross Join

`SELECT * FROM MatchScore CROSS JOIN Departments  `

**SQL View**

VIEWS are virtual tables that do not store any data of their own but display data stored in other tables. In other words, VIEWS are nothing but SQL Queries. A view can contain all or a few rows from a table. A MySQL view can show data from one table or many tables.

`CREATE VIEW `view_name` AS SELECT statement;`

`CREATE [OR REPLACE] VIEW [db_name.]view_name [(column_list)]
AS
  select-statement;`

Creating a simple view

`CREATE VIEW salePerOrder AS
    SELECT 
        orderNumber, 
        SUM(quantityOrdered * priceEach) total
    FROM
        orderDetails
    GROUP by orderNumber
    ORDER BY total DESC;`  

Creating a view based on another view

`CREATE VIEW bigSalesOrder AS
    SELECT 
        orderNumber, 
        ROUND(total,2) as total
    FROM
        salePerOrder
    WHERE
        total > 60000;`

`SELECT 
    orderNumber, 
    total
FROM
    bigSalesOrder;`   

Creating a view with join

`CREATE OR REPLACE VIEW customerOrders AS
SELECT 
    orderNumber,
    customerName,
    SUM(quantityOrdered * priceEach) total
FROM
    orderDetails
INNER JOIN orders o USING (orderNumber)
INNER JOIN customers USING (customerNumber)
GROUP BY orderNumber;`

`SELECT * FROM customerOrders 
ORDER BY total DESC;`

Creating a view with a subquery

`CREATE VIEW aboveAvgProducts AS
    SELECT 
        productCode, 
        productName, 
        buyPrice
    FROM
        products
    WHERE
        buyPrice > (
            SELECT 
                AVG(buyPrice)
            FROM
                products)
    ORDER BY buyPrice DESC;`

`SELECT * FROM aboveAvgProducts;`    

Creating a view with explicit view columns

`CREATE VIEW customerOrderStats (
   customerName , 
   orderCount
) 
AS
    SELECT 
        customerName, 
        COUNT(orderNumber)
    FROM
        customers
            INNER JOIN
        orders USING (customerNumber)
    GROUP BY customerName;`

`SELECT 
    customerName,
    orderCount
FROM
    customerOrderStats
ORDER BY 
	orderCount, 
    customerName;`    

MySQL updatable views

```
In MySQL, views are not only query-able but also updatable. It means that you can use the INSERT or UPDATE statement to insert or update rows of the base table through the updatable view. In addition, you can use DELETE statement to remove rows of the underlying table through the view.

However, to create an updatable view, the SELECT statement that defines the view must not contain any of the following elements:

Aggregate functions such as MIN, MAX, SUM, AVG, and COUNT.
DISTINCT
GROUP BY clause.
HAVING clause.
UNION or UNION ALL clause.
Left join or outer join.
Subquery in the SELECT clause or in the WHERE clause that refers to the table appeared in the FROM clause.
Reference to non-updatable view in the FROM clause.
Reference only to literal values.
Multiple references to any column of the base table.
```

`???`

Drop Views

`DROP VIEW [IF EXISTS] view_name;`

`DROP VIEW [IF EXISTS] view_name1 [,view_name2]...;`

Rename View

`RENAME TABLE original_view_name TO new_view_name;`

**SQL Index**

indexes are used to quickly find rows with specific column values. Without an index, MySQL must scan the whole table to locate the relevant rows. The larger table, the slower it searches.

CREATE INDEX

`CREATE TABLE t(
   c1 INT PRIMARY KEY,
   c2 INT NOT NULL,
   c3 INT NOT NULL,
   c4 VARCHAR(10),
   INDEX (c2,c3) 
);`

`CREATE INDEX index_name ON table_name (column_list)`

`CREATE INDEX idx_c4 ON t(c4);`

`EXPLAIN SELECT 
    employeeNumber, 
    lastName, 
    firstName
FROM
    employees
WHERE
    jobTitle = 'Sales Rep';`

`DROP INDEX name ON leads;`    

`DROP INDEX email ON leads
ALGORITHM = INPLACE 
LOCK = DEFAULT;`

`DROP INDEX `PRIMARY` ON table_name;`

`SHOW INDEXES FROM database_name.table_name;`

**Stored Procedures**

`DELIMITER //

CREATE PROCEDURE GetAllProducts()
BEGIN
	SELECT *  FROM products;
END //

DELIMITER ;`

`CALL stored_procedure_name(argument_list);`

`DROP PROCEDURE [IF EXISTS] stored_procedure_name;`

`DROP PROCEDURE GetEmployees;`

**Stored procedure parameters**

`[IN | OUT | INOUT] parameter_name datatype[(length)]`

`DELIMITER //

CREATE PROCEDURE GetOfficeByCountry(
	IN countryName VARCHAR(255)
)
BEGIN
	SELECT * 
 	FROM offices
	WHERE country = countryName;
END //

DELIMITER ;`

`CALL GetOfficeByCountry('USA');`

`DELIMITER $$

CREATE PROCEDURE GetOrderCountByStatus (
	IN  orderStatus VARCHAR(25),
	OUT total INT
)
BEGIN
	SELECT COUNT(orderNumber)
	INTO total
	FROM orders
	WHERE status = orderStatus;
END$$

DELIMITER ;`

`CALL GetOrderCountByStatus('Shipped',@total);
SELECT @total;`

`DELIMITER $$

CREATE PROCEDURE SetCounter(
	INOUT counter INT,
    IN inc INT
)
BEGIN
	SET counter = counter + inc;
END$$

DELIMITER ;`

`SET @counter = 1;
CALL SetCounter(@counter,1); -- 2
CALL SetCounter(@counter,1); -- 3
CALL SetCounter(@counter,5); -- 8
SELECT @counter; -- 8`

**SQL Variables**

`DECLARE variable_name datatype(size) [DEFAULT default_value];`

`DECLARE totalSale DEC(10,2) DEFAULT 0.0;`

`SET variable_name = value;`

`DECLARE total INT DEFAULT 0;
SET total = 10;`

`DECLARE productCount INT DEFAULT 0;

SELECT COUNT(*) 
INTO productCount
FROM products;`

**SQL Triggers**

****
`SELECT columns FROM tables WHERE condition 1 AND condition 2;

INSERT INTO suppliers (supplier_id, supplier_name) SELECT account_no, name FROM customers WHERE customer_name ='IBM' AND employees =1000;`
term
: definition

```
SELECT columns FROM tables WHERE condition 1 AND condition 2;

INSERT INTO suppliers (supplier_id, supplier_name) SELECT account_no, name FROM customers WHERE customer_name ='IBM' AND employees =1000;
```

###### This is an <h6> tag

CREATE TABLE category (
    catid int,
    catname varchar(255));

CREATE TABLE agegroup (
agegroupid int,
agegroupname varchar(255));

CREATE TABLE idealfor (
idealforid int,
idealforname varchar(255));

CREATE TABLE brand (
brandid int,
brandname varchar(255));

CREATE TABLE product (
productid int,
productname varchar(255));

CREATE TABLE customer (
customerid int,
customername varchar(255));

CREATE TABLE orderdetails (
ordid int,
customerid int,
productid INT,
qty INT,
dop DATE
);

### normalisation
### Add categoryid in product/brand
### Add Rate in product
### Do we need Rate column in orderdetails ? Why
### How to mark brand as popular
### How to make your product search as dynamic
### Brand - Seller ?
### Use case for customer / seller
### User review

### Total purchase
### Total purchase month wise
### Total purchase selected month
### Total purchase group by customer
### Total purchase by product
### Total purchase by product - month wise

### Top selling brand ?
### Low selling brand
### Brand wise total purchase
### Which product is not moving/selling ?
### Which product is moving/selling ?

Add primary key for Orderdetails table
Alter Orderdetails table to define the FKs for customerid,productid
Add additional columns in customer table (address,city,pin,state,country)
Add brandid as FK in product table
Create seller table with these columns (sellerid, sellername)
Create seller_product mapping table (sellerid,productid)

Top seller
product sales by Seller wise
Seller wise product total sales
City wise product sales
City wise brand sales

### OrderStatus
### Get Customer Level

### OrderStatus
pass your date of purchase (dop)
ordID   New Ack Acc Cancel  InPro   Transit Delivered
