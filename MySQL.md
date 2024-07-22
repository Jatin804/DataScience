
<h1>Some important points :- </h1>

<h2> For error related safe mode of workbench, use :- </h2>
<p>set sql_safe_updates = 0;</p>

<h2>sql index starts from 1 not like other languages which starts from 0</h2>



<hr>
<hr>

<h2> To check in what db you are at </h2>

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