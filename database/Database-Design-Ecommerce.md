# Database Design: eCommerce Website

This document outlines the database design for an eCommerce website named `myshop`. It includes the structure of tables, their columns, and relationships.

## Table of Contents

1. [Users](#users)
2. [User Addresses](#user-addresses)
3. [Categories](#categories)
4. [Products](#products)
5. [User Carts](#user-carts)
6. [Shippings](#shippings)
7. [Orders](#orders)
8. [Order Products](#order-products)

---

## Users

The `users` table stores information about the users of the eCommerce website.

### Table: `users`

| Column     | Type      | Description              |
| ---------- | --------- | ------------------------ |
| id         | INT       | Primary key              |
| name       | VARCHAR   | User's name              |
| email      | VARCHAR   | User's email             |
| mobile_no  | VARCHAR   | User's mobile number     |
| password   | VARCHAR   | User's password          |
| created_at | TIMESTAMP | Timestamp of creation    |
| updated_at | TIMESTAMP | Timestamp of last update |

---

## User Addresses

The `user_addresses` table stores the addresses of users.

### Table: `user_addresses`

| Column         | Type    | Description                   |
| -------------- | ------- | ----------------------------- |
| id             | INT     | Primary key                   |
| user_id        | INT     | Foreign key to `users` table  |
| address_type   | ENUM    | Type of address (Home/Office) |
| address_line_1 | VARCHAR | Address line 1                |
| address_line_2 | VARCHAR | Address line 2                |
| area           | VARCHAR | Area                          |
| landmark       | VARCHAR | Landmark                      |
| pincode        | VARCHAR | Pincode                       |
| city           | VARCHAR | City                          |
| state          | VARCHAR | State                         |
| country        | VARCHAR | Country                       |
| coordinates    | VARCHAR | Coordinates                   |

---

## Categories

The `categories` table stores the product categories.

### Table: `categories`

| Column    | Type    | Description                    |
| --------- | ------- | ------------------------------ |
| id        | INT     | Primary key                    |
| name      | VARCHAR | Category name                  |
| status    | BOOLEAN | Status (0/1)                   |
| parent_id | INT     | Parent category ID (0 if none) |

---

## Products

The `products` table stores information about the products available on the website.

### Table: `products`

| Column      | Type      | Description                       |
| ----------- | --------- | --------------------------------- |
| id          | INT       | Primary key                       |
| category_id | INT       | Foreign key to `categories` table |
| name        | VARCHAR   | Product name                      |
| description | TEXT      | Product description               |
| price       | DECIMAL   | Product price                     |
| quantity    | INT       | Available quantity                |
| in_stock    | BOOLEAN   | Stock status                      |
| status      | BOOLEAN   | Product status                    |
| images      | TEXT      | URLs of product images            |
| created_at  | TIMESTAMP | Timestamp of creation             |
| updated_at  | TIMESTAMP | Timestamp of last update          |
| deleted_at  | TIMESTAMP | Timestamp of deletion             |

---

## User Carts

The `user_carts` table stores the products added to the user's cart.

### Table: `user_carts`

| Column     | Type | Description                     |
| ---------- | ---- | ------------------------------- |
| id         | INT  | Primary key                     |
| user_id    | INT  | Foreign key to `users` table    |
| product_id | INT  | Foreign key to `products` table |
| quantity   | INT  | Quantity of the product         |

---

## Shippings

The `shippings` table stores the shipping zones and their prices.

### Table: `shippings`

| Column | Type    | Description    |
| ------ | ------- | -------------- |
| id     | INT     | Primary key    |
| zone   | VARCHAR | Shipping zone  |
| price  | DECIMAL | Shipping price |

---

## Orders

The `orders` table stores information about the orders placed by users.

### Table: `orders`

| Column          | Type    | Description                           |
| --------------- | ------- | ------------------------------------- |
| id              | INT     | Primary key                           |
| user_id         | INT     | Foreign key to `users` table          |
| user_address_id | INT     | Foreign key to `user_addresses` table |
| order_amount    | DECIMAL | Total order amount                    |
| shipping_amount | DECIMAL | Shipping amount                       |
| discount        | DECIMAL | Discount amount                       |
| tax             | DECIMAL | Tax amount                            |

---

## Order Products

The `order_products` table stores the products included in each order.

### Table: `order_products`

| Column           | Type    | Description                     |
| ---------------- | ------- | ------------------------------- |
| id               | INT     | Primary key                     |
| order_id         | INT     | Foreign key to `orders` table   |
| user_id          | INT     | Foreign key to `users` table    |
| product_id       | INT     | Foreign key to `products` table |
| product_name     | VARCHAR | Name of the product             |
| product_price    | DECIMAL | Price of the product            |
| product_quantity | INT     | Quantity of the product         |

---

This documentation provides a clear reference for the database design of the eCommerce website `myshop`. It includes the structure of tables, their columns, and relationships to ensure efficient data management and retrieval.
