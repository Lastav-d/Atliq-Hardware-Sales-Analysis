# 📊 Atliq Hardware Sales Analysis (2017–2020)

This project focuses on analyzing the sales data of **Atliq Hardware** using **MySQL Workbench** and **Power BI**. The goal was to extract business insights from the raw data and present them to the CEO to help in strategic decision-making.

---

## 📁 Dataset Details

- Sales data from **2017 to 2020**
- Tables include: `transactions`, `customers`, `products`, `markets`, `date`
- Currency: INR and USD

---

## 🧰 Tools & Technologies

- **MySQL Workbench** – Data cleaning, SQL querying, joins, aggregations
- **Power BI** – ETL, data transformation, visual analytics
- **DAX / M Code** – For calculated columns and filters

---

## 🔍 Project Workflow

### 1. Data Cleaning & SQL Queries (MySQL Workbench)
- Identified duplicate records and blank entries
- Joined `transactions` with `date` table to filter by year and month
- Filtered data by market, customer, and currency
- Key SQL Queries used:
  ```sql
  SELECT * FROM customers;
  SELECT COUNT(*) FROM customers;
  SELECT DISTINCT product_code FROM transactions WHERE market_code = 'Mark001';
  SELECT SUM(sales_amount) FROM transactions
  INNER JOIN date ON transactions.order_date = date.date
  WHERE date.year = 2020 AND TRIM(currency) IN ('INR', 'USD');
