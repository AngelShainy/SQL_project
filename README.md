# SQL_project
Developed and managed a relational database to analyze customer bookings, orders, and payments. Employed joins and aggregate functions to create analytical data-driven business decisions.
QUERIES
create database Book_store_db;
use Book_store_db;
CREATE TABLE Books (
  book_id INT PRIMARY KEY,
  title VARCHAR(100),
  author VARCHAR(50),
  category VARCHAR(30),
  price DECIMAL(8,2),
  stock INT
);
INSERT INTO Books VALUES
(1, 'Atomic Habits', 'James Clear', 'Self-Help', 450.00, 15),
(2, 'The Alchemist', 'Paulo Coelho', 'Fiction', 350.00, 20),
(3, 'Ikigai', 'Hector Garcia', 'Self-Help', 400.00, 10),
(4, 'Think Like a Monk', 'Jay Shetty', 'Motivational', 500.00, 12),
(5, 'The Psychology of Money', 'Morgan Housel', 'Finance', 550.00, 8),
(6, 'Rich Dad Poor Dad', 'Robert Kiyosaki', 'Finance', 480.00, 14),
(7, 'Wings of Fire', 'A.P.J Abdul Kalam', 'Biography', 300.00, 9),
(8, '1984', 'George Orwell', 'Fiction', 420.00, 11),
(9, 'Sapiens', 'Yuval Noah Harari', 'History', 600.00, 5),
(10, 'Deep Work', 'Cal Newport', 'Productivity', 530.00, 7);
select * from Books;
CREATE TABLE Customers (
  customer_id INT PRIMARY KEY,
  customer_name VARCHAR(50),
  city VARCHAR(30),
  email VARCHAR(50)
);
INSERT INTO Customers VALUES
(101, 'Aditi Rao', 'Hyderabad', 'aditi@gmail.com'),
(102, 'Rohit Mehta', 'Mumbai', 'rohit@gmail.com'),
(103, 'Sneha Kapoor', 'Delhi', 'sneha@gmail.com'),
(104, 'Kiran Das', 'Chennai', 'kiran@gmail.com'),
(105, 'Neha Sharma', 'Bangalore', 'neha@gmail.com'),
(106, 'Rahul Verma', 'Hyderabad', 'rahul@gmail.com'),
(107, 'Ankit Verma', 'Mumbai', 'ankit@gmail.com'),
(108, 'Meena Iyer', 'Chennai', 'meena@gmail.com'),
(109, 'Vikram Reddy', 'Bangalore', 'vikram@gmail.com'),
(110, 'Isha Singh', 'Delhi', 'isha@gmail.com');
SELECT * FROM Customers;
CREATE TABLE Orders (
  order_id INT PRIMARY KEY,
  customer_id INT,
  order_date DATE,
  total_amount DECIMAL(10,2),
  FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);
