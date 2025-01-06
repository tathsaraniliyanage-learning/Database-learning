create database if not exists thogakade;
use thogakade;
create table customer(
    cust_id varchar(5) primary key,
    name varchar(25),
    email varchar(25),
    age int(2)
);
create table item(
    item_code varchar(5) primary key,
    item_name varchar(25),
    qty int not null,
    price decimal not null,
    description varchar(50)
);
create table orders(
    o_id varchar(5) primary key,
    date date,
    cust_id varchar(5),
    constraint foreign key (cust_id) references customer(cust_id) on update cascade on delete cascade
    );
create table order_detail(
    order_id varchar(5),
    item_code varchar(5),
    constraint foreign key (order_id) references orders(o_id) on update cascade on delete cascade,
    constraint foreign key (item_code) references item(item_code) on update cascade on delete cascade
);

insert into customer values('c011','amali','amali@gmail.com',13);
insert into customer values('c012','bimali','bimali@gmail.com',23);
insert into customer values('c013','timali','timali@gmail.com',37);
insert into customer values('c014','vimali','vimali@gmail.com',25);
insert into customer values('c010','bimalila','bimalila@gmail.com',39);
insert into customer values('c009','timalila','timalila@gmail.com',40);
insert into customer values('c008','vimalila','vimalila@gmail.com',41);
insert into customer values('c005','timalila','timalila@gmail.com',40);
insert into customer values('c006','vimalila','vimalila@gmail.com',41);
insert into item values('i001','dhal',5,78.00,'new');
insert into item values('i002','suger',2,88.00,'new');
insert into item values('i003','biscuit',100,188.00,'yes');
insert into item values('i004','soap',20,2808.00,'old');
insert into orders values('o001','2024-06-17','c001');
insert into order_detail values('o001','i001');



table ekaka tyena data tika delete kirima
truncate table order_detail;

table ekaka column ekaka tyena row ekak delete kirima
delete from item where description='new';

table ekak sampurnyen delete kirima
drop table order_detail;




exercise

delete customer named vima
delete from customer where name="vima";

delete all records from order_detail
truncate table order_detail;

select all customers with all details
select * from customer;

select only name and age of all customers
select name,age from customer;

select the emails of all customers
select email from customer;

select all the emails which are unique only
select distinct email from customer;

select id and name of each customer but use custName instead of name
select cust_id, name as custName from customer;

select all customers who age is 25
select * from customer where age=25;

display email of customer whose name is amali
select email from customer where name="amali";

display name and email of customers whose age is 27
select name,email from customer where age=27;

display name and email of customer whose age is greather than 30
select name,email from customer where age>30;

display name and email of customer whose age is lesser than 20
select name, email from customer where age<20;

display name and email of customer whose age is greather than or equal to 23
select name, email from customer where age>=23;

display name and email of customer whose age is lesser than or equal to 40
select name, email from customer where age<=23;

display name and email of customer whose age is not equal to 40
select name, email from customer where age!=40;

get name and email of all customers whose age is between 10 and 20
select email from customer where age between 10 and 20;

get name and email of all customers whose age is between 10 and 20
select email from customer where age not between 10 and 20;

get name and email of all customers whose age is 13 or 20
select email from customer where age in(13, 20);

drop database
drop database thogakade;

delete the table customer
drop table customer;

select all customers whose name starts with v
select * from customer where name like 's%';

select all customers whose name starts with a
select * from customer where name like '%a';

select all customers whose age starts with 1
select * from customer where age like '1%';

find customers whose email is null
select * from customer where email is null;

find customers whose email is not null
select * from customer where email is not null;

update the customer name
update customer set name='lamal' where cust_id='c011';

update customer name and age 
update customer set name="bimal",age=31 where cust_id="c001";

update name in age 13 customer
update customer set name="kalu" where age=13;

update age in all records in customer
update customer set age=30;

display all details  of customer
select * from customer;

display all customers by smallest age to largest age
select * from customer order by age;
select * from customer order by age asc;

