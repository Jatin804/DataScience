
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

<h2>To only create a structure of the table without attribute values of it </h2>
<p>create table temp like customers ; </p>