INSERT INTO Orders VALUES
(201, 101, '2024-06-01', 850.00),
(202, 103, '2024-06-10', 950.00),
(203, 104, '2024-07-01', 480.00),
(204, 105, '2024-07-20', 1100.00),
(205, 107, '2024-08-02', 950.00);
SELECT * FROM Orders;
CREATE TABLE Order_Details (
  order_id INT,
  book_id INT,
  quantity INT,
  FOREIGN KEY (order_id) REFERENCES Orders(order_id),
  FOREIGN KEY (book_id) REFERENCES Books(book_id)
);
INSERT INTO Order_Details VALUES
(201, 1, 1),
(201, 2, 1),
(202, 5, 1),
(202, 3, 1),
(203, 6, 1),
(204, 4, 2),
(204, 10, 1),
(205, 8, 1),
(205, 2, 1),
(205, 9, 1);
SELECT * FROM Order_Details;
SELECT customer_name FROM Customers WHERE city='Hyderabad';
SELECT title, price FROM Books WHERE price > 500;
SELECT city, COUNT(*) AS total_customers FROM Customers GROUP BY city;
SELECT SUM(total_amount) AS total_revenue FROM Orders;
INSERT INTO Books VALUES
(11, 'The Subtle Art of Not Giving a F*ck', 'Mark Manson', 'Self-Help', 490.00, 10),
(12, 'Zero to One', 'Peter Thiel', 'Business', 600.00, 8),
(13, 'Start with Why', 'Simon Sinek', 'Motivational', 520.00, 9),
(14, 'The 5 AM Club', 'Robin Sharma', 'Self-Help', 450.00, 12),
(15, 'Educated', 'Tara Westover', 'Biography', 400.00, 7),
(16, 'Becoming', 'Michelle Obama', 'Biography', 580.00, 10),
(17, 'The Lean Startup', 'Eric Ries', 'Business', 630.00, 6),
(18, 'Man’s Search for Meaning', 'Viktor Frankl', 'Philosophy', 500.00, 9),
(19, 'Can’t Hurt Me', 'David Goggins', 'Motivational', 550.00, 8),
(20, 'The Intelligent Investor', 'Benjamin Graham', 'Finance', 700.00, 5);
select * from Books;
INSERT INTO Customers VALUES
(111, 'Harini Nair', 'Kochi', 'harini@gmail.com'),
(112, 'Manoj Kumar', 'Pune', 'manoj@gmail.com'),
(113, 'Priya Menon', 'Chandigarh', 'priya@gmail.com'),
(114, 'Suresh Babu', 'Coimbatore', 'suresh@gmail.com'),
(115, 'Ananya Joshi', 'Ahmedabad', 'ananya@gmail.com'),
(116, 'Ritesh Agarwal', 'Lucknow', 'ritesh@gmail.com'),
(117, 'Kavya Iyer', 'Chennai', 'kavya@gmail.com'),
(118, 'Sonia Patel', 'Bangalore', 'sonia@gmail.com'),
(119, 'Deepak Reddy', 'Hyderabad', 'deepak@gmail.com'),
(120, 'Nikhil Sharma', 'Mumbai', 'nikhil@gmail.com');
INSERT INTO Orders VALUES
(206, 111, '2024-08-10', 900.00),
(207, 112, '2024-08-12', 1050.00),
(208, 113, '2024-08-15', 650.00),
(209, 114, '2024-08-20', 800.00),
(210, 115, '2024-08-22', 1200.00),
(211, 116, '2024-09-01', 700.00),
(212, 117, '2024-09-05', 950.00),
(213, 118, '2024-09-10', 850.00),
(214, 119, '2024-09-15', 1300.00),
(215, 120, '2024-09-18', 1100.00);
INSERT INTO Order_Details VALUES
(206, 11, 1),
(206, 13, 1),
(207, 20, 1),
(207, 12, 1),
(208, 14, 1),
(209, 16, 1),
(210, 17, 1),
(211, 18, 1),
(212, 19, 1),
(214, 15, 1);
SELECT * FROM Books ORDER BY price DESC LIMIT 3;
SELECT SUM(quantity) AS total_books_sold FROM Order_Details;
SELECT b.title, SUM(od.quantity) AS sold_count
FROM Order_Details od
JOIN Books b ON od.book_id = b.book_id
GROUP BY b.title
ORDER BY sold_count DESC
LIMIT 1;
SELECT c.customer_name, SUM(o.total_amount) AS total_spent
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_name;
SELECT c.customer_name, SUM(od.quantity) AS total_books
FROM Customers c
JOIN Orders o ON c.customer_id=o.customer_id
JOIN Order_Details od ON o.order_id=od.order_id
GROUP BY c.customer_name;
SELECT category, AVG(price) AS avg_price FROM Books GROUP BY category;
SELECT title FROM Books WHERE book_id NOT IN (SELECT DISTINCT book_id FROM Order_Details);
SELECT b.title, SUM(od.quantity) AS sold_qty
FROM Books b
JOIN Order_Details od ON b.book_id=od.book_id
GROUP BY b.title
HAVING sold_qty > 1;
SELECT MONTH(order_date) AS month, COUNT(*) AS total_orders
FROM Orders
GROUP BY MONTH(order_date);
SELECT c.customer_name, SUM(o.total_amount) AS total_spent
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_name
ORDER BY total_spent DESC
LIMIT 2;
SELECT b.category, SUM(od.quantity) AS total_sold
FROM Books b
JOIN Order_Details od ON b.book_id = od.book_id
GROUP BY b.category
ORDER BY total_sold DESC
LIMIT 1;
SELECT c.city, SUM(o.total_amount) AS city_revenue
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
GROUP BY c.city
ORDER BY city_revenue DESC;
SELECT title, stock
FROM Books
WHERE stock < (SELECT AVG(stock) FROM Books);
SELECT customer_name
FROM Customers
WHERE customer_id NOT IN (SELECT DISTINCT customer_id FROM Orders);
SELECT b.author, SUM(od.quantity) AS books_sold
FROM Books b
JOIN Order_Details od ON b.book_id = od.book_id
GROUP BY b.author
ORDER BY books_sold DESC;
