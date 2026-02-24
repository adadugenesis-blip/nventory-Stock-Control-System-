# Inventory-Stock-Control-System-
# 📦 Inventory Stock Control System  

## 📖 Project Overview  
The **Inventory Stock Control System** is a database project designed to help businesses manage products, suppliers, and stock movements efficiently.  

The system tracks inventory levels, records stock coming in and going out, and helps prevent issues such as stock shortages, overstocking, and data inconsistency.  

This project uses a **relational database** and **MySQL** to model real-world inventory operations in a structured and reliable way.  

---

## 🛠️ Tools Used  
- MySQL  
- SQL (Structured Query Language)  
- MySQL Workbench  
- ER Diagram Tool (Draw.io / Lucidchart)  
- GitHub (Project documentation and version control)  

---

## ⚠️ Problem Statement  
Many businesses manage inventory manually or using unstructured spreadsheets. This leads to:  

- Inaccurate stock quantities  
- Difficulty tracking suppliers and products  
- Poor visibility of stock movement  
- Losses due to overstocking or stock shortages  

There is a need for a **centralized database system** that can accurately store inventory data and support efficient stock management.  

# 📦 Inventory Stock Control System  

## 📌 Full Project Questions / Tasks  

---

## 1️⃣ Database Design  

### 🔹 Why is a Relational Database Model Suitable?

A relational database model is suitable for an inventory stock control system because:

- It organizes data into structured tables (relations).
- It reduces data redundancy through normalization.
- It maintains data integrity using primary and foreign keys.
- It enforces relationships between entities.
- It allows efficient querying using SQL.
- It ensures consistency and accuracy in stock tracking.

Relational databases are ideal for handling structured data such as products, suppliers, and stock transactions.

---

### 🔹 Main Entities and Their Relationships  

The main entities in the Inventory Stock Control System include:

1. **Product**
2. **Supplier**
3. **Stock_In**
4. **Stock_Out**
5. **Inventory**

#### Relationships:

- A **Supplier** can supply many **Products** (One-to-Many).
- A **Product** can have many **Stock_In** records (One-to-Many).
- A **Product** can have many **Stock_Out** records (One-to-Many).
- **Inventory** keeps track of the current stock level of each Product.

---

### 🔹 Entity Relationship (ER) Diagram Structure  

Below is the logical structure of the database:

#### 📦 Product
- product_id (PK)
- product_name
- category
- unit_price

#### 🚚 Supplier
- supplier_id (PK)
- supplier_name
- contact_info
- address

#### 📥 Stock_In
- stockin_id (PK)
- product_id (FK)
- supplier_id (FK)
- quantity
- date_received

#### 📤 Stock_Out
- stockout_id (PK)
- product_id (FK)
- quantity
- date_sold

#### 📊 Inventory
- inventory_id (PK)
- product_id (FK)
- current_stock

---

## 2️⃣ Normalization  

### 🔹 Assume All Data is Stored in One Table  

Example of a single table design:

| ProductID | ProductName | SupplierName | SupplierPhone | QuantityIn | QuantityOut | DateReceived | DateSold |

---

### 🔹 Problems with This Design  

Storing all data in one table causes:

- ❌ Data redundancy (supplier details repeated)
- ❌ Update anomalies (changing supplier phone in multiple rows)
- ❌ Insert anomalies (cannot add supplier without product)
- ❌ Delete anomalies (deleting product removes supplier info)
- ❌ Poor data organization

---

## 🔄 Normalization Process (Up to 3NF)

### ✅ First Normal Form (1NF)

Rules:
- Remove repeating groups
- Ensure atomic values (no multiple values in one column)
- Add a primary key

Result:
- Each row contains only one product transaction.
- Primary key introduced (e.g., transaction_id).

---

### ✅ Second Normal Form (2NF)

Rules:
- Must be in 1NF
- Remove partial dependencies
- Separate data that depends only on part of a composite key

Action:
- Create separate tables for:
  - Product
  - Supplier
  - Stock Transactions

Now:
- Product details depend only on product_id.
- Supplier details depend only on supplier_id.

---

### ✅ Third Normal Form (3NF)

Rules:
- Must be in 2NF
- Remove transitive dependencies
- Non-key attributes must depend only on the primary key

Action:
- Ensure supplier contact info depends only on supplier_id.
- Ensure product price depends only on product_id.
- Separate inventory calculations from transaction tables.

Final Tables:
- Product
- Supplier
- Stock_In
- Stock_Out
- Inventory

---

## ✅ Final Outcome

After normalization to 3NF:

- Data redundancy is minimized
- Data integrity is improved
- Anomalies are eliminated
- The database becomes scalable and efficient
