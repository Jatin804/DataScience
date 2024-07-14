
<h2>Some important points :- </h2>

<h2> For error related safe mode of workbench, use :- </h2>
<p>set sql_safe_updates = 0;</p>




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

<h2>To <b>duplicate</b> a table (best way) and with its all attributes values inside of it </h2>
<p> create table cust_copt as select * from customers ;</p>

<h2>To only create a <b> structure like </b> of the table without attribute values of it </h2>
<p>create table temp like customers ; </p>

<h2>To <b>add default values</b>, through default keyword</h2>
<p>insert into players values(3, 'players3', default);</p>

<h2>Using <b>auto_increment keyword</b> ( to use auto_increment that attribute should be a key )</h2>
<h3>Add accoording to the last value</h3>
<p>
    create table customers(
    cust_id int unique auto_increment,
    cust_name varchar(40) not null,
    cust_email varchar(90) unique
    );
</p>

<h2>For <b>specific auto_increment</b> form a specific value</h2>
<p>
    create table customers(
    cust_id int unique auto_increment,
    cust_name varchar(40) not null,
    cust_email varchar(90) unique
    ) <b> auto_increment=100 ; </b>
</p>

<hr>

<h2>To <b>update</b> a specific value inside a table</h2>
<p>
    update customers
    set cust_name = 'Adarsh gupta' 
    where cust_id=6;
</p>

<h2>To <b>delete</b> values inside the customers</h2>
<p>delete from customers where cust_id = 101;</p>