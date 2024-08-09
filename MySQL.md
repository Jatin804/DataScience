
<h1>Some important points :- </h1>

<h2>1. For error related safe mode of workbench, use :- </h2>
<p>set sql_safe_updates = 0;</p>

<h2>2. Sql index starts from 1 not like other languages which starts from 0</h2>

<h2>3. Datatime 8byte, slow accessing, not according to timezone</h2>

<h2>4. Timestamp 4byte, fast accessing, can be converted into current timezone</h2>

<h2>5. Foreign key | references</h2>
<p>To connect the attributes of the parent table to chile table the we use foreign key</p>
<p>constraint is important in condition if u want to update the foreign key behaviour</p>
<p>create table posts( <br>
    p_id int, <br>
    likes int, <br>
    u_id int, constraint fk foreign key (u_id) references users(user_id));	<br>
</p>

<h2>6. To drop foreign key </h2>
<p>alter table posts drop constraint fk;</p>

<h2>7. To create another user</h2>
<p>CREATE USER 'username'@'host' IDENTIFIED BY 'password';</p>

<h2>8. User PRIVILEGES, to limit the access of accessing users like clint and admin </h2>
<p>GRANT PRIVILEGE ON database.table TO 'username'@'host';</p>
<p>*.* <- for all</p>

<h2>9. To Revoke, take take all privilegrs</h2>
<p>REVOKE ALL PRIVILEGES ON *.* FROM '<user_name>'@'localhost';</p>

<h2>10.</h2>






<hr>
<hr>


<h1>Notes :- </h1>

<h2>To check in what db you are at </h2>

<p>select database() ;</p>

<h2> Same as desc customers funtion </h2>
<p>show columns from customers ;</p>

<h2> To insert values </h2>
<p>insert into customers values(1, 'customer1', 'customer@12gmail.com') ;</p>

<h2> For specific row insertion inside table </h2>
<p> insert into customers(cust_id, cust_name) values(2, 'customer2');</p>

<h2> Multiple row insertion </h2>
<p>
    insert into customers values <br>
    (3, 'customer3','customer@123gmail.com'), <br>
    (4, 'customer4', 'customer@1234@gmail.com'), <br>
    (5, 'customer5', 'customer@12345@gmail.com') ; <br>
</p>

<h2>To duplicate a table (best way) and with its all attributes values inside of it </h2>
<p> create table cust_copt as select * from customers ;</p>

<h2>To only create a structure like of the table without attribute values of it </h2>
<p>create table temp like customers ; </p>

<h2>To add default values, through default keyword</h2>
<p>insert into players values(3, 'players3', default);</p>

<h2>Using auto_increment keyword ( to use auto_increment that attribute should be a key )</h2>
<h3>Add accoording to the last value</h3>
<p>
    create table customers( <br>
    cust_id int unique auto_increment, <br>
    cust_name varchar(40) not null, <br>
    cust_email varchar(90) unique <br>
    );
</p>

<h2>For specific auto_increment form a specific value</h2>
<p>
    create table customers( <br>
    cust_id int unique auto_increment, <br>
    cust_name varchar(40) not null, <br>
    cust_email varchar(90) unique <br>
    ) <b> auto_increment=100 ; </b>
</p>

<hr>

<h2>To update a specific value inside a table</h2>
<p>
    update customers <br>
    set cust_name = 'Adarsh gupta'  <br>
    where cust_id=6; <br>
</p>

<hr>

<h2>To delete values inside the customers</h2>
<p>delete from customers where cust_id = 101;</p>

<hr>

<h2>in keyword</h2>
<p>select * from customers where country <b>in</b> ('usa', 'france', 'spain'); </p>

<hr>

<h2>not keyword</h2>
<p>select * from customers where country <b>not</b> in ('usa', 'france', 'spain');</p>

<hr>

<h2>To display limit keyword</h2>
<p>select * from customers limit 10;</p>

<hr>

<h2>For specific range in rows</h2>
<p>Method 1 :- </p>
<p>select * from customers limit 10,50;</p>
<br>
<p>Method 2 :- </p>
<p>select * from customers limit 5 offset 3;</p>

<hr>

<h2>Sorting asc and desc</h2>
<p>
    select * from customers order by creditlimit; <br> 
    select * from customers order by creditlimit desc;
</p>

<hr>

<h2>To display the limited rows, limit keyword</h2>
<p>select * from customers order by creditlimit desc <b>limit</b> 1;</p>

<hr>

<h2>To select distinct rows of table, distinct keyword</h2>
<p>select <b>distinct</b>(country), contactFirstName from customers <br>								-- using distinct function 
    where country = 'usa' <br>
    order by creditlimit; <br>
</p>

<hr>

<h2>Using null or not null keyword </h2>
<p>select * from customers <br>
    where addressline2 is <b>not null;</b>	<br>
</p>
<br>
<p>
    select * from customers <br>
    where state is <b>null;</b> <br>
</p>

<hr>

<h2>Using between keyword</h2>
<p>
    select * from customers <br>
    where creditlimit <b>between</b> 80000 and 100000; <br>
</p>

<hr>

<h2>Using like operator</h2>
<p>
    select * from customers where contactLastName <b>like</b> '%sc%';								 in between letters  <br>
    select * from customers where contactLastName <b>like</b> '%sc';								 in last  <br>
    select * from customers where contactLastName <b>like</b> 'sc%';								 in starting <br>
    select * from customers where contactLastName <b>like</b> '_rs%';                               ( _ )  -> represents for one any char <br>
</p>

