Here is a clean, well-arranged **README** for your SQL project.
I removed symbols and formatted everything professionally.
You can copy–paste this directly into your GitHub README.

---

# SQL Project – Online Book Store Database

This project contains a complete relational database designed for an online book store. The database includes tables for books, customers, orders, and order details. Various SQL queries are used to analyze customer behavior, sales performance, best selling books, revenue, and inventory insights.

## Features of the Project

• Designed and managed a normalized relational database
• Implemented tables for books, customers, orders, and order details
• Performed joins, aggregate functions, subqueries, and analytical queries
• Generated insights such as revenue, customer spending, best selling books, and category wise performance

## Database Schema Includes

• Books table
• Customers table
• Orders table
• Order Details table

## SQL Queries Used

Below are the queries used in the project, arranged neatly and grouped by category.

---

## Database and Table Creation

create database Book_store_db
use Book_store_db

create table Books
(book_id int primary key, title varchar(100), author varchar(50), category varchar(30), price decimal(8,2), stock int)

create table Customers
(customer_id int primary key, customer_name varchar(50), city varchar(30), email varchar(50))

create table Orders
(order_id int primary key, customer_id int, order_date date, total_amount decimal(10,2), foreign key(customer_id) references Customers(customer_id))

create table Order_Details
(order_id int, book_id int, quantity int, foreign key(order_id) references Orders(order_id), foreign key(book_id) references Books(book_id))

---

## Data Insertion

Books inserted
Customers inserted
Orders inserted
Order details inserted

---

## Basic Queries

select * from Books
select * from Customers
select * from Orders
select * from Order_Details

select customer_name from Customers where city = 'Hyderabad'
select title, price from Books where price > 500
select city, count(*) as total_customers from Customers group by city
select sum(total_amount) as total_revenue from Orders

---

## Analytical Queries

Top 3 costliest books
select * from Books order by price desc limit 3

Total books sold
select sum(quantity) as total_books_sold from Order_Details

Best selling book
select b.title, sum(od.quantity) as sold_count
from Order_Details od
join Books b on od.book_id = b.book_id
group by b.title
order by sold_count desc
limit 1

Customer total spending
select c.customer_name, sum(o.total_amount) as total_spent
from Customers c
join Orders o on c.customer_id = o.customer_id
group by c.customer_name

Books purchased by each customer
select c.customer_name, sum(od.quantity) as total_books
from Customers c
join Orders o on c.customer_id = o.customer_id
join Order_Details od on o.order_id = od.order_id
group by c.customer_name

Average price per category
select category, avg(price) as avg_price from Books group by category

Books never ordered
select title from Books where book_id not in
(select distinct book_id from Order_Details)

Books with quantity greater than one sold
select b.title, sum(od.quantity) as sold_qty
from Books b
join Order_Details od on b.book_id = od.book_id
group by b.title
having sold_qty > 1

Monthly order count
select month(order_date) as month, count(*) as total_orders
from Orders group by month(order_date)

Top 2 customers by spending
select c.customer_name, sum(o.total_amount) as total_spent
from Customers c
join Orders o on c.customer_id = o.customer_id
group by c.customer_name
order by total_spent desc
limit 2

Top selling category
select b.category, sum(od.quantity) as total_sold
from Books b
join Order_Details od on b.book_id = od.book_id
group by b.category
order by total_sold desc
limit 1

Revenue earned by each city
select c.city, sum(o.total_amount) as city_revenue
from Customers c
join Orders o on c.customer_id = o.customer_id
group by c.city
order by city_revenue desc

Books with stock less than average stock
select title, stock from Books
where stock < (select avg(stock) from Books)

Customers who never placed an order
select customer_name from Customers
where customer_id not in (select distinct customer_id from Orders)

Author wise books sold
select b.author, sum(od.quantity) as books_sold
from Books b
join Order_Details od on b.book_id = od.book_id
group by b.author
order by books_sold desc

---

If you want, I can also:

• Add a project description in Telugu-English mix
• Add screenshots section
• Add installation steps
• Add ER diagram for your project

Just tell me!
