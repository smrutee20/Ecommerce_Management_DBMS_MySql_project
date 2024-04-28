# Ecommerce_dbms-project
This project is a part of NIT, Arunachal Pradesh for Database Management Systems (DBMS) - CS-309 Curriculum.<br>
It contains theoretical as well as implementation in MySQL.<br>
If you liked the repo do :star: it. 

## Pre-requisite

MySQL Setup: you can follow this link: (for windows user) https://www.youtube.com/watch?v=1VyufR2x1ac

## Contents

- Project Description
- Basic structure
  - Functional requirements
  - Entity Relation (ER) diagram and constraints
  - Relational database schema
- Implementation
  - Creating tables
  - Inserting data
- Queries
  - Basic queries
  - SQL function
 
## 1. Project Description

In this modern era of online shopping no seller wants to be left behind, moreover due to its simplicity the shift from offline selling model to an online selling model is witnessing a rampant growth.<br>
Therefore, as an engineer our job is to ease the path of this transition for the seller.
Amongst many things that an online site requires the most important is a database system. Hence in this project we are planning to design a database where small clothing sellers can sell their product online.

## 2. Basic Structure

### 2.1 Functional requirement

- A new user can register on the website.
- A customer can see details of the product present in the cart
- A customer can view his order history.
- Admin can start a sale with certain discount on every product.
- Customer can filter the product based on the product details.
- A customer can add or delete a product from the cart.
- A seller can unregister/ stop selling his product.
- A seller/ customer can update his details.
- Admin can view the products purchased on particular date.
- Admin can view number of products sold on a particular date.
- A customer can view the total price of product present in the cart unpurchased.
- Admin can view details of customer who have not purchased anything.
- Admin can view total profit earned from the website.

### 2.2 Entity Relation Diagram



### 2.3 Relational Database Schema


## 3. Implementation

You can directly copy and paste all the commands from the text given here into the SQL console to create and insert values into your table.

### 3.1 Creating Tables

```CREATE TABLE Cart (
    Cart_id VARCHAR(7) NOT NULL,
    PRIMARY KEY(Cart_id)
);```

