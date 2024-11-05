# SALES REPORT
 An analysis was done on this sales report of a retail store to find out its sales performance.  Key insights such as top-selling products, regional  performance, and monthly sales trends is shown with Microsoft 
 Excel and SQL  . An interactive Power BI  dashboard is also represented here that highlights these findings.

### PROJECT TITLE: SALES PERFORMANCE ANALYSIS


### PROJECT OVERVIEW
This Data Analysis project aims to analyzing the sales performance of a retail store over two years.
By exploring the sales data, I was able  to uncover key insights such as top-selling products, regional 
performance, and monthly sales trends, to enable us tell compelling stories about the data and help the business make informed decisions.
An interactive Power BI dashboard that highlights these findings is also represented here.


### DATA SOURCES
The primary source of Data used here is an Excel file,which i had to convert to a csv file for me to be able to import into SQL. The file
was provided by INCUBATOR HUB.

### TOOLS USED
- Microsoft Excel [Download Here](https://www.microsoft.com)
  1. For Data cleaning 
  2. For Analysis
  3. For Visualiation
- SQL - Structured Query Language [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
  1. For Querying of Data
- Power BI [Download Here](https://www.microsoft.com/en-us/download/details.aspx?id=58494)
  1. For Data Visualiation
 

 ### DATA CLEANING AND PREPARATION  
 In the initial phase of the Data Cleaning and preparations,I performed the following action;
 1. Data loading and inspection
 2. Conversion of dataset to tables
 3. Removal of duplicates 
 4. Data cleaning and formatting

 ### EXPLORATORY DATA ANALYSIS
 EDA involved the exploring of the Data to answer some questions about the Data such as;
  - What are the top-selling products
  - What is the regional performance
  - What is the monthly sales trends

### DATA ANALYSIS
This is where I include some basic functions used in Excel, basic lines of code and queries used in SQL and some 
of the DAX epressions used in POWER BI during my analysis.
1. Excel
   1. Revenue
   ```Excel
   =[@UnitPrice]*[@Quantity]
   ```
3. SQL;
   1. TOTAL SALES FOR PRODUCT CATEGORY
 ```SQL
   SELECT PRODUCT, SUM(Revenue) AS TOTALSALES
   FROM [dbo].[LITA Capstone Dataset]
   GROUP BY PRODUCT ORDER BY 2 DESC
 ```
   2. TOTAL REVENUE PER PRODUCT
 ```SQL
    SELECT PRODUCT,SUM(QUANTITY*UNITPRICE)
    AS REVENUE FROM[dbo].[LITA Capstone Dataset]
    GROUP BY PRODUCT
 ```
  3. TOP 5 BY PURCHASE AMOUNT
```SQL
  SELECT TOP 5 CUSTOMER_ID,
  SUM(REVENUE) AS TOTALPURCHASE
  FROM [dbo].[LITA Capstone Dataset]
  GROUP BY CUSTOMER_ID
  ORDER BY TOTALPURCHASE DESC
```
  4. PRODUCTS WITH NO SALE
```SQL
  SELECT PRODUCT FROM[dbo].[LITA Capstone Dataset]
  GROUP BY PRODUCT 
  HAVING MAX(OrderDate)<
  DATEADD(QUARTER,-1,GETDATE())
```
  5. PERCENTAGE OF TOTAL SALES FOR  EACH REGION
```SQL
  SELECT REGION,COUNT (*) AS REGION_SALES,
  (COUNT(*)*100.0/(SELECT COUNT(*)
  FROM[dbo].[LITA Capstone Dataset])) AS
  SALES_PERCENTAGE FROM [dbo].[LITA Capstone Dataset]
  GROUP BY REGION
```
   6. Number of sales transaction in each region 
 ```SQL
  SELECT REGION,COUNT(ORDERID) AS NUMBEROFTRANSACTIONS
  FROM[dbo].[LITA Capstone Dataset]
  GROUP BY REGION
```
  7. Highest selling product by sales value
```SQL
  SELECT TOP 1 PRODUCT, SUM(REVENUE) AS TOTALSALES
  FROM [dbo].[LITA Capstone Dataset]
  GROUP BY Product
  ORDER BY TOTALSALES DESC
```
  8. Monthly sales total for the current year
```SQL
  SELECT MONTH (ORDERDATE) AS MONTH,
  SUM (REVENUE) AS MONTHLYSALES
  FROM[dbo].[LITA Capstone Dataset]
  WHERE YEAR (OrderDate) = YEAR(GETDATE())
  GROUP BY MONTH (ORDERDATE)
```





 
