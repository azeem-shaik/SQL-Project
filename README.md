# 📊 SQL Ad-hoc Analysis – AtliQ Hardware

Welcome to my ad-hoc SQL project built using **MySQL** on the **AtliQ Hardware** dataset. This project focuses on answering key business questions through data-driven insights.

---

## 📚 Table of Contents

- [🏢 About AtliQ Hardware](#-about-atliq-hardware)
- [🧠 Problem Statement](#-problem-statement)
- [📌 Business Requests & Solutions](#-business-requests--solutions)
- [💻 Demo Query Examples](#-demo-query-examples)

---

## 🏢 About AtliQ Hardware
**AtliQ Hardware** is a fictional company and a leading producer of electronic hardware in India. This project simulates real-world data analytics scenarios for such an organization.

---

## 🧠 Problem Statement
You are given access to multiple datasets that reflect the operations of AtliQ Hardware. Your objective is to write SQL queries that address specific business questions by extracting actionable insights. These insights are intended to help stakeholders make informed decisions quickly and effectively.

---

## 📌 Business Requests & Solutions

### 1. 📦 Monthly Product Sales – Amazon India (FY 2021)
Generate a report of **monthly aggregated sales by product** specifically for **Amazon India** customers in **Fiscal Year 2021**.

### 2. 📈 Monthly Gross Sales – Croma India
Provide a **monthly gross sales report** for **Croma India** customers.

### 3. ⚙️ Stored Procedure: Monthly Gross Sales
A stored procedure to automatically generate the **monthly gross sales report**.

### 4. 🏅 Stored Procedure: Market Badge Classification
Assign a **“Gold”** badge if sold quantity > 5 million, else **“Silver”**.

### 5. 👑 Stored Procedure: Top Customers
Get the **top-performing customers** based on revenue.

### 6. 🥇 Stored Procedure: Top Products
Return **top-selling products** across all markets.

### 7. 🌍 Stored Procedure: Top Markets
Identify **top markets** based on total sales.

### 8. 🎯 Forecast Accuracy Report
Create an **aggregated forecast accuracy report** by customer.

### 9. 🌐 Stored Procedure: Top Markets by Region
List **top markets by region** based on performance.

### 10. 🧩 Stored Procedure: Top Products by Division
Display **top products per division** by quantity sold.

---

## 💻 Demo Query Examples

### ✅ Monthly Product Sales – Amazon India
```sql
SELECT 
    p.product_name,
    MONTH(f.date) AS month,
    SUM(f.sold_quantity) AS total_quantity
FROM 
    fact_sales_monthly f
JOIN 
    dim_customer c ON f.customer_code = c.customer_code
JOIN 
    dim_product p ON f.product_code = p.product_code
WHERE 
    c.customer = 'Amazon India' AND f.fiscal_year = 2021
GROUP BY 
    p.product_name, MONTH(f.date)
ORDER BY 
    p.product_name, month;
