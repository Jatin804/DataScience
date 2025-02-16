# Some important points

## 1. For error-related safe mode of Workbench, use:
```sql
set sql_safe_updates = 0;
```

## 2. SQL index starts from 1, unlike other languages that start from 0.

## 3. Datetime
- 8 bytes
- Slow accessing
- Not according to timezone

## 4. Timestamp
- 4 bytes
- Fast accessing
- Can be converted into current timezone

## 5. Foreign Key | References
To connect the attributes of the parent table to the child table, we use a foreign key.

Constraint is important if you want to update the foreign key behavior:
```sql
create table posts (
    p_id int,
    likes int,
    u_id int,
    constraint fk foreign key (u_id) references users(user_id)
);
```

## 6. To drop a foreign key
```sql
alter table posts drop constraint fk;
```

## 7. To create another user
```sql
CREATE USER 'username'@'host' IDENTIFIED BY 'password';
```

## 8. User Privileges
To limit access of users (e.g., client and admin):
```sql
GRANT PRIVILEGE ON database.table TO 'username'@'host';
```
For all databases and tables:
```sql
GRANT PRIVILEGE ON *.* TO 'username'@'host';
```

## 9. To revoke all privileges
```sql
REVOKE ALL PRIVILEGES ON *.* FROM 'username'@'localhost';
```

---

# Notes

## To check the current database
```sql
select database();
```

## Equivalent to `desc customers`
```sql
show columns from customers;
```

## To insert values
```sql
insert into customers values(1, 'customer1', 'customer@12gmail.com');
```

## For specific row insertion
```sql
insert into customers(cust_id, cust_name) values(2, 'customer2');
```

## Multiple row insertion
```sql
insert into customers values
(3, 'customer3', 'customer@123gmail.com'),
(4, 'customer4', 'customer@1234@gmail.com'),
(5, 'customer5', 'customer@12345@gmail.com');
```

## To duplicate a table (with values)
```sql
create table cust_copy as select * from customers;
```

## To create a table structure only (without values)
```sql
create table temp like customers;
```

## To add default values
```sql
insert into players values(3, 'player3', default);
```

## Using `auto_increment`
### Basic auto-increment
```sql
create table customers (
    cust_id int unique auto_increment,
    cust_name varchar(40) not null,
    cust_email varchar(90) unique
);
```

### Start auto-increment from a specific value
```sql
create table customers (
    cust_id int unique auto_increment,
    cust_name varchar(40) not null,
    cust_email varchar(90) unique
) auto_increment=100;
```

## Updating a specific value
```sql
update customers
set cust_name = 'Adarsh Gupta'
where cust_id=6;
```

## Deleting values
```sql
delete from customers where cust_id = 101;
```

## Using `IN` keyword
```sql
select * from customers where country in ('USA', 'France', 'Spain');
```

## Using `NOT IN` keyword
```sql
select * from customers where country not in ('USA', 'France', 'Spain');
```

## Using `LIMIT` keyword
```sql
select * from customers limit 10;
```

## For specific row range
### Method 1
```sql
select * from customers limit 10,50;
```
### Method 2
```sql
select * from customers limit 5 offset 3;
```

## Limit
```sql
select * from customers order by creditlimit desc limit 1;
```

## Sorting
```sql
select * from customers order by creditlimit;
select * from customers order by creditlimit desc;
```

## Using `DISTINCT`
```sql
select distinct(country), contactFirstName
from customers
where country = 'USA'
order by creditlimit;
```

## Using `BETWEEN`
```sql
select * from customers
where creditlimit between 80000 and 100000;
```

## Using `LIKE`
```sql
select * from customers where contactLastName like '%sc%'; -- Contains 'sc'
select * from customers where contactLastName like '%sc';  -- Ends with 'sc'
select * from customers where contactLastName like 'sc%';  -- Starts with 'sc'
select * from customers where contactLastName like '_rs%'; -- Second character is 'r', third is 's'
```

## Using `REGEXP`
```sql
select * from customers where customerName regexp '^en';
select * from customers where customerName regexp 'g|eh|ac|uy';
```

## Count operator
```sql
select count(distinct city) from customers;
```

## Grouping and `HAVING` alternate of " where " clause used after group by
```sql
select count(country), country from customers
group by country
having count(country) < 5;
```

## CONCAT or CONCAT\_WS (Concatenation using none, white spaces, defined spaces, or variables)

```sql
SELECT CONCAT('hello', 'world');
SELECT CONCAT_WS(' ', 'hello', 'world');
SELECT CONCAT_WS('_', 'hello', 'world');
-- With reference using ' ' or '_', etc.
SELECT CONCAT_WS('...', first_name, last_name) FROM employees;
```

---

## Uppercase (UCASE)

```sql
SELECT UCASE('Hello');
```

## Lowercase (LCASE)

```sql
SELECT LCASE('HELLOO');
```

---

