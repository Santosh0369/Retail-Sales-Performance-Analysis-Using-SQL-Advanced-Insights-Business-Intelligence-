# 📊 Retail Sales Performance Analysis Using SQL (Advanced Insights & Business Intelligence)

---

## 1️⃣ Executive Summary

This project focuses on **analyzing retail sales performance** using SQL to generate actionable business insights. Building on foundational data exploration, this analysis dives deeper into customer behaviour, product performance, and revenue contribution.

The project leverages advanced SQL techniques such as joins, aggregations, and ranking functions to identify trends, top-performing entities, and areas of improvement, enabling data-driven decision-making.

---

## 2️⃣ Business Problem

Retail businesses need to answer critical questions such as:

* Which products generate the highest and lowest revenue?
* Who are the most valuable customers?
* Which customers are least engaged?
* Where should the business focus to maximize revenue?

Without structured analysis, businesses risk:

* Poor product strategy
* Inefficient customer targeting
* Missed revenue opportunities

This project solves these problems using SQL-based performance analysis.

---

## 3️⃣ Methodology

The analysis follows a structured approach:

### 🔹 Data Integration

* Joined fact table (`fact_sales`) with dimension tables:

  * `dim_products`
  * `dim_customers`

### 🔹 Revenue Analysis

* Calculated total revenue per product
* Identified top-performing products using:

  * `SUM()` aggregation
  * `ORDER BY DESC`

### 🔹 Ranking Analysis

* Used:

  * `TOP N` queries
  * `RANK()` window function

* Identified:

  * Top 5 products
  * Bottom 5 products

### 🔹 Customer Analysis

* Ranked customers based on total revenue contribution
* Identified top 10 high-value customers

### 🔹 Engagement Analysis

* Measured customer activity using:

  * `COUNT(DISTINCT order_number)`

* Identified:

  * Least active customers

---

## 4️⃣ Skills

This project demonstrates:

* Advanced SQL Querying
* Joins (Fact & Dimension Tables)
* Aggregations (SUM, COUNT)
* Window Functions (RANK)
* Ranking & Performance Analysis
* Business KPI Analysis
* Customer Analytics
* Product Performance Evaluation

---

## 5️⃣ Results & Business Recommendation

### 📊 Key Insights:

* A small set of products contributes a significant portion of total revenue
* Top customers drive a large share of business value
* Some products consistently underperform
* Certain customers show low engagement levels

### 💡 Business Recommendations:

* Focus marketing on top-performing products
* Implement loyalty programs for high-value customers
* Investigate and optimize or remove low-performing products
* Re-engage inactive customers through targeted campaigns

---

## 6️⃣ Next Steps

To extend this analysis:

* 📈 Build dashboards using Power BI / Tableau
* ⏳ Add time-based trends (monthly, yearly analysis)
* 👥 Perform customer segmentation (RFM analysis)
* 🤖 Apply predictive analytics for sales forecasting
* 🔄 Automate reporting pipelines

---

## 📌 Conclusion

This project demonstrates how SQL can be used beyond basic querying to perform **advanced business analysis**, uncover key insights, and support strategic decision-making in a retail environment.


This script is a **next-level SQL analytics file** — it goes beyond basic EDA and focuses on:

> 📊 **Time-series analysis + performance tracking + segmentation + contribution analysis**

I’ll break it down clearly so you can **understand + explain it in interviews** 👇
(Your file: )

---

# 🧠 1. Change Over Time Analysis (Time-Series)

## 🔹 What this section does:

Tracks how business metrics **change over time (monthly/yearly)**

---

### ✅ Query 1: Year & Month Breakdown

```sql
YEAR(order_date), MONTH(order_date)
```

👉 Groups data by:

* Year
* Month

### 📊 Metrics calculated:

* Total sales
* Total customers
* Total quantity

👉 **Use:**

* Monthly sales trend
* Growth tracking

---

### ✅ Query 2: Using `DATETRUNC()`

```sql
DATETRUNC(month, order_date)
```

👉 Cleaner way to group dates into months

✔ Better for dashboards
✔ Avoids separate YEAR/MONTH columns

---

### ✅ Query 3: Using `FORMAT()`

