# 🛒 Zepto Inventory Data Analysis using PostgreSQL

## 📌 Project Overview

This project analyzes Zepto's inventory dataset using PostgreSQL. The goal is to perform data cleaning, exploration, and business analysis to extract meaningful insights about product pricing, discounts, inventory availability, and category performance.

The project demonstrates practical SQL skills commonly used by Data Analysts in real-world business scenarios.

---

## 📂 Dataset Information

The dataset contains information about products available on Zepto, including:

- Product Category
- Product Name
- MRP (Maximum Retail Price)
- Discount Percentage
- Available Quantity
- Discounted Selling Price
- Product Weight
- Stock Availability
- Quantity

### Dataset Size
- **Rows:** 3,732
- **Columns:** 9

---

## 🛠️ Technologies Used

- PostgreSQL
- CSV Dataset
- Data Cleaning
- Exploratory Data Analysis (EDA)

---

## 📊 Business Analysis Questions

### Q1. Top 10 Best-Value Products by Discount

```sql
SELECT DISTINCT name, mrp, discountPercent
FROM zepto
ORDER BY discountPercent DESC
LIMIT 10;
```

---

### Q2. High MRP Products Currently Out of Stock

```sql
SELECT DISTINCT name, mrp
FROM zepto
WHERE outOfStock = TRUE
AND mrp > 300
ORDER BY mrp DESC;
```

---

### Q3. Estimated Revenue by Category

```sql
SELECT category,
SUM(discountedSellingPrice * availableQuantity) AS total_revenue
FROM zepto
GROUP BY category;
```

---

### Q4. Premium Products with Low Discounts

```sql
SELECT DISTINCT name, mrp, discountPercent
FROM zepto
WHERE mrp > 500
AND discountPercent < 10;
```

---

### Q5. Categories Offering Highest Average Discounts

```sql
SELECT category,
ROUND(AVG(discountPercent),2) AS avg_discount
FROM zepto
GROUP BY category
ORDER BY avg_discount DESC
LIMIT 5;
```

---

### Q6. Best Value Products Based on Price Per Gram

```sql
SELECT DISTINCT name,
weightInGms,
discountedSellingPrice,
ROUND(discountedSellingPrice/weightInGms,2) AS price_per_gram
FROM zepto
WHERE weightInGms >= 100;
```

---

### Q7. Product Weight Classification

```sql
CASE
    WHEN weightInGms < 1000 THEN 'Low'
    WHEN weightInGms < 5000 THEN 'Medium'
    ELSE 'Bulk'
END
```

---

### Q8. Total Inventory Weight by Category

```sql
SELECT category,
SUM(weightInGms * availableQuantity) AS total_weight
FROM zepto
GROUP BY category;
```

---

## 📈 Key Insights

- Identified products with the highest discount percentages.
- Analyzed categories generating the highest estimated revenue.
- Discovered premium products with minimal discounts.
- Measured inventory distribution across categories.
- Evaluated product value using price-per-gram analysis.
- Investigated stock availability trends.

---

## 🚀 Skills Demonstrated

- SQL Query Writing
- Data Cleaning
- Aggregations
- Joins & Filtering
- CASE Statements
- Business Analytics
- Inventory Analysis
- Revenue Analysis
- PostgreSQL Database Management

---

## 👨‍💻 Author

**Aakash Kumar**

B.Tech (2027) | Aspiring Data Analyst

- SQL
- Python
- Power BI
- PostgreSQL
- Data Analytics

Feel free to connect and provide feedback on this project!
