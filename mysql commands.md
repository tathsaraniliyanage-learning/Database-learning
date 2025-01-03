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
    order_id varchar(5) primary key,
    date date,
);
create table order_detail(
    
);