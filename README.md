# 📊 Atliq Hardware Sales Analysis (2017–2020)

This project analyzes the sales data of **Atliq Hardware** using **MySQL Workbench** and **Power BI**. The goal is to provide meaningful business insights to the CEO to support better decision-making.

---

## 📁 Dataset Overview

- Data Source: Atliq Hardware (2017–2020)
- Key Tables: `transactions`, `customers`, `products`, `markets`, `date`
- Currency: INR & USD
- Market Code for Chennai: `Mark001`

---

## 🧰 Tools Used

- **MySQL Workbench** – Data querying, joins, aggregations
- **Power BI Desktop** – Data visualization, ETL process
- **Power BI Mobile Layout** – Dashboard design for mobile view
- **M Language (Power Query)** – Used in Power BI for data transformation

---

## 🔄 ETL Process in Power BI

1. **Imported cleaned tables** from MySQL into Power BI Desktop  
2. **Removed**:
   - Duplicate rows  
   - Blank values in key columns  
3. **Currency Normalization** – Converted all USD transactions to INR  
   - Used the following **M Code**:
     ```m
     = Table.AddColumn(#"Cleanup duplicate currency", "Normalize sales Amount", 
         each if [currency] = "USD#(cr)" then [sales_amount] * 87 else [sales_amount])
     ```
4. Ensured all sales amounts were normalized for accurate analysis

---

## 📈 Dashboard Creation (Power BI)

Designed a professional and interactive dashboard with the following visuals:

- 📅 **Total Revenue Over the Years**  
- 📦 **Sales by Product and Market**  
- 💰 **Currency Comparison (INR vs USD)**  
- 📊 **Year-on-Year Sales Growth**

✅ **Published** the dashboard for both:
- **Web View**
- **Mobile Layout** (Optimized for phone screens)

🔗 [**View Power BI Dashboard**](https://app.powerbi.com/groups/me/reports/101592dd-3f7f-49e1-b76e-1a3727eb85e2/988780d47f97312f7011?experience=power-bi)

---

## 🔍 Key SQL Queries (MySQL Workbench)

Some sample queries used for analysis:
```sql
-- Total number of customers
SELECT COUNT(*) FROM customers;

-- Transactions in Chennai market
SELECT * FROM transactions WHERE market_code = 'Mark001';

-- Total revenue in 2020 (INR & USD)
SELECT SUM(sales_amount) 
FROM transactions 
INNER JOIN date ON transactions.order_date = date.date 
WHERE date.year = 2020 AND TRIM(currency) IN ('INR', 'USD');
