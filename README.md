# 💼 Zepto E-commerce Inventory Analysis (SQL Project)

Hey there — this is a SQL-based data analysis project I built to strengthen my SQL skills. I used a real-world dataset scraped from **Zepto**, one of India’s fastest-growing quick-commerce startups.

This project simulates how analysts work behind the scenes in e-commerce: from cleaning messy data to extracting actual business insights using SQL.

---

## 🧠 Who this project is for:

* Anyone prepping for **BA/Data Analyst roles**
* Folks learning **SQL through real problems**, not theory
* People building **portfolio projects** for resumes & LinkedIn

---

## 📌 What This Project Covers

The goal was to work with a realistic e-commerce inventory dataset and use SQL to:

* Clean and explore the data
* Spot problems like pricing inconsistencies or zero stock
* Write queries to extract business-relevant insights

---

## 📁 Dataset Info

The dataset (from Kaggle) was scraped from Zepto's product listings.

Each row represents a product-SKU combo — multiple entries exist for different sizes or discounts (just like real online catalogs).

### Key columns:

* `sku_id`: Unique product entry
* `name`: Product name
* `category`: Product category
* `mrp`: Price (converted from paise to ₹)
* `discountPercent`: Discount applied
* `discountedSellingPrice`: Final price
* `availableQuantity`: Stock units
* `weightInGms`: Weight of item
* `outOfStock`: True/False
* `quantity`: Package size

---

## 🔧 What I Did (Step-by-Step)

### 1. 📦 Database Setup

Created the SQL table using:

```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
```

### 2. 📥 Data Import

Imported CSV using pgAdmin. Faced UTF-8 encoding issues, fixed by re-saving the file as CSV UTF-8.

Alternative import method:

```sql
\copy zepto(category,name,mrp,discountPercent,availableQuantity,
discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'data/zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```

---

### 3. 🔍 Data Exploration

* Checked total rows and sample records
* Listed all distinct categories
* Compared in-stock vs out-of-stock products
* Found duplicates (same product, multiple SKUs)
* Null checks on all columns

---

### 4. 🧹 Data Cleaning

* Removed rows where MRP or discounted price = 0
* Converted prices from paise to ₹
* Cleaned up inconsistent weight/quantity values

---

### 5. 📊 Business Insights

Wrote queries to extract:

* 🔝 Top 10 best-value products (by discount %)
* 💸 High-priced items currently out of stock
* 💰 Potential revenue per category
* 🎯 Expensive items with very low discounts
* 🏆 Top 5 categories with highest avg discounts
* ⚖️ Price-per-gram comparison (value-for-money)
* 📦 Grouped products by weight: low/medium/bulk
* 📦 Total inventory weight per category

---

## 💡 What I Learned

* Cleaned and analyzed real-world, messy data (a lot harder than toy datasets)
* Practiced writing **business-driven SQL**
* Understood how product data affects pricing, stock, and revenue
* Improved confidence with PostgreSQL & EDA-style thinking

---

## 🛠 Tools Used

* PostgreSQL + pgAdmin
* SQL (CTEs, aggregations, filters, conditions)
* Kaggle Dataset (Zepto)

---

## 📌 How to Run This

```bash
git clone [repo-link]
cd zepto-SQL-data-analysis-project
```

* Create a PostgreSQL DB
* Run the SQL script provided
* Load dataset into pgAdmin
* Follow along and try customizing queries!

---
