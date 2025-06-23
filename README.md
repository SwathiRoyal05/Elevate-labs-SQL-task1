---

# SQL Developer Internship - Task 1: Database Setup and Schema Design

This repository contains the deliverables for Task 1 of the SQL Developer Internship, focusing on database setup and schema design for an **E-commerce** domain.

---

## Objective

The primary objective of this task was to learn how to create databases, define tables, and establish relationships between them using SQL.

---

## Chosen Domain: E-commerce

An e-commerce platform was chosen as the domain due to its common use cases and the variety of entities and relationships it presents, making it an excellent learning ground for database design principles.

---

## Entities and Relationships

The following core entities were identified for the e-commerce domain:

* **Customers:** Individuals who purchase products.
* **Products:** Items available for sale.
* **Categories:** Classifications for products (e.g., Electronics, Apparel, Books).
* **Suppliers:** Businesses that provide products.
* **Orders:** Records of customer purchases.
* **Order Items:** A junction entity to detail which products are part of a specific order, and in what quantity.

### Relationships:

* **One-to-Many (1:M):**
    * A `Customer` can place many `Orders`.
    * A `Category` can contain many `Products`.
    * A `Supplier` can supply many `Products`.
    * An `Order` can have many `Order Items`.
    * A `Product` can be included in many `Order Items`.
* **Many-to-Many (M:N):**
    * The relationship between `Orders` and `Products` is many-to-many (an order can have many products, and a product can be in many orders). This is resolved using the `Order_Items` junction table.

---

## Deliverables

### 1. SQL Script to Create Schema

The `ecommerce_schema.sql` file contains the SQL Data Definition Language (DDL) script to create the `ecommerce_db` database and all the necessary tables with their respective columns, data types, primary keys, foreign keys, and other constraints.

**Key Design Decisions:**

* **Surrogate Primary Keys:** Most tables use an `INT AUTO_INCREMENT` column as their primary key (e.g., `customer_id`, `product_id`). This provides a simple, stable, and efficient unique identifier for each record.
* **Meaningful Data Types:** Appropriate data types (e.g., `VARCHAR`, `INT`, `DECIMAL`, `TEXT`, `TIMESTAMP`, `ENUM`) are used to ensure data integrity and optimize storage.
* **Constraints:**
    * `NOT NULL`: Enforced on essential columns (e.g., `first_name`, `product_name`, `price`) to ensure critical data is always present.
    * `UNIQUE`: Applied to `email` in `Customers` and `Categories` to prevent duplicate entries for these attributes.
    * `FOREIGN KEY`: Used to establish relationships between tables, ensuring referential integrity (e.g., an `order` must be associated with an existing `customer`).
    * `DEFAULT`: Used for columns like `stock_quantity` and `order_status` to provide sensible initial values.
* **Timestamps:** `created_at` and `updated_at` columns with `DEFAULT CURRENT_TIMESTAMP` and `ON UPDATE CURRENT_TIMESTAMP` are included in `Products` for auditing and tracking record modification times.

### How to Use the SQL Script:

1.  **Open MySQL Workbench (or your preferred MySQL client).**
2.  **Connect to your MySQL server.**
3.  **Open the `ecommerce_schema.sql` file.**
4.  **Execute the script.** This will create the `ecommerce_db` database and all the tables within it.

### 2. ER Diagram

![ER Task](https://github.com/user-attachments/assets/05ed1fa4-5f48-439f-a7c6-fefda577d057)

---

## Key Concepts Demonstrated

This task allowed for practical application of several fundamental database concepts:

* **DDL (Data Definition Language):** Using `CREATE DATABASE` and `CREATE TABLE` statements.
* **Normalization:** The schema design aims to reduce data redundancy and improve data integrity by separating concerns into different tables and linking them through relationships (adhering primarily to 3rd Normal Form).
* **ER Diagrams:** Visualizing the database structure and relationships.
* **Primary Keys:** Uniquely identifying records within a table.
* **Foreign Keys:** Establishing relationships and enforcing referential integrity.
* **Constraints:** Applying rules to maintain data quality.
* **AUTO_INCREMENT:** Automatically generating unique identifiers for primary keys.

---
