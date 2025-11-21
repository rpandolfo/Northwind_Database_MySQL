# 📚 Northwind Database Analysis Using MySQL Workbench

[![SQL](https://img.shields.io/badge/SQL-Query%20Analysis-4479A1?logo=postgresql&logoColor=white)]()
[![Database](https://img.shields.io/badge/Database-MySQL-00618A?logo=mysql&logoColor=white)]()
[![Project Status](https://img.shields.io/badge/Status-Completed-success)]()

## 📝 Project Summary

This project provides a structured introduction to relational databases and SQL querying using the **Northwind dataset**, completed during a **Data Technician Bootcamp**. The work mirrors the analytical tasks expected of a **Junior Data Analyst**.

The workbook gradually develops from foundational database principles to advanced analytical SQL queries. It includes hands-on exercises covering filtering, sorting, aggregations, conditional logic, and multi-table JOINs—applied to real-world business cases such as:

- Customer segmentation  
- Product and category analysis  
- Order tracking and performance reporting  
- Supplier and inventory insights  

**Core skills demonstrated:**

- Understanding **primary, secondary, and foreign keys**  
- Differentiating **relational vs. non-relational databases**  
- Writing clean, efficient **SQL queries**  
- Applying **JOIN types** to combine and analyze related tables  
- Converting business needs into actionable analytical outputs  

---

## 🔑 Database Keys and Relationships

| Concept           | Explanation                                                                 |
|------------------|-----------------------------------------------------------------------------|
| **Primary Key**   | A field that **uniquely identifies a record** within a table.               | 
| **Secondary Key** | A non-unique field used to **retrieve records** and provide extra access.   | 
| **Foreign Key**   | A primary key from another table used to **link related records**.          | 

---

## 🗄️ Relational vs. Non-Relational Databases

| Database Type       | Description                                                             | Best Fit & Why                                                |
|--------------------|-------------------------------------------------------------------------|--------------------------------------------------------------|
| **Relational**      | Stores structured data in **tables with defined relationships**.        | Ideal for structured information requiring accuracy and joins. |
| **Non-Relational**  | Handles **unstructured formats** (documents, key-value, graph, etc.).   | Best for images, multimedia, and flexible large-scale data. |

---

# Basic SQL Queries (Northwind Database)

| Task | Objective | SQL Query |
|------|-----------|-----------|
| **1. Full Customer Data** | Retrieve all columns from the `Customers` table. | `SELECT * FROM customers;` |
| **2. Customer Names and Cities** | Retrieve only `CustomerName` and `City`. | `SELECT CustomerName, City FROM customers;` |
| **3. Unique Cities** | Retrieve distinct city names. | `SELECT DISTINCT City FROM customers;` |
| **4. High-Value Products** | Retrieve products priced above 50. | `SELECT * FROM products WHERE Price > 50;` |
| **5. International Customers** | Get customers in the USA or UK. | `SELECT * FROM customers WHERE Country = 'USA' OR Country = 'UK';` |
| **6. Recent Orders Report** | Retrieve orders sorted by most recent date. | `SELECT * FROM orders ORDER BY OrderDate DESC;` |
| **7. Mid-Range Products** | Products priced between 20 and 50. | `SELECT * FROM products WHERE Price BETWEEN 20 AND 50 ORDER BY Price DESC;` |
| **8. Local Marketing (USA)** | Customers in the USA, in Portland or Kirkland. | `SELECT * FROM customers WHERE Country = 'USA' AND (City = 'Portland' OR City = 'Kirkland') ORDER BY CustomerName ASC;` |
| **9. UK or London Customers** | Customers who are in the UK OR located in London. | `SELECT * FROM customers WHERE Country = 'UK' OR City = 'London' ORDER BY CustomerName DESC;` |
| **10. Product Inventory** | Products in CategoryID 1 or 2. | `SELECT * FROM products WHERE CategoryID IN (1, 2) ORDER BY ProductName ASC;` |

---

## 🔗 JOIN Types Overview

| JOIN Type        | Description                                                           | Example Use Case |
|------------------|-----------------------------------------------------------------------|------------------|
| **Self JOIN**     | A table joined to itself.                                             | Employees and their managers. |
| **Right JOIN**    | All rows from the **right** table + matches from the left.            | Show all orders, even without matching customers. |
| **Full JOIN**     | All rows with matches from either table.                              | Combine customer and order data with gaps. |
| **Inner JOIN**    | Returns **only matching** rows.                                       | Customers who have placed orders. |
| **Cross JOIN**    | Returns **every combination** of two tables.                          | All size–color–fit options for clothing. |
| **Left JOIN**     | All rows from the **left** table + matches from the right.            | All customers, even those without orders. |

---

## 🧪 Practical JOIN Queries

| Task | Objective | SQL Query |
|------|-----------|-----------|
| **1. Products to Suppliers** | Match each product with its supplier. | `SELECT ProductName, SupplierName FROM products JOIN suppliers ON products.SupplierID = suppliers.SupplierID;` |
| **2. Classifying Products** | Display products with category names. | `SELECT ProductName, CategoryName FROM products JOIN categories ON products.CategoryID = categories.CategoryID;` |
| **3. Meat/Poultry Report** | Products from the *Meat/Poultry* category. | `SELECT ProductName, CategoryName FROM products JOIN categories ON products.CategoryID = categories.CategoryID WHERE CategoryName = 'Meat/Poultry';` |
| **4. Complete Order Overview** | Orders with customer and employee details. | `SELECT OrderID, OrderDate, CustomerName, CONCAT_WS(' ', FirstName, LastName) AS EmployeeName FROM orders JOIN customers ON orders.CustomerID = customers.CustomerID JOIN employees ON orders.EmployeeID = employees.EmployeeID;` |
| **5. Supply Chain Overview** | Product, category, and supplier combined. | `SELECT ProductName, categories.CategoryName, suppliers.SupplierName FROM products JOIN categories ON products.CategoryID = categories.CategoryID JOIN suppliers ON products.SupplierID = suppliers.SupplierID;` |
| **6. Yearly Order Summary (1996)** | 1996 orders with customer and product info. | `SELECT CustomerName, orders.CustomerID, OrderDate, ProductName FROM orders JOIN customers ON orders.CustomerID = customers.CustomerID JOIN order_details ON orders.OrderID = order_details.OrderID JOIN products ON order_details.ProductID = products.ProductID WHERE OrderDate LIKE '1996%';` |
| **7. Product Count by Category** | Number of products per category. | `SELECT CategoryName, COUNT(ProductName) AS TotalQuantity FROM products JOIN categories ON categories.CategoryID = products.CategoryID GROUP BY CategoryName;` |
| **8. Sales Volume Breakdown** | Product price and total quantity ordered. | `SELECT Price, SUM(Quantity) AS TotalQuantity, ProductName FROM products JOIN order_details ON products.ProductID = order_details.ProductID GROUP BY ProductName, Price;` |

---

