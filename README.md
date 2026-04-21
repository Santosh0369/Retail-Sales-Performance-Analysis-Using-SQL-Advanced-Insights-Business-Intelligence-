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



> 📊 **Time-series analysis + performance tracking + segmentation + contribution analysis**


---

# 🧠 1. Change Over Time Analysis (Time-Series)

## 🔹 What this section does:

Tracks how business metrics **change over time (monthly/yearly)**

---

### ✅ Query 1: Year & Month Breakdown

<img width="707" height="563" alt="image" src="https://github.com/user-attachments/assets/1fb4a749-6715-4a11-a448-f3fc727c3d7e" />


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

<img width="670" height="519" alt="image" src="https://github.com/user-attachments/assets/f3fe925e-15a3-4cea-8c81-fcdc36ebc531" />


👉 Cleaner way to group dates into months

✔ Better for dashboards
✔ Avoids separate YEAR/MONTH columns

---

### ✅ Query 3: Using `FORMAT()`

<img width="682" height="545" alt="image" src="https://github.com/user-attachments/assets/1e9b678b-6511-45de-9a58-bf91b1b150ad" />


👉 Converts date into a readable format like:

* `2024-Jan`

✔ Good for reporting
❗ Slightly slower than DATETRUNC

---

# 📈 2. Cumulative Analysis (Running Totals)

## 🔹 What this does:

Tracks **growth over time**

---

### ✅ Key concept:

<img width="820" height="607" alt="image" src="https://github.com/user-attachments/assets/8dc49424-ba6a-47c2-a186-8053e925d419" />


👉 Running total (cumulative sales)

👉 Moving average price

---

### 💡 Why important:

* Shows business growth trend
* Helps identify acceleration/slowdown

---

# 📊 3. Performance Analysis (Advanced)

## 🔹 This is the MOST IMPORTANT section

---


<img width="792" height="674" alt="image" src="https://github.com/user-attachments/assets/85c0fe42-8f67-4384-8e92-d790fe371f50" />

### ✅ CTE (yearly_product_sales)

👉 Creates yearly sales per product

---

### ✅ Compare with Average

👉 For each product:

* Calculates average sales across years

---

### ✅ Difference from average:

👉 Shows:

* Above average
* Below average

---

### ✅ CASE Logic:

👉 Converts numbers → business labels

---

### ✅ Year-over-Year (YOY)

👉 Gets **previous year sales**

---

### ✅ YOY Growth:

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

<img width="618" height="509" alt="image" src="https://github.com/user-attachments/assets/81c4cc8a-3cd9-4a4a-a971-66f431d23d7d" />


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

<img width="731" height="671" alt="image" src="https://github.com/user-attachments/assets/343ce61d-36b7-41a5-945e-0dc8c269d970" />


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

### Step 1: Total sales per category

### Step 2: Overall sales

### Step 3: Percentage contribution
---
<img width="788" height="625" alt="image" src="https://github.com/user-attachments/assets/ab32c45f-5c50-4951-b6e8-47ace3f17057" />

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

# 💬  Explanation!

> "This SQL script performs advanced analytics on retail data, including time-series analysis to track trends, cumulative analysis for growth tracking, and performance analysis using window functions like LAG for year-over-year comparisons. It also includes customer and product segmentation using CASE statements and part-to-whole analysis to measure category contribution to total revenue."

---

# 🧠 Simple Summary

> This code analyzes **how the business performs over time, who the best customers are, which products matter most, and where growth is happening**

---

---
