# Lita_Capstone_Project
DOCUMENTAION FOR MY CAPSTONE PROJECT WITH LITA DATA ANALYSIS CLASS

### Project title: Salesdata analysis 

### Project Overview 
---
This project aims to analyze sales data to extract valuable insights, identify trends, and optimize business decisions. The project utilizes Excel, SQL and Power BI data visualization techniques to provide a comprehensive understanding of sales performance such as total sales, average sales according to region, products, and month.

### Data Source
---
The data source is a Salesdata obtained from the Lita data class instructors/facilitator.

### Tools Used
---
- Microsoft Excel for Data Cleaning, Analysis and visualization.
- SQL (Structured Query Language) for Querying of Data
- Power Business Intelligence (Power BI) for Data cleaning, Analysis and Creation of Visuals
- GitHub for portfolio building

### Data cleaning and preparation
---
The initial phase of this project cleaning, the following actions were taken
1. Data loading and inspection on each tool.
2. Removal of Duplicates, Handling missing variables, and changing Data types.
3. Data Transformation, Cleaning and Formatting.

### Exploring Data Analysis 
---
In EDA, the Data was explored to answer to answer some questions such as 
1. Using Excel to:
- summarizing total sales by product, region, and month using pivot tables.
- Use Excel formulas to calculate metrics such as average sales per product and total revenue by region.
- Creating other interesting report using pivot tables and charts.
2. Writing SQL Queries to:
- retrieve the total sales for each product category.
- find the number of sales transactions in each region.
- find the highest-selling product by total sales value.
- calculate total revenue per product.
- calculate monthly sales totals for the current year.
- find the top 5 customers by total purchase amount.
- calculate the percentage of total sales contributed by each region.
- identify products with no sales in the last quarter.
3. Creating a dashboard that visualizes the insights found in Excel and SQL, which a sales overview, top-performing products, and regional breakdowns.
  
### Data Analysis 
---
This is where excel functions, SQL queries and as well as lines of Codes used during the salesdata analysis are displayed.

```EXCEL
=AVERAGEIF(SalesData!C:C,SalesData!C2,SalesData!H:H)

=SUMIF(SalesData!D:D,SalesData!D3,SalesData!H:H)
```
```SQL
SELECT * FROM [dbo].[Capstone project lita]

TOTAL SALES 

SELECT SUM(SALES) AS TOTALSALES
FROM [dbo].[Capstone project lita];

Total sales for each product

SELECT PRODUCT, SUM(SALES) AS totalsales
from [dbo].[Capstone project lita]
group by Product;

Number of sales transaction in each region

SELECT region, count(SALES) AS salestransaction
from [dbo].[Capstone project lita]
group by region;

Highest selling product by total sales value

select top 1 product, sum(sales) as totalsales
from [dbo].[Capstone project lita]
group by Product;

Total revenue per product

select product, sum(sales) as totalrevenue
from [dbo].[Capstone project lita]
group by Product;

Monthly sales total for the current year

select DATENAME(MONTH,OrderDate) as month,
sum(sales) as monthlysales
from [dbo].[Capstone project lita]
where year(orderdate) = year(getdate())
group by DATENAME(MONTH,orderdate);

Top 5 customers by total purchase amount

select top 5 Customer_Id,
SUM(sales) AS TOTALPURCHASE
FROM[dbo].[Capstone project lita]
group by Customer_Id
ORDER BY TOTALPURCHASE DESC;

Percentage of total sales contributed by each region

Select region,
SUM(sales)/(select sum(sales) FROM[dbo].[Capstone project lita])* 100 as SALESPERCENTAGE
FROM [dbo].[Capstone project lita]
GROUP BY Region;

Product with no sales in the last quarter

select PRODUCT
from[dbo].[Capstone project lita]
where Product not in (
select product from [dbo].[Capstone project lita]
where OrderDate >= DATEADD(q,-1, GETDATE())
);
```
![1748852122668871515223071254349](https://github.com/user-attachments/assets/cc50ee44-8b8b-49f2-ae88-69dcd7fb1428)

![1748852286041175972358853900739](https://github.com/user-attachments/assets/d5c36cc0-99fa-4e25-adaa-5376ded58b14)

