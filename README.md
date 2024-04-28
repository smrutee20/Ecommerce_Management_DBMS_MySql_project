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
![Entity Relation Diagram](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/er_diagram.png)


### 2.3 Relational Database Schema
![Relational Database Schema](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Relational%20Database%20Schema.png)


## 3. Implementation

You can directly copy and paste all the commands from the text given here into the SQL console to create and insert values into your table.

### 3.1 Creating Tables

```sql
    CREATE TABLE Cart (
    Cart_id VARCHAR(7) NOT NULL,
    PRIMARY KEY(Cart_id)
    );
```
![Cart Table](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Cart%20Description.jpg)

```sql
    CREATE TABLE Customer (
    Customer_id VARCHAR(6) NOT NULL,
    c_pass VARCHAR(10) NOT NULL,
    Name VARCHAR(20) NOT NULL,
    Address VARCHAR(20) NOT NULL,
    Pincode INT(6) NOT NULL,
    Phone_number_s INT(10) NOT NULL,
    Cart_id VARCHAR(7) NOT NULL,
    PRIMARY KEY (Customer_id),
    FOREIGN KEY(Cart_id) REFERENCES Cart(Cart_id)
    );
```
![Customer Table](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Customer%20table%20description.jpg)

```sql
    CREATE TABLE Seller (
    Seller_id VARCHAR(6) NOT NULL,
    s_pass VARCHAR(10) NOT NULL,
    Name VARCHAR(20) NOT NULL,
    Address VARCHAR(10) NOT NULL,
    PRIMARY KEY (Seller_id)
    );
```
![Seller Table](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Seller%20Table%20description.jpg)

```sql
    CREATE TABLE Seller_Phone_num (
    Phone_num INT(10) NOT NULL,
    Seller_id VARCHAR(6) NOT NULL,
    PRIMARY KEY (Phone_num, Seller_id),
    FOREIGN KEY (Seller_id) REFERENCES Seller(Seller_id)
    ON DELETE CASCADE
    );
```
![Seller Phone Number](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Seller%20Phone%20number%20table%20description.jpg)

```sql
        CREATE TABLE Payment
        (
        payment_id VARCHAR(7) NOT NULL,
        payment_date DATE NOT NULL,
        Payment_type VARCHAR(10) NOT NULL,
        Customer_id VARCHAR(6) NOT NULL,
        Cart_id VARCHAR(7) NOT NULL,
        PRIMARY KEY (payment_id),
        FOREIGN KEY (Customer_id) REFERENCES Customer(Customer_id),
        FOREIGN KEY (Cart_id) REFERENCES Cart(Cart_id),
        total_amount numeric(6)
        );
```
![Payment Table](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Payment%20table%20description.jpg)

```sql
        CREATE TABLE Product
        (
        Product_id VARCHAR(7) NOT NULL,
        Type VARCHAR(7) NOT NULL,
        Color VARCHAR(15) NOT NULL,
        P_Size VARCHAR(2) NOT NULL,
        Gender CHAR(1) NOT NULL,
        Commission NUMBER(2) NOT NULL,
        Cost NUMBER(5) NOT NULL,
        Quantity NUMBER(2) NOT NULL,
        Seller_id VARCHAR(6),
        PRIMARY KEY (Product_id),
        FOREIGN KEY (Seller_id) REFERENCES Seller(Seller_id)
        ON DELETE SET NULL
        );
```
![Product Table](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Product%20table%20description.jpg)

```sql
        CREATE TABLE Cart_item
        (
        Quantity_wished NUMBER(1) NOT NULL,
        Date_Added DATE NOT NULL,
        Cart_id VARCHAR(7) NOT NULL,
        Product_id VARCHAR(7) NOT NULL,
        FOREIGN KEY (Cart_id) REFERENCES Cart(Cart_id),
        FOREIGN KEY (Product_id) REFERENCES Product(Product_id),
        Primary key(Cart_id,Product_id)
        );
```
![Cart Item Table](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Cart%20Item%20description.jpg)

### 3.2 Inserting Values

These are some demo values.

```sql
        INSERT INTO Cart VALUES ('crt1011');
```
![Cart Values](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Cart_Values.jpg)

```sql
        INSERT INTO Customer VALUES ('cid100', 'ABCM1235', 'rajat', 'G-453', '632014', 9893135876, 'crt1011');
```
![Customer Values](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Customer%20Values.jpg)

```sql
        INSERT INTO Seller VALUES ('sid100', '12345', 'aman', 'delhi cmc');
```
![Seller Values](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Seller%20Values.jpg)

```sql
        INSERT INTO Product VALUES ('pid1001', 'jeans', 'red', '32', 'M', 10, 10005, 20, 'sid100');
```
![Product Values](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Product%20Values.jpg)

```sql
        INSERT INTO Seller_Phone_num VALUES ('9943336206', 'sid100');
```
![Seller Phone Num Values](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Seller%20Phone%20Number%20Values.jpg)

```sql
        INSERT INTO Cart_item VALUES (3, STR_TO_DATE('10-OCT-1999', '%d-%b-%Y'), 'crt1011', 'pid1001');
```
![Cart Item Values](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Cart%20Item%20Values.jpg)

```sql
        INSERT INTO Payment VALUES ('pmt1001', STR_TO_DATE('10-OCT-1999', '%d-%b-%Y'), 'online', 'cid100', 'crt1011', NULL);
```
![Payment Values](https://github.com/smrutee20/Ecommerce_dbms-project/blob/main/Payment%20Values.jpg)
