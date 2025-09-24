# SQL Advanced Data Analytics – Exploratory Data Analysis   

This repository contains a complete **SQL-based Exploratory Data Analysis (EDA)** project developed in **SQL Server**. It demonstrates how SQL alone can be used to explore and analyze data in depth—without relying on external tools.  

The project is organized as a set of individual scripts that focus on specific analytical techniques. Each script can be run on its own or combined for a full EDA workflow.  

---

## 🎯 Project Goal  
The main goal of this project was to learn and showcase how far SQL can go in **data analytics and EDA tasks**. Instead of exporting data to Python or R, all exploration and analysis happens inside SQL Server using carefully designed queries.  

This project is useful for:
- Data analysts looking to deepen SQL skills.  
- Hiring managers or recruiters wanting to see real-world SQL applied to analytics.  
- Teams interested in SQL-first analytics workflows.  

---

## 🗃 Database Overview  

This project uses a simple but realistic database with four core tables:  

| Table Name | Description |
|------------|-------------|
| **Customers** | Stores customer details such as CustomerID, Name, Contact Info, and Location. Useful for segmentation, demographics, and purchase behavior analysis. |
| **Employees** | Holds employee information such as EmployeeID, Name, Department, and Role. Used for linking orders to employees or analyzing team performance. |
| **Orders** | Contains order-level data including OrderID, CustomerID, EmployeeID, ProductID, Quantity, Price, OrderDate, and Status. This is the main fact table for trends, rankings, and cumulative analysis. |
| **Products** | Lists product details such as ProductID, ProductName, Category, and UnitPrice. Useful for product-level performance, part-to-whole analysis, and ranking. |

All analyses in the project are performed using these four tables. You can adapt the queries to any similar schema by changing the table and column names.  

---

## 📂 Project Structure  

The project follows a logical EDA flow. Each SQL file corresponds to a specific analysis area:

| Script No. | Topic/Focus Area | Description |
|------------|-----------------|-------------|
| 01 | **Database Exploration** | Basic database information, table structures, and column profiling. |
| 02 | **Dimensions Exploration** | Explore categorical and dimensional data fields (Customers, Products, Employees). |
| 03 | **Date Exploration** | Work with dates in Orders: distributions, gaps, trends over time. |
| 04 | **Measures Exploration** | Explore numeric measures such as quantity, price, and revenue. |
| 05 | **Big Numbers / Magnitudes** | Identify large values, totals, and aggregations in sales and orders. |
| 06 | **Ranking (Top N / Bottom N)** | Rank customers, employees, or products based on sales or orders. |
| 07 | **Change-Over-Time Trends** | Track changes in key metrics over time using Orders. |
| 08 | **Cumulative Analysis** | Running totals of sales, cumulative orders, progressive metrics. |
| 09 | **Performance Analysis** | Compare employee, product, or customer performance. |
| 10 | **Part-to-Whole Proportional Analysis** | Ratios, percentages, and contribution analysis (e.g., each product’s share of total sales). |
| 11 | **Data Segmentation** | Group customers or orders into meaningful segments (by region, category, etc.). |
| 12 | **Reporting Views** | Combine outputs into reporting-friendly views or tables. |

---

## 🛠 How to Use  

1. **Set up the database**  
   - Create the four tables (`Customers`, `Employees`, `Orders`, `Products`).  
   - Insert your data into each table.  
   - Update connection details in SQL Server Management Studio (SSMS).  

2. **Run the scripts**  
   - Scripts are numbered from 01 to 12.  
   - Open each `.sql` file in SSMS and run it against your database.  
   - Check the output results directly in the Results pane.  

3. **Adapt to your data**  
   - Replace table names, column names, or database references to fit your dataset.  
   - You can use the same logic on any SQL Server database.  

---

## 📝 Example Query  

Here’s an example of one of the ranking techniques used in the project:

```sql
SELECT 
    CustomerID,
    SUM(Quantity * UnitPrice) AS TotalSales,
    RANK() OVER (ORDER BY SUM(Quantity * UnitPrice) DESC) AS SalesRank
FROM Orders o
JOIN Customers c ON o.CustomerID = c.CustomerID
GROUP BY CustomerID;


This gives a quick view of top customers by sales.

🗂 Folder Contents
SQL_Advanced_Data_Analytics/
│
├── 01_Database_Exploration.sql
├── 02_Dimensions_Exploration.sql
├── 03_Date_Exploration.sql
├── 04_Measures_Exploration.sql
├── 05_Big_Numbers.sql
├── 06_Ranking_Top_Bottom.sql
├── 07_Change_Over_Time_Trends.sql
├── 08_Cumulative_Analysis.sql
├── 09_Performance_Analysis.sql
├── 10_Part_to_Whole_Proportion.sql
├── 11_Data_Segmentation.sql
└── 12_Reporting.sql


Each file contains comments explaining the logic of the queries.

Source Credit - Data with Baraa YT channel.


