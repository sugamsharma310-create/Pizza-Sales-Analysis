
# 🍕 Pizza Sales Data Analytics Report

An end-to-end **Pizza Sales Data Analytics project** using **SQL and Microsoft Power BI** to transform transactional sales data into meaningful business insights through KPI analysis, sales trends, category analysis, and product performance analysis.

---

## 📌 Project Overview

This project analyzes pizza sales data to understand overall sales performance, customer ordering patterns, pizza category and size contribution, and individual product performance.

The project combines:

* **SQL** for data analysis and KPI calculations
* **Microsoft Power BI** for interactive dashboard development
* Business-focused visualizations for identifying sales trends and product performance

The SQL analysis includes core metrics such as Total Revenue, Average Order Value, Total Pizzas Sold, Total Orders, and Average Pizzas per Order.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* Calculate important sales KPIs
* Analyze daily and monthly order trends
* Understand revenue contribution by pizza category
* Analyze revenue contribution by pizza size
* Identify the best-performing pizzas
* Identify lower-performing pizzas
* Analyze pizza sales based on revenue, quantity, and order volume
* Build an interactive Power BI dashboard for business analysis

---

## 🛠️ Tools & Technologies

| Tool / Technology            | Purpose                                 |
| ---------------------------- | --------------------------------------- |
| **SQL**                      | Data analysis and KPI calculations      |
| **Microsoft Power BI**       | Interactive dashboard and visualization |
| **Power BI Filters/Slicers** | Dynamic data exploration                |
| **Transactional Sales Data** | Source dataset                          |

---

## 📊 Key Performance Indicators

The project calculates the following KPIs:

### Total Revenue

Total revenue generated from pizza sales.

```sql
SELECT SUM(total_price) AS Total_Revenue
FROM pizza_sales;
```

### Average Order Value

Average revenue generated per unique order.

```sql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value
FROM pizza_sales;
```

### Total Pizzas Sold

Total number of pizzas sold.

```sql
SELECT SUM(quantity) AS Total_pizza_sold
FROM pizza_sales;
```

### Total Orders

Number of unique orders.

```sql
SELECT COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales;
```

### Average Pizzas Per Order

Average number of pizzas included in each order.

```sql
SELECT CAST(
    CAST(SUM(quantity) AS DECIMAL(10,2)) /
    CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2))
    AS DECIMAL(10,2)
) AS Avg_Pizzas_per_order
FROM pizza_sales;
```

---

## 📈 SQL Analysis

The project contains SQL queries for several business questions.

### 1. Daily Order Trend

Orders are analyzed by day of the week using the order date.

```sql
SELECT
    DATENAME(DW, order_date) AS order_day,
    COUNT(DISTINCT order_id) AS total_orders
FROM pizza_sales
GROUP BY DATENAME(DW, order_date);
```

### 2. Monthly Order Trend

Orders are grouped by month to understand monthly ordering patterns.

```sql
SELECT
    DATENAME(MONTH, order_date) AS Month_Name,
    COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY DATENAME(MONTH, order_date);
```

### 3. Revenue by Pizza Category

The project calculates total revenue and percentage contribution for each pizza category.

```sql
SELECT
    pizza_category,
    CAST(SUM(total_price) AS DECIMAL(10,2)) AS total_revenue,
    CAST(
        SUM(total_price) * 100 /
        (SELECT SUM(total_price) FROM pizza_sales)
        AS DECIMAL(10,2)
    ) AS PCT
FROM pizza_sales
GROUP BY pizza_category;
```

### 4. Revenue by Pizza Size

Revenue contribution is also analyzed by pizza size.

The analysis calculates both:

* Total revenue
* Percentage of overall sales

---

## 🍕 Product Performance Analysis

The project analyzes individual pizza products using three major performance indicators:

### Revenue

Identifies the:

* Top 5 pizzas by revenue
* Bottom 5 pizzas by revenue

### Quantity Sold

Identifies the:

* Top 5 pizzas by quantity sold
* Bottom 5 pizzas by quantity sold

### Total Orders

Identifies the:

* Top 5 pizzas by number of orders
* Bottom 5 pizzas by number of orders

Example:

```sql
SELECT TOP 5
    pizza_name,
    SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC;
```

The supplied SQL project also supports filtering the analysis by pizza category using a `WHERE` clause.

---

## 📊 Power BI Dashboard

The Power BI report provides an interactive interface for exploring pizza sales performance.

### Dashboard Pages

