ASSIGNMENT TITLE 
INTRODUCTION & FOUNDATIONAL SKILLS 

BACKGROUND 
﻿This week, we'll be diving into the exciting world of SQL and databases! We'll explore what SQL is used for, how it benefits web applications, and the building blocks of databases: tables, columns, and data types. But most importantly, we'll get our hands dirty by creating a basic database structure for our upcoming Expense Tracker project!

LEARNING OBJECTIVES 
1. Understand the purpose and applications of SQL, particularly for web applications.
2. Identify the fundamental components of a database: tables, columns, and data types.

TASK 
Design a basic database schema for your Expense Tracker project. 


OVERVIEW OF SQL 
SQL (Structured Query Language) is a standardized programming language used to manage and manipulate relational databases. It allows you to perform tasks such as querying data, updating records, deleting records, and creating and modifying database structures. SQL is essential for web applications as it enables the back-end to interact with the database efficiently.

FUNDAMENTAL COMPONENTS OF A DATABASE 
1. Tables: A table is a collection of related data entries and consists of rows and columns. Each table in a database represents a specific type of entity (e.g., users, expenses).
2. Columns: Columns, also known as fields, are the attributes of the table. Each column has a specific data type that defines the kind of data it can hold.
3. Data Types: Data types define the type of data that can be stored in a column. Common data types include INTEGER, VARCHAR, DATE, DECIMAL, etc.

DESIGNING A BASIC DATABASE SCHEMA FOR AN EXPENSE TRACKER PROJECT 
Here’s a simple schema for an Expense Tracker project. 

#We’ll create four tables: Users, Categories, Expenses, and Budgets.


1. Users Table: Stores information about users.

Columns
user_id:      INT, Primary Key, Auto Increment
username:     VARCHAR(50), Unique, Not Null
email:        VARCHAR(100), Unique, Not Null
password:     VARCHAR(255), Not Null
created_at:   TIMESTAMP, Default Current Timestamp

SQL code
CREATE TABLE Users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
); 


2. Categories Table: Stores different expense categories.

Columns 
category_id:       INT, Primary Key, Auto Increment
category_name:     VARCHAR(50), Not Null
user_id:           INT, Foreign Key, Not Null

SQL Code
CREATE TABLE Categories (
    category_id INT PRIMARY KEY AUTO_INCREMENT,
    category_name VARCHAR(50) NOT NULL,
    user_id INT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);


3. Expenses Table: Stores expense records.

Columns 
expense_id:     INT, Primary Key, Auto Increment
amount:         DECIMAL(10, 2), Not Null
expense_date:   DATE, Not Null
category_id:    INT, Foreign Key, Not Null
user_id:        INT, Foreign Key, Not Null
description:    VARCHAR(255), Null

SQL code
CREATE TABLE Expenses (
    expense_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(10, 2) NOT NULL,
    expense_date DATE NOT NULL,
    category_id INT NOT NULL,
    user_id INT NOT NULL,
    description VARCHAR(255),
    FOREIGN KEY (category_id) REFERENCES Categories(category_id),
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
); 


4. Budgets Table: Stores budget information for different categories and users.

Columns 
budget_id:     INT, Primary Key, Auto Increment
amount:        DECIMAL(10, 2), Not Null
start_date:    DATE, Not Null
end_date:      DATE, Not Null
category_id:   INT, Foreign Key, Not Null
user_id:       INT, Foreign Key, Not Null

SQL code
CREATE TABLE Budgets (
    budget_id INT PRIMARY KEY AUTO_INCREMENT,
    amount DECIMAL(10, 2) NOT NULL,
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    category_id INT NOT NULL,
    user_id INT NOT NULL,
    FOREIGN KEY (category_id) REFERENCES Categories(category_id),
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
); 








