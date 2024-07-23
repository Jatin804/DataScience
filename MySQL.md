<h1>MySQL Notes</h1>

<h2>Error Related Safe Mode of Workbench</h2>
<p>To disable safe mode in Workbench:</p>
<p>SET sql_safe_updates = 0;</p>

<h2>SQL Index</h2>
<p>Unlike other languages, SQL index starts from 1.</p>

<hr>

<h2>Check Current Database</h2>
<p>To check the current database:</p>
<p>SELECT DATABASE();</p>

<h2>Describe Table</h2>
<p>To display the columns of a table:</p>
<p>DESCRIBE customers;</p>

<h2>Insert Values</h2>
<p>To insert values into the customers table:</p>
<p>INSERT INTO customers VALUES (1, 'customer1', 'customer1@gmail.com');</p>

<h2>Insert Specific Rows</h2>
<p>To insert specific rows into the customers table:</p>
<p>INSERT INTO customers (cust_id, cust_name) VALUES (2, 'customer2');</p>

<h2>Insert Multiple Rows</h2>
<p>To insert multiple rows into the customers table:</p>
<p>INSERT INTO customers VALUES (3, 'customer3', 'customer3@gmail.com'), (4, 'customer4', 'customer4@gmail.com'), (5, 'customer5', 'customer5@gmail.com');</p>

<h2>Duplicate a Table</h2>
<p>To duplicate a table with all its attributes and values:</p>
<p>CREATE TABLE cust_copy AS SELECT * FROM customers;</p>

<h2>Create Table Structure</h2>
<p>To create a table with the same structure as another table:</p>
<p>CREATE TABLE temp LIKE customers;</p>

<h2>Add Default Values</h2>
<p>To add default values to a table:</p>
<p>INSERT INTO players VALUES (3, 'player3', DEFAULT);</p>

<h2>Auto Increment</h2>
<p>To use auto_increment for a column:</p>
<p>
CREATE TABLE customers (
    cust_id INT UNIQUE AUTO_INCREMENT,
    cust_name VARCHAR(40) NOT NULL,
    cust_email VARCHAR(90) UNIQUE
);
</p>

<h2>Auto Increment with Specific Value</h2>
<p>To start auto_increment from a specific value:</p>
<p>
CREATE TABLE customers (
    cust_id INT UNIQUE AUTO_INCREMENT,
    cust_name VARCHAR(40) NOT NULL,
    cust_email VARCHAR(90) UNIQUE
) AUTO_INCREMENT=100;
</p>

<hr>

<h2>Update Specific Value</h2>
<p>To update a specific value in a table:</p>
<p>UPDATE customers SET cust_name = 'Adarsh Gupta' WHERE cust_id = 6;</p>

<hr>

<h2>Delete Values</h2>
<p>To delete values from the customers table:</p>
<p>DELETE FROM customers WHERE cust_id = 101;</p>

<hr>

<h2>IN Keyword</h2>
<p>To select rows with specific values using the IN keyword:</p>
<p>SELECT * FROM customers WHERE country IN ('usa', 'france', 'spain');</p>

<hr>

<h2>NOT Keyword</h2>
<p>To select rows with values not in a specific list using the NOT keyword:</p>
<p>SELECT * FROM customers WHERE country NOT IN ('usa', 'france', 'spain');</p>

<hr>

<h2>Limit Rows</h2>
<p>To limit the number of rows returned:</p>
<p>SELECT * FROM customers LIMIT 10;</p>

<hr>

<h2>Limit Rows with Offset</h2>
<p>To select a specific range of rows using the LIMIT and OFFSET keywords:</p>
<p>SELECT * FROM customers LIMIT 5 OFFSET 3;</p>

<hr>

<h2>Sorting</h2>
<p>To sort rows in ascending or descending order:</p>
<p>SELECT * FROM customers ORDER BY creditlimit;</p>
<p>SELECT * FROM customers ORDER BY creditlimit DESC;</p>

<hr>

<h2>Limit Rows with Sorting</h2>
<p>To limit the number of rows returned and sort them:</p>
<p>SELECT * FROM customers ORDER BY creditlimit DESC LIMIT 1;</p>

<hr>

<h2>Select Distinct Rows</h2>
<p>To select distinct rows from a table:</p>
<p>SELECT DISTINCT country, contactFirstName FROM customers WHERE country = 'usa' ORDER BY creditlimit;</p>

<hr>

<h2>NULL and NOT NULL</h2>
<p>To select rows with NULL or NOT NULL values:</p>
<p>SELECT * FROM customers WHERE addressline2 IS NOT NULL;</p>
<p>SELECT * FROM customers WHERE state IS NULL;</p>

<hr>

<h2>BETWEEN Operator</h2>
<p>To select rows within a specific range:</p>
<p>SELECT * FROM customers WHERE creditlimit BETWEEN 80000 AND 100000;</p>