#### 🏠 Home

The Home dashboard provides a high-level view of sales performance using:

* KPI cards
* Order trend analysis
* Pizza category analysis
* Pizza size analysis
* Revenue distribution
* Quantity sold analysis

#### 🏆 Best/Worst Sellers

This page focuses on product-level performance and provides comparisons of:

* Top pizzas by revenue
* Bottom pizzas by revenue
* Top pizzas by orders
* Bottom pizzas by orders
* Top pizzas by quantity
* Bottom pizzas by quantity

---

## 🎛️ Interactive Filters

The dashboard provides interactive filtering capabilities, including:

* **Order Date**
* **Pizza Category**

These filters allow users to explore the dashboard dynamically and focus on specific periods or product categories.

---

## 📌 Business Questions Answered

The project is designed to answer questions such as:

1. What is the total revenue generated?
2. What is the average order value?
3. How many pizzas have been sold?
4. How many unique orders have been placed?
5. What is the average number of pizzas per order?
6. How do orders vary by day of the week?
7. How do orders vary by month?
8. Which pizza categories contribute to revenue?
9. Which pizza sizes contribute most to revenue?
10. Which pizzas generate the highest revenue?
11. Which pizzas generate the lowest revenue?
12. Which pizzas have the highest quantity sold?
13. Which pizzas have the lowest quantity sold?
14. Which pizzas appear in the highest number of orders?
15. Which pizzas appear in the lowest number of orders?

---

## 🧠 Skills Demonstrated

This project demonstrates practical skills in:

### SQL

* `SELECT`
* `SUM()`
* `COUNT()`
* `COUNT(DISTINCT)`
* `GROUP BY`
* `ORDER BY`
* `TOP`
* `WHERE`
* Date functions
* Calculated percentages
* KPI development
* Ranking analysis

### Power BI

* Dashboard development
* KPI cards
* Interactive slicers
* Trend analysis
* Category analysis
* Product ranking
* Data visualization
* Business intelligence reporting

### Data Analytics

* Exploratory data analysis
* Sales performance analysis
* Product performance analysis
* Trend analysis
* Business KPI analysis
* Data storytelling

---

## 📂 Project Structure

A recommended GitHub repository structure is:

```text
pizza-sales-data-analytics/
│
├── README.md
│
├── SQL/
│   └── PIZZA SALES SQL QUERIES.sql
│
├── PowerBI/
│   └── pizza sales powerbi.pbix
│
├── Dashboard/
│   └── dashboard-screenshot.png
│
└── Documentation/
    └── Pizza_Sales_Data_Analytics_Project_Report.docx
```

---

## 🚀 How to Use the Project

### Step 1 — SQL Analysis

Open the SQL query file and execute the queries against the `pizza_sales` table.

The queries calculate the project's main KPIs and perform trend, category, size, and product-level analysis.

### Step 2 — Power BI

Open the `.pbix` file using Microsoft Power BI Desktop.

Explore:

* KPI cards
* Sales trends
* Category analysis
* Size analysis
* Best/Worst seller analysis

### Step 3 — Apply Filters

Use the available dashboard filters to analyze specific:

* Dates
* Pizza categories

---

## 📈 Project Outcome

This project demonstrates how transactional sales data can be transformed into a business intelligence solution using **SQL + Power BI**.

The workflow moves from:

```text
Raw Sales Data
      ↓
SQL Analysis
      ↓
KPI Calculation
      ↓
Trend & Product Analysis
      ↓
Power BI Dashboard
      ↓
Business Insights
```

The resulting dashboard provides a structured way to monitor overall sales performance and investigate category, size, and product-level performance.

---

## 💼 Resume Project Title

**Pizza Sales Data Analytics Dashboard | SQL & Power BI**

---

## 🔗 LinkedIn Skills

Recommended skills/tags for the project:

`SQL` `Microsoft Power BI` `Data Analytics` `Business Intelligence` `Data Visualization` `Dashboard Development` `Data Storytelling` `KPI Analysis` `Sales Analytics`

---

## 👨‍💻 Project Type

**Data Analytics | Business Intelligence | Sales Analytics**

---

## 📄 Documentation

For a detailed project report covering the objectives, analytical approach, SQL analysis, Power BI dashboard structure, skills demonstrated, and resume/LinkedIn description, see the accompanying project report.

---

## ⭐ Portfolio Note

This project was created as a practical demonstration of using SQL for analytical querying and Power BI for interactive business intelligence reporting.