display all customers by largest age to smallest age
select * from customer order by age desc;

display all customers by smallest to largest name
select * from customer order by name asc;

display all customer whose age is greather than 40 is assending order of
name
select * from customer where age>40 order by name asc;

display name and email of customers whose age is lesser or equal to 40 in order of their name descender order
select name,email from customer where age<=40 order by name desc;

display name and email of customers whose age is lesser or equal to 40 in order of their name descender order without using "order by name"
select name,email from customer where age<=40 order by 2 desc;

get first 3 records of customer
select * from customer limit 3;

eliminate first 3 records and display the next 5 records
select * from customer limit 3,5;

group customer table by their email
select email from customer group by email;
select distinct email from customer;

group customer table by their names
select name from customer group by name;

get a count of customers whose age in the same age
select count(age) from customer group by age;

count , age from all customers
select count(*), age from customer group by age;

count , age from all customers and change count(age) to count
select count(age) as count, age from customer group by age;

display no of orders in same day
select count(date) orders, date from orders group by date;

display how many orders each customer has made
select cust_id,count(*) as order_count from orders group by cust_id;

get age of each customers
select age from customer;

ek name ekkt tyena age count ek sewi,ma
select name,count(age) age_count from customer group by name;

get maximum age and name
select name, max(age) from customer group by name;

get minimum age and name
select name, min(age) from customer group by name;

get total age an email can get
select sum(age), email from customer group by email;

get average age an email can get
select avg(age), email from customer group by email;

display no of customers from each email;
select email,count(*) from customer group by email;

display age where more than 1 customer age
select age, count(*) from customer  group by age having count(*)>1;




sequence

select name
from customer
where cust_id='c001'
group by age
having count(*)>1
order by age;



how to find a total of column
select sum(salary) from customer;

how to find average of column'
select avg(salary) from customer;

how to find min of column'
select min(salary) from customer;

how to find max of column'
select max(salary) from customer;

find count of orders made by each customer
select count(*) from orders group by customer;

find how many customers per address and name
select count(id) as count , cust_id from orders group by cust_id order by count desc;

find count of each item in orders
select count(item_code) from order_detail group by order_id

list the orders by customer, sort number of orders in desc customer
select count(cust_id) count, cust_id from orders group by cust_id order by count desc;

list how many customers are from galle and their salaries
select salary, count(cust_id) from customer where address='galle' group by cust_id;

list top 3 customers by the number of orders
select count(cust_id) count, cust_id from orders group by cust_id order by count desc limit 3;

find the 3 most movable itm in the store.
select count(item_code), item from order_detail group by item_code limit 3;

find the 3 least movable item in the store
select item_code, count(*) as no_of_item from order_detail group by item_code order by no_of_items asc limit 3;

find the order count of each customer in 2008
select cust_id, count(*) as order_count from orders where date like '2008%' group by cust_id;

how many orders each customer has placed
select cust_id,count(cust_id) from orders group by cust_id;





join queries

join customer and order table
select * from customer join orders on customer.cust_id = orders.cust_id;

join orders and order_detail table
select * from orders join order_detail on orders.id= order_detail.order_id;

join customer , order , order_detail tables

select * from customer c
join orders o
on c.cust_id=o.cust_id
join order_detail od
on o.o_id=od.order_id;


union

select name from customer
union
select date from orders;


join customer and order table

select c.cust_id, c.name, c.email,c.age
from customer c
left join orders o
on c.cust_id=o.cust_id;


in inner join, match between values.
in outer join, match between a value and a table.



create a table named orders_archieved with all the records from orders table.(create an table and get from another table data to this table)

create table orders_archieved as select * from orders;


create the new table named order_description with the following values.
(order_id , date, cust_name , description onhand of the item)

create table order_description as
select od.order_id , 0.date, c.name,i.description
from customer c
join orders o
on c.cust_id =0.cust_id;
join order_detail od
on o.id= od.order_id
join item
on od.item_code= i.item_code;




