# 🛒 Retail Analytics & Consumer Insights Dashboard

## 📌 Project Overview

This project presents an end-to-end Retail Analytics solution developed using SQL, PostgreSQL, Power BI, and DAX. The dashboard transforms raw retail data into actionable business insights across sales, products, customers, inventory, and marketing performance.

The objective is to help stakeholders monitor business performance, identify growth opportunities, optimize inventory management, and evaluate marketing effectiveness through interactive analytics.

---

## 🎯 Business Objectives

This dashboard was designed to answer key business questions:

- Which products and categories generate the highest revenue and profit?
- How do customer segments contribute to overall sales?
- What purchasing patterns exist across customers?
- How much inventory is being managed and where are losses occurring?
- Which marketing channels and campaigns deliver the highest ROI?

---

## 🛠️ Tools & Technologies

| Technology | Purpose |
|------------|---------|
| PostgreSQL | Data Storage & Querying |
| SQL | Data Cleaning & Analysis |
| Power BI | Dashboard Development |
| DAX | KPI & Measure Calculations |
| Excel / CSV | Source Dataset |

---

## 📂 Data Model

The project follows a dimensional data model consisting of:

### Fact Table
- vw_sales

### Dimension Tables
- products
- customers
- inventory
- marketing_performance
- delivery_performance
- customer_feedback
- Date_Table

The model uses one-to-many relationships to ensure accurate filter propagation and analytical calculations across all dashboard pages.

---

# 📊 Dashboard Pages

---

## 1️⃣ Executive Summary

Provides a high-level overview of overall business performance.

### KPIs
- Revenue
- Quantity Sold
- Total Orders
- Profit
- Customer Count
- Profit Margin %

### Key Visuals
- Sales Trend
- Product Category Contribution
- Top Brands
- Top Products

### Dashboard Preview

![Executive Summary](Images/Executive_Summary.png)

---

## 2️⃣ Product Performance

Analyzes profitability and performance across products, categories, and brands.

### KPIs
- Total SKU
- Revenue per SKU
- Average Selling Price
- Active SKU

### Key Visuals
- Top Products by Profit
- Top Brands by Profit
- Category Performance Matrix
- Product Performance Matrix

### Dashboard Preview

![Product Performance](Images/Product_Performance.png)

---

## 3️⃣ Customer Analytics

Provides insights into customer behavior, segmentation, and purchasing frequency.

### KPIs
- Total Customers
- Repeat Customers
- Repeat Customer Rate
- Average Order Value

### Key Visuals
- Customer Purchase Frequency Distribution
- Customer Segment Distribution
- Customer Performance Matrix

### Dashboard Preview

![Customer Analytics](Images/Customer_Analytics.png)

---

## 4️⃣ Inventory Analytics

Monitors inventory health and stock management performance.

### KPIs
- Total Stock Received
- Inventory Value
- Damaged Stock Value
- Damage Rate %

### Key Visuals
- Inventory Value by Category
- Damaged Stock Value by Category
- Damaged Stock Trend
- Inventory Health Matrix

### Dashboard Preview

![Inventory Analytics](Images/Inventory_Analytics.png)

---

## 5️⃣ Marketing Campaign Analytics

Evaluates campaign performance and marketing ROI.

### KPIs
- Total Spend
- Revenue Generated
- Total Conversions
- Average ROAS

### Key Visuals
- Revenue by Channel
- ROAS by Channel
- Conversion Trend
- Revenue by Target Audience
- Campaign Performance Matrix

### Dashboard Preview

![Marketing Analytics](Images/Marketing_Campaign_Analytics.png)

---

# 🧮 Key DAX Measures

### Revenue

```DAX
Revenue =
SUM(vw_sales[sales_amount])
```

### Profit

```DAX
Profit =
SUMX(
    products,
    RELATED(vw_sales[sales_amount]) *
    (products[margin_percentage]/100)
)
```

### Profit Margin %

```DAX
Profit Margin % =
DIVIDE([Profit],[Revenue])
```

### Inventory Value

```DAX
Inventory Value =
SUMX(
    inventory,
    inventory[stock_received] *
    RELATED(products[mrp])
)
```

### ROAS

```DAX
ROAS =
DIVIDE(
    SUM(marketing_performance[revenue_generated]),
    SUM(marketing_performance[spend])
)
```

---

# 🗄️ SQL Analysis

SQL was used for:

- Data cleaning and transformation
- Revenue analysis
- Product performance analysis
- Customer segmentation
- Inventory monitoring
- Marketing campaign evaluation
- Business reporting views

Example:

```sql
SELECT
    category,
    SUM(sales_amount) AS revenue
FROM vw_sales
GROUP BY category;
```

---

# 📈 Key Business Insights

- Identified high-profit products and brands driving revenue.
- Analyzed customer purchase frequency and segment performance.
- Measured inventory value and stock damage trends.
- Evaluated marketing campaign effectiveness using ROAS and conversion metrics.
- Developed an integrated retail analytics solution covering multiple business functions.

---

# 🚀 Future Enhancements

- Sales Forecasting
- Customer Churn Prediction
- Demand Forecasting
- Inventory Optimization
- Marketing Performance Forecasting

---

## 👩‍💻 Author

**Khushi Rajput**

M.Tech (AI & Data Science)  
Business Intelligence Developer | Aspiring Data Scientist

LinkedIn: Add Your LinkedIn Profile

---