<hr>

<h2>LIKE Operator</h2>
<p>To select rows based on pattern matching:</p>
<p>SELECT * FROM customers WHERE contactLastName LIKE '%sc%';</p>
<p>SELECT * FROM customers WHERE contactLastName LIKE '%sc';</p>
<p>SELECT * FROM customers WHERE contactLastName LIKE 'sc%';</p>
<p>SELECT * FROM customers WHERE contactLastName LIKE '_rs%';</p>

<p>Note: The "LIKE" operator requires the use of "%" or "_" to define the pattern. An alternative to "LIKE" is the "REGEXP" operator.</p>

<hr>

<h2>REGEXP Operator</h2>
<p>To select rows based on regular expressions:</p>
<p>SELECT * FROM customers WHERE customerName REGEXP '^en';</p>
<p>SELECT * FROM customers WHERE customerName REGEXP '^b';</p>
<p>SELECT * FROM customers WHERE name REGEXP 'g|eh|ac|uy';</p>

<hr>

<h2>Count Operator</h2>
<p>To count the number of distinct values:</p>
<p>SELECT COUNT(DISTINCT city) FROM customers;</p>

<hr>

<h2>GROUP BY</h2>
<p>To group rows based on a column:</p>
<p>SELECT COUNT(country), country FROM customers GROUP BY country;</p>

<hr>

<h2>HAVING</h2>
<p>To filter groups using aggregate functions:</p>
<p>SELECT COUNT(country), country FROM customers GROUP BY country HAVING COUNT(country) < 5;</p>

<hr>

<h2>Character Length</h2>
<p>To find the length of a string:</p>
<p>SELECT CHAR_LENGTH('Hello');</p>

<hr>

<h2>Concatenation</h2>
<p>To concatenate strings:</p>
<p>SELECT CONCAT('hello', 'world');</p>
<p>SELECT CONCAT_WS(' ', 'hello', 'world');</p>
<p>SELECT CONCAT_WS('_', 'hello', 'world');</p>
<p>SELECT CONCAT_WS('...', first_name, last_name) FROM employees;</p>

<hr>

<h2>Uppercase and Lowercase</h2>
<p>To convert strings to uppercase or lowercase:</p>
<p>SELECT UCASE('Hello');</p>
<p>SELECT LCASE('HELLO');</p>

<hr>

<h2>Trim</h2>
<p>To remove leading and trailing spaces from a string:</p>
<p>SELECT TRIM(' cooldu@123 ');</p>

<hr>

<h2>Substring</h2>
<p>To extract a substring from a string:</p>
<p>SELECT SUBSTR('sheryians', 2, 5);</p>

<hr>

<h2>Insert</h2>
<p>To insert a substring into a string:</p>
<p>SELECT INSERT('sheryains', 5, 2, 't_shirt');</p>
<p>SELECT INSERT(last_name, 3, 0, 'kuch_bhi') AS edit FROM employees;</p>

<hr>

<h2>Replace</h2>
<p>To replace a substring in a string:</p>
<p>SELECT REPLACE('hello world', 'hello', 'hey');</p>

<hr>

<h2>Reverse</h2>
<p>To reverse a string:</p>
<p>SELECT REVERSE('hello');</p>

<hr>

<h2>String Comparison</h2>
<p>To compare two strings:</p>
<p>SELECT STRCMP('hello', 'hey');</p>

<hr>

<h2>Absolute Value</h2>
<p>To find the absolute value of a number:</p>
<p>SELECT ABS(-199);</p>

<hr>

<h2>Ceiling and Floor</h2>
<p>To round a number up or down:</p>
<p>SELECT CEIL(18.9);</p>
<p>SELECT FLOOR(18.3);</p>

<hr>

<h2>Round</h2>
<p>To round a number:</p>
<p>SELECT ROUND(9.4);</p>

<hr>

<h2>Modulus</h2>
<p>To find the remainder of a division:</p>
<p>SELECT MOD(30, 4);</p>

<hr>

<h2>Random Number</h2>
<p>To generate a random number:</p>
<p>SELECT RAND();</p>
<p>SELECT 100 * RAND();</p>

<hr>

<h2>Truncate</h2>
<p>To truncate a number to a specific decimal place:</p>
<p>SELECT TRUNCATE(100.23456789, 2);</p>
<p>SELECT TRUNCATE(RAND() * 100000, 0);</p>

<hr>

<h2>Power</h2>
<p>To calculate the power of a number:</p>
<p>SELECT POW(2, 3);</p>

<hr>

<h2>Square Root</h2>
<p>To calculate the square root of a number:</p>
<p>SELECT SQRT(9);</p>

<hr>

<h2>Division</h2>
<p>To perform integer division:</p>
<p>SELECT 40 DIV 2;</p>

<hr>

