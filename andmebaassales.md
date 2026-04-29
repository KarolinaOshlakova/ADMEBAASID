````sql
````--1.categories
create table categories(
category_id int PRIMARY KEY identity (1,1),
category_name varchar(25) UNIQUE);

INSERT INTO categories(category_name)
VALUES ('Arvuti');

SELECT * FROM categories;

````--2.brands
CREATE TABLE brands(
brand_id int PRIMARY KEY identity(1,1),
brand_name varchar(15) UNIQUE);

INSERT INTO brands(brand_name)
VALUES ('Samsung');

SELECT *FROM brands;

````--3.products
CREATE TABLE products(
product_id int PRIMARY KEY identity(1,1),
product_name varchar(50) not null,
brand_id int,
FOREIGN KEY (brand_id) references brands(brand_id),
category_id int,
FOREIGN KEY (category_id) references categories(category_id),
model_year int,
list_price money);

SELECT * FROM products;

INSERT INTO products
VALUES ('nutitelefon´X10', 1, 1, 2025, 600);

````--4.stores
CREATE TABLE stores(
store_id int PRIMARY KEY identity (1,1),
store_name varchar(20) not null,
phone varchar(13),
email varchar(20),
street varchar(21),
city varchar(15),
state varchar(10),
zip_code char(5)
)
SELECT * FROM stores;

INSERT INTO stores
VALUES ('T1', '58444433', 'T1@gmail.com', 'T1 tee', 'Tallinn', 'Eesti', '46376');

````--5.stocks
CREATE TABLE stocks( 
store_id int,
product_id int, 
PRIMARY KEY (store_id, product_id),
FOREIGN KEY (store_id) references stores(store_id),
FOREIGN KEY (product_id) references products(product_id),
quantity int 
)
SELECT * FROM stocks;

INSERT INTO stocks
VALUES (2, 1, 4);


````--6.customers
CREATE TABLE customers(
customer_id int PRIMARY KEY identity(1,1),
first_name varchar(15) not null,
last_name varchar(15) not null,
phone varchar(13),
email varchar(15),
city varchar(15) check (city='Tallinn' or city='Narva'),
state varchar(15),
zip_code char(5)
); 

SELECT * FROM customers

INSERT INTO customers
VALUES('Marina','Uuema','58593940','Mari@gmail.com', 'Tallinn', 'Harjumaa','12913');


````--7.staffs
CREATE TABLE staffs(
staff_id int PRIMARY KEY identity(1,1),
first_name varchar(15) not null,
last_name varchar(15) not null,
phone varchar(13),
active bit,
store_id int,
FOREIGN KEY (store_id) references stores(store_id),
manager bit
)

INSERT INTO staffs
VALUES('Marina', 'Rahva', '5948948', 1, 2, 0);

SELECT * FROM staffs

````--8.orders
CREATE TABLE orders(
order_id int PRIMARY KEY identity(1,1),
customer_id int,
order_status varchar(15) check(order_status='complete' or order_status='incomplete'),
order_date Date,
required_date Date,
shipped_date Date,
store_id int,
FOREIGN KEY(store_id) references stores(store_id),
staff_id int,
FOREIGN KEY(staff_id) references staffs(staff_id));

 SELECT * FROM orders;

INSERT INTO orders 
VALUES (5,'incomplete','2026-05-18','2026-05-20','2026-05-22', 1,1
);

````--9.order_items
CREATE TABLE order_items(
order_id int,
product_id int,
item_id int,
quatity int,
list_price money,
discount int,
FOREiGN KEY (order_id) references orders(order_id),
FOREIGN KEY(product_id) references products(product_id)
)
SELECT * FROM order_items
SELECT * FROM orders
SELECT * FROM products
INSERT INTO order_items
VALUES(1,1,1,10,600.00,100)
