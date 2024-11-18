# SQL-PROJECT - Super store
# Superstore SQL Project

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset Information](#dataset-information)
- [Objectives](#objectives)
- [SQL Queries and Analysis](#sql-queries-and-analysis)
  - [1. Total Sales by Region](#1-total-sales-by-region)
  - [2. Top 5 Cities by Sales](#2-top-5-cities-by-sales)
  - [3. Average Discount by Category](#3-average-discount-by-category)
  - [4. State with the Highest Profit](#4-state-with-the-highest-profit)
  - [5. States with Sales Above Average](#5-states-with-sales-above-average)
  - [6. Cities with Profit Above Average](#6-cities-with-profit-above-average)
  - [7. Min and Max Sales by Segment](#7-min-and-max-sales-by-segment)
  - [8. State with Maximum Sales](#8-state-with-maximum-sales)
  - [9. Top City for Office Supplies](#9-top-city-for-office-supplies)
  - [10. Total Sales by City from Joined Tables](#10-total-sales-by-city-from-joined-tables)
  - [11. States and Regions from Joined Tables](#11-states-and-regions-from-joined-tables)

## Project Overview
This project focuses on analyzing a **Superstore** dataset using **SQL** to derive business insights for a B2C (Business-to-Consumer) context. The primary goal is to explore various metrics like sales, profit, discounts, and more across different dimensions such as regions, cities, categories, and segments.

## Dataset Information
- The data used in this project is from the **Sample Superstore** dataset, which includes details about customer purchases, sales, discounts, and profits.
- The analysis leverages **MySQL** for data extraction and manipulation, showcasing the power of SQL for business analytics.

## Objectives
- To provide actionable insights into sales performance.
- To identify top-performing regions, cities, and product categories.
- To assist in making data-driven decisions for improving customer engagement and profitability.

## SQL Queries and Analysis

### 1. Total Sales by Region
sql
SELECT Region, SUM(Sales) AS Total_Sales
FROM SampleSuperstore
GROUP BY Region;
## 2. Top 5 Cities by Sales
sql
SELECT City, SUM(Sales) AS Total_Sales
FROM SampleSuperstore
GROUP BY City
ORDER BY Total_Sales DESC
LIMIT 5;
## 3. Average Discount by Category
sql
Copy code
SELECT Category, AVG(Discount) AS Average_Discount
FROM SampleSuperstore
GROUP BY Category;
## 4. State with the Highest Profit
sql
Copy code
SELECT State, SUM(Profit) AS Total_Profit
FROM SampleSuperstore
GROUP BY State
ORDER BY Total_Profit DESC
LIMIT 1;
## 5. States with Sales Above Average
sql
Copy code
SELECT State, SUM(Sales) AS Total_Sales
FROM SampleSuperstore
GROUP BY State
HAVING Total_Sales > (SELECT AVG(Sales) FROM SampleSuperstore)
LIMIT 10;
## 6. Cities with Profit Above Average
sql
Copy code
SELECT City, SUM(Profit) AS Total_Profit
FROM SampleSuperstore
GROUP BY City
HAVING Total_Profit > (SELECT AVG(Profit) FROM SampleSuperstore)
LIMIT 10;
## 7. Min and Max Sales by Segment
sql
Copy code
SELECT Segment, MIN(Sales) AS Min_Sales, MAX(Sales) AS Max_Sales
FROM SampleSuperstore
GROUP BY Segment;
## 8. State with Maximum Sales
sql
Copy code
SELECT State
FROM SampleSuperstore
WHERE Sales = (SELECT MAX(Sales) FROM SampleSuperstore);
## 9. Top City for Office Supplies
sql
Copy code
SELECT City, SUM(Sales) AS Total_Sales
FROM SampleSuperstore
WHERE Category = 'Office Supplies'
GROUP BY City
ORDER BY Total_Sales DESC
LIMIT 1;
## 10. Total Sales by City from Joined Tables
sql
Copy code
SELECT country.city, SUM(storesales.Sales) AS Total_Sales
FROM storesales
JOIN country ON storesales.postal_code = country.postal_code
GROUP BY country.city
LIMIT 10;
## 11. States and Regions from Joined Tables
sql
Copy code
SELECT storesales.region, country.state AS states
FROM storesales
JOIN Country ON storesales.postal_code = Country.postal_code
ORDER BY storesales.region ASC
LIMIT 10;