```sql
FORMAT(order_date, 'yyyy-MMM')
```

👉 Converts date into readable format like:

* `2024-Jan`

✔ Good for reporting
❗ Slightly slower than DATETRUNC

---

# 📈 2. Cumulative Analysis (Running Totals)

## 🔹 What this does:

Tracks **growth over time**

---

### ✅ Key concept:

```sql
SUM(total_sales) OVER (ORDER BY order_date)
```

👉 Running total (cumulative sales)

---

### ✅ Also calculates:

```sql
AVG(avg_price) OVER (ORDER BY order_date)
```

👉 Moving average price

---

### 💡 Why important:

* Shows business growth trend
* Helps identify acceleration/slowdown

---

# 📊 3. Performance Analysis (Advanced)

## 🔹 This is the MOST IMPORTANT section

---

### ✅ Step 1: CTE (yearly_product_sales)

```sql
WITH yearly_product_sales AS (...)
```

👉 Creates yearly sales per product

---

### ✅ Step 2: Compare with Average

```sql
AVG(current_sales) OVER (PARTITION BY product_name)
```

👉 For each product:

* Calculates average sales across years

---

### ✅ Difference from average:

```sql
current_sales - avg_sales
```

👉 Shows:

* Above average
* Below average

---

### ✅ CASE Logic:

```sql
CASE 
    WHEN > 0 THEN 'Above Avg'
```

👉 Converts numbers → business labels

---

### ✅ Year-over-Year (YOY)

```sql
LAG(current_sales)
```

👉 Gets **previous year sales**

---

### ✅ YOY Growth:

```sql
current_sales - previous_year_sales
```

👉 Shows:

* Increase
* Decrease
* No change

---

### 💡 Why this matters:

This is **real business analysis**:

* Performance benchmarking
* Growth tracking

---

# 🧩 4. Data Segmentation Analysis

---

## 🔹 Product Segmentation

### ✅ Logic:

```sql
CASE 
    WHEN cost < 100 THEN 'Below 100'
```

👉 Groups products by cost

---

### Output:

| cost_range | total_products |

👉 Helps:

* Pricing strategy
* Inventory planning

---

## 🔹 Customer Segmentation (Very Important)

### Step 1: Calculate

* Total spending
* First order date
* Last order date
* Lifespan

---

### Step 2: Segment customers

```sql
CASE 
    WHEN lifespan >= 12 AND spending > 5000 THEN 'VIP'
```

👉 Segments:

* VIP
* Regular
* New

---

### 💡 Why this is powerful:

* Real-world **customer segmentation**
* Used in marketing & CRM

---

# 🧮 5. Part-to-Whole Analysis

## 🔹 What this does:

Finds **contribution of each category**

---

### Step 1: Total sales per category

```sql
SUM(sales_amount)
```

---

### Step 2: Overall sales

```sql
SUM(total_sales) OVER ()
```

---

### Step 3: Percentage contribution

```sql
(total_sales / overall_sales) * 100
```

---

### Output:

| category | total_sales | % contribution |

---

### 💡 Why important:

* Identifies key revenue drivers
* Helps prioritize business focus

---

# 🎯 What This Script Really Is

👉 This is:

### ✅ **Advanced SQL Analytics / Business Intelligence Analysis**

---

# 🚀 Skills Demonstrated

This script shows:

✔ Time-series analysis
✔ Window functions (LAG, SUM OVER, AVG OVER)
✔ CTEs (Common Table Expressions)
✔ Customer segmentation
✔ Product segmentation
✔ YOY growth analysis
✔ Contribution analysis

---

# 💬 Interview Explanation (Use This!)

> "This SQL script performs advanced analytics on retail data, including time-series analysis to track trends, cumulative analysis for growth tracking, and performance analysis using window functions like LAG for year-over-year comparisons. It also includes customer and product segmentation using CASE statements and part-to-whole analysis to measure category contribution to total revenue."

---

# 🧠 Simple Summary

👉 In one line:

> This code analyzes **how the business performs over time, who the best customers are, which products matter most, and where growth is happening**

---

If you want next step, I can:

* Create **README for THIS script (most powerful project)**
* Or give **real business insights you can speak in interviews (game changer)** 🚀


---