<p>Cons of like operator : must define it under % or _ </p>
<br>
<p>Replacement : " regexp " (alternate of like operator)</p>

<hr>

<h2> regexp uses caret ( ^ ) -> opposite of % operators (in position of random others chars or ints)</h2>
<p>
    select * from customers where customerName <b>regexp</b> '^en'; 								-- no need of the % %   <br>
    select * from customers where customerName <b>regexp</b> '^b';									-- ?   it checks through  like abc = a + ab + abc			(['xyz']) -> in stating its swld the a or y or z <br>
    select * from coustomerName where name <b>regexp</b> 'g|eh|ac|uy';								-- g or eh or ac or uy <br>
</p>

<hr>

<h2>Use of count operator </h2>
<p>
    select <b>count</b>(distinct city) from customers; <br>
</p>

<hr>

<h2>Using " group by "</h2>
<p>
    select count(country), country from customers <b>group by</b> country;	                        -- result based of groups eg. count based on country
</p>

<hr>

<h2>" having " alternate of " where " clause used after group by </h2>
<p>
    select count(country), country from customers <br> 
    group by country <b>having</b> count(country) < 5;
</p>

<hr>

<h2>To find char lenght of a char in or not of DB </h2>
<p>
    select <b>char_length</b>('Hello'); <br>
    <h4>OR -- </h4>
    select <b>character_length</b>('Hello'); <br>
</p>

<hr>

<h2>concat or concat_ws  (concat using none or using white spaces or with a defined spaces or variable)</h2>
<p>select concat('hello', 'world');</p>

<p>select concat_ws(' ', 'hello', 'world');	 <br>
    select concat_ws('_', 'hello', 'world');		 <br>								   		-- with refrence with ' ' or '_' etc 
    select concat_ws('...', first_name, last_name) from employees; <br>
</p>

<hr>

<h2>Uppercase (ucase)</h2>
<p>select ucase('Hello');</p>

<h2>Lowercase (lcase)</h2>
<p>select lcase('HELLOO');</p>

<hr>

<h2>" Trim ", trimming the white spaces</h2>
<p>select trim('          cooldu@123           ');				    							-- removes the white spaces of right and left not mids one </p>

<hr>

<h2>"substr" , use -> a string concadination </h2>
<p>select substr('sheryians', 2,5);</p>                                                         -- from 2 to next 5, <b> it cuts like start, to next point </b>

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

<h2>Data type Datetime : </h2>
<p>To store datatime | Format : YYYY-MM-DD HH:MM:SS </p>
<br>
<p>create table employees( <br>
    empl_if int,  <br>
    empl_name varchar(50), <br>
    joining_data datetime <br>
    ); <br>
</p>

<hr>

<h2>Timestamp datatype </h2>
<p>To store date but according to timezone it varies </p>
<br>
<p>create table employees( <br>
    empl_if int, <br> 
    empl_name varchar(40), <br>
    joining_date timestamp <br>
    ); <br>
</p>

<hr>

<h2>now() function in time and date </h2>
<p>create table employees( <br>
    empl_if int, <br>
    empl_name varchar(40), <br>
    created_at timestamp default now(),                						            -- will add default time <br>
    updated_at timestamp on update now() default now()                       			-- will record update date and time  <br>
    ); <br>
</p>

<hr>

<h2>Its not possible to delete parent values if its connected to child attributes | To do so : </h2>
<h4>{ on delete | on update : cascade | set null }</h4>

<p>
    alter table posts add constraint fk foreign key(u_id) references users(user_id) on delete cascade;							-- on delete cascade 

    alter table posts add constraint fk foreign key(u_id) references users(user_id) on delete cascade on update cascade;		-- on update cascade 

    alter table posts add constraint fk foreign key(u_id) references users(user_id) on delete set null; 						-- on delete set null (remains the data of child)
</p>

<hr>

<h2>Sub query | extracting data from two tables</h2>
<p>select * from employees where department_id = (select department_id from departments where department_name = 'purchasing');</p>

<p>or sub(sub(sub)) query</p>

<p>select * from employees where department_id = (select department_id from departments where location_id = (select location_id from locations where city = 'southlake'));
</p>

<hr>

<h2>Joins </h2>

<h4>Inner join</h4>
<p>select t.tname, s.sname <br>
from teachers t join subject s <br>
on t.t_id = s.techers_id ;<br>
</p>

<h4>Left join </h4>
<p>
    select * from teachers t left join subjects s<br>
    on teachers.t_id = subjects.techers_id;
</p>

<h4>Right join</h4>
<p>
    select * from teachers t left join subjects s<br>
    on teachers.t_id = subjects.techers_id;
</p>

<h4>Union or full join </h4>
<p>    
    select * from teachers t left join subjects s<br>
    on teachers.t_id = subjects.techers_id;  <br>
    <b>Union</b>
    select * from teachers t left join subjects s<br>
    on teachers.t_id = subjects.techers_id; <br>
</p>

<h4>Cross join </h4>
<p>select * from techaers, subjects;</p>

<h4>Self join | creating a copy of a table to compare with the same table </h4>
<p>s
    elect t1.s_id, t1.name, t1.city, t1.subject from student t1, student t2 
    where t1.city = t2.city && t1.s_id = t2.s_id;
</p>

<hr>

<h2>Using keyword for camparing </h2>
<p>Condition for using " using keyword " when both tables having same (fk) and (primary key)'s name.</p>
<p>select * from employees e join departments d using (department_id);</p>

<hr>

Data functions, Views, Users, Delimiters, Functional dependencies <- pending to write
