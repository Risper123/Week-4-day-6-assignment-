#week 4 day 6 assignment 

Assignment Questions
💳 Bills and Payments Table Join
You have two tables, bills and payments, where the BillID column is common between them. Write an SQL query that uses INNER JOIN to retrieve the following details:
SELECT 
    b.TotalAmount, 
    b.Status, 
    p.DueDate, 
    p.PaymentMethod, 
    p.PaymentAmount
FROM 
    bills b
INNER JOIN 
    payments p ON b.BillID = p.BillID;
    

TotalAmount and Status from the bills table.
DueDate, PaymentMethod, and PaymentAmount from the payments table.
🛍️ Customer and Bills Table Join
You have two tables, customer and bills, where the customerID column is common between them. Write an SQL query that uses LEFT JOIN to retrieve the following details:

customerName, email, and customerAddress from the customer table.
TotalAmount and Status from the bills table.

SELECT 
    c.customerName, 
    c.email, 
    c.customerAddress, 
    b.TotalAmount, 
    b.Status
FROM 
    customer c
LEFT JOIN 
    bills b ON c.customerID = b.customerID;
    
🧾 Bills and Bill Items Table Join
You have two tables, bills and bill_items, where the BillID column is common between them. Write an SQL query that uses RIGHT JOIN to retrieve the following details:

BillDate and DueDate from the bills table.
Status, ItemDescription, Quantity, and LineTotal from the bill_items table.

SELECT 
    b.BillDate, 
    b.DueDate, 
    bi.Status, 
    bi.ItemDescription, 
    bi.Quantity, 
    bi.LineTotal, 
    DATEDIFF(b.DueDate, b.BillDate) AS Number_of_Days
FROM 
    bills b
RIGHT JOIN 
    bill_items bi ON b.BillID = bi.BillID;
    
Calculate the difference in days between BillDate and DueDate as Number_of_Days.
👤 One-to-One Relationship: Users and User Profiles
You are given two tables, users and user_profiles, where:

The users table contains user_id and username.
The user_profiles table contains profile_id, user_id, and profile_data.
Write an SQL query to create the two tables, ensuring the following:

The users table has user_id as the primary key and a username.
The user_profiles table has profile_id as the primary key, and it references the user_id from the users table with a foreign key constraint.
Ensure that the user_id in the user_profiles table is unique, creating a one-to-one relationship between the two tables.

CREATE TABLE users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255)
);

CREATE TABLE user_profiles (
    profile_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT UNIQUE, 
    profile_data TEXT,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

👥 One-to-Many Relationship: Departments and Employees
You are given two tables, departments and employees, where:

The departments table contains department_id and department_name.
The employees table contains employee_id, employee_name, and department_id.
Write an SQL query to create the two tables, ensuring the following:

The departments table has department_id as the primary key and a department_name.
The **employees **table has employee_id as the primary key, and the department_id is a foreign key referencing the department_id in the departments table.
The relationship between departments and employees is a one-to-many relationship (one department can have multiple employees).

CREATE TABLE departments (
    department_id INT AUTO_INCREMENT PRIMARY KEY,
    department_name VARCHAR(255)
);

CREATE TABLE employees (
    employee_id INT AUTO_INCREMENT PRIMARY KEY,
    employee_name VARCHAR(255),
    department_id INT,
    FOREIGN KEY (department_id) REFERENCES departments(department_id)
); 

📋 Categories, Bills, and Customer Tables Join
You are given three tables: categories, bills, and customer, where:

The categories table contains CategoryID and CategoryName.
The bills table contains BillID, CategoryID, TotalAmount, and DueDate.
The customer table contains CustomerID, customerName, and customerAddress.
Write an SQL query that uses INNER JOIN and LEFT JOIN to retrieve the following details:

CategoryName from the categories table.
TotalAmount and DueDate from the bills table.
customerName and customerAddress from the customer table.
SELECT 
    c.CategoryName, 
    b.TotalAmount, 
    b.DueDate, 
    cust.customerName, 
    cust.customerAddress
FROM 
    categories c
INNER JOIN 
    bills b ON c.CategoryID = b.CategoryID
LEFT JOIN 
    customer cust ON b.customerID = cust.customerID;

