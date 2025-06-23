# Library Management System

This project contains the SQL schema and code for managing books, members, and loans in a library.

## Features
- Manage library members
- Track books and their details
- Handle book loans and returns
- Enforce data integrity with foreign keys

## Database Tables
- **Member**
- **Book**
- **Loan**

## Tech Stack
- MySQL / MariaDB
- Git & GitHub for version control

## How to Use
1. Run the SQL script in your MySQL Workbench / phpMyAdmin / XAMPP.
2. Modify or extend tables as per need.
3. Track changes using Git.
   
## CODE
--Create Database
CREATE DATABASE LibraryDB;
USE LibraryDB;

-- Member Table
CREATE TABLE Member (
  member_id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  join_date DATE NOT NULL
);

-- Book Table
CREATE TABLE Book (
  book_id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(200) NOT NULL,
  author VARCHAR(100),
  genre VARCHAR(50),
  publish_year YEAR
);

-- Loan Table
CREATE TABLE Loan (
  loan_id INT AUTO_INCREMENT PRIMARY KEY,
  book_id INT,
  member_id INT,
  loan_date DATE NOT NULL,
  return_date DATE,
  FOREIGN KEY (book_id) REFERENCES Book(book_id),
  FOREIGN KEY (member_id) REFERENCES Member(member_id)
);