## "TRIM" - Trimming White Spaces

```sql
SELECT TRIM('          cooldu@123           ');
-- Removes the white spaces from the left and right but not in the middle.
```

---

## "SUBSTR" - String Concatenation

```sql
SELECT SUBSTR('sheryians', 2, 5);
-- Extracts from index 2 to the next 5 characters.
```

---

## INSERT - Insert a Substring into a String

```sql
SELECT INSERT('sheryains', 5, 2, 't_shirt');
SELECT INSERT(last_name, 3, 0, 'kuch_bhi') AS edit FROM employees;
```

---

## REPLACE - Replace a Substring in a String

```sql
SELECT REPLACE('hello world', 'hello', 'hey');
```

---

## REVERSE - Reverse a String

```sql
SELECT REVERSE('hello');
```

---

## STRING COMPARISON

```sql
SELECT STRCMP('hello', 'hey');
```

---

## ABSOLUTE VALUE

```sql
SELECT ABS(-199);
```

---

## CEILING and FLOOR

```sql
SELECT CEIL(18.9);
SELECT FLOOR(18.3);
```

---

## ROUND - Rounding a Number

```sql
SELECT ROUND(9.4);
```

---

## MODULUS - Finding Remainder

```sql
SELECT MOD(30, 4);
```

---

## RANDOM NUMBER

```sql
SELECT RAND();
SELECT 100 * RAND();
```

---

## TRUNCATE - Truncate a Number to a Specific Decimal Place

```sql
SELECT TRUNCATE(100.23456789, 2);
SELECT TRUNCATE(RAND() * 100000, 0);
```

---

## POWER - Calculating Power of a Number

```sql
SELECT POW(2, 3);
```

---

## SQUARE ROOT

```sql
SELECT SQRT(9);
```

---

## INTEGER DIVISION

```sql
SELECT 40 DIV 2;
```

---

## DATETIME Data Type

Format: `YYYY-MM-DD HH:MM:SS`

```sql
CREATE TABLE employees(
    empl_id INT,
    empl_name VARCHAR(50),
    joining_date DATETIME
);
```

---

## TIMESTAMP Data Type

Timestamp varies based on timezone.

```sql
CREATE TABLE employees(
    empl_id INT,
    empl_name VARCHAR(40),
    joining_date TIMESTAMP
);
```

---

## NOW() Function in Time and Date

```sql
CREATE TABLE employees(
    empl_id INT,
    empl_name VARCHAR(40),
    created_at TIMESTAMP DEFAULT NOW(),  -- Adds default time
    updated_at TIMESTAMP ON UPDATE NOW() DEFAULT NOW()  -- Records update date and time
);
```

---

## FOREIGN KEY CONSTRAINTS (CASCADE & SET NULL)

It is not possible to delete parent values if connected to child attributes unless specified:

```sql
ALTER TABLE posts ADD CONSTRAINT fk FOREIGN KEY (u_id) REFERENCES users(user_id) ON DELETE CASCADE;
-- Deletes the child records when parent is deleted.

ALTER TABLE posts ADD CONSTRAINT fk FOREIGN KEY (u_id) REFERENCES users(user_id) ON DELETE CASCADE ON UPDATE CASCADE;
-- Updates the child records when parent is updated.

ALTER TABLE posts ADD CONSTRAINT fk FOREIGN KEY (u_id) REFERENCES users(user_id) ON DELETE SET NULL;
-- Sets child record values to NULL if the parent is deleted.
```

---

## SUBQUERY - Extracting Data from Two Tables

```sql
SELECT * FROM employees WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'purchasing');
```

### Nested Subqueries (Multi-level Queries)

```sql
SELECT * FROM employees
WHERE department_id = (
    SELECT department_id FROM departments
    WHERE location_id = (
        SELECT location_id FROM locations
        WHERE city = 'southlake'
    )
);
```

## Joins
### Inner Join
```sql
select t.tname, s.sname
from teachers t join subject s
on t.t_id = s.teachers_id;
```

### Left Join
```sql
select * from teachers t left join subjects s
on t.t_id = s.teachers_id;
```

### Right Join
```sql
select * from teachers t right join subjects s
on t.t_id = s.teachers_id;
```

### Full Join (Using `UNION`)
```sql
select * from teachers t left join subjects s
on t.t_id = s.teachers_id
union
select * from teachers t right join subjects s
on t.t_id = s.teachers_id;
```

### Cross Join
```sql
select * from teachers, subjects;
```

### Self Join
```sql
select t1.s_id, t1.name, t1.city, t1.subject
from student t1, student t2
where t1.city = t2.city and t1.s_id = t2.s_id;
```

## Subquery
```sql
select * from employees
where department_id = (select department_id from departments where department_name = 'Purchasing');
```

```sql
select * from employees
where department_id = (select department_id from departments where location_id = (select location_id from locations where city = 'Southlake'));
```

