# 📊 Online Sales Data Analysis using SQL

## 📝 Project Overview

This project demonstrates how to analyze online sales data using SQL. The analysis includes extracting time-based features, aggregating revenue and order volumes, and applying filters using `WHERE` clauses. All queries are designed to run on a table named `Online_Sales_Data`.

---

## 📂 Dataset Structure

The table `Online_Sales_Data` includes the following fields:

- `Transaction_ID` (INT) – Unique identifier for each transaction  
- `Date` (DATE) – Date of the transaction  
- `ProductCategory` (VARCHAR) – Category of the product  
- `ProductName` (VARCHAR) – Name of the product  
- `UnitsSold` (INT) – Number of units sold  
- `UnitPrice` (DECIMAL) – Price per unit  
- `Total_Revenue` (DECIMAL) – Total revenue per transaction  
- `Region` (VARCHAR) – Region where the sale occurred  
- `PaymentMethod` (VARCHAR) – Mode of payment  

---

## 🧾 SQL Queries Used

### 1. 📆 Extract Month and Year
```sql
SELECT EXTRACT(MONTH FROM Date) AS Month FROM Online_Sales_Data ORDER BY Month;
SELECT EXTRACT(YEAR FROM Date) AS Year FROM Online_Sales_Data ORDER BY Year;
```

### 2. 📅 Group by Year and Month
```sql
SELECT
  EXTRACT(YEAR FROM Date) AS Year,
  EXTRACT(MONTH FROM Date) AS Month
FROM Online_Sales_Data
GROUP BY Year, Month
ORDER BY Year, Month;
```

### 3. 💰 Total Revenue using SUM()
```sql
SELECT
  EXTRACT(YEAR FROM Date) AS Year,
  EXTRACT(MONTH FROM Date) AS Month,
  SUM(Total_Revenue) AS Total_Revenue
FROM Online_Sales_Data
GROUP BY Year, Month
ORDER BY Year, Month;
```

### 4. 📦 Order Volume using COUNT(DISTINCT)
```sql
SELECT
  EXTRACT(YEAR FROM Date) AS Year,
  EXTRACT(MONTH FROM Date) AS Month,
  COUNT(DISTINCT Transaction_ID) AS Order_Volume
FROM Online_Sales_Data
GROUP BY Year, Month
ORDER BY Year, Month;
```

### 5. 📅 Filter Data with WHERE Clause (Quarter 1, 2024)
```sql
SELECT
  YEAR(Date) AS Sales_Year,
  MONTH(Date) AS Sales_Month,
  SUM(Total_Revenue) AS Total_Revenue,
  COUNT(DISTINCT Transaction_ID) AS Order_Volume
FROM
  Online_Sales_Data
WHERE
  Date BETWEEN '2024-01-01' AND '2024-03-31'
GROUP BY
  YEAR(Date), MONTH(Date)
ORDER BY
  Sales_Year, Sales_Month;
```

---

## ✅ Key Learnings

- Used `EXTRACT()` to isolate `MONTH` and `YEAR` from `Date`
- Aggregated data using `SUM()` and `COUNT(DISTINCT ...)`
- Grouped and ordered results using `GROUP BY` and `ORDER BY`
- Filtered data using `WHERE` with `BETWEEN`

---

## 📌 Requirements

- MySQL or any SQL-compliant database system
- A table named `Online_Sales_Data` with appropriate schema



