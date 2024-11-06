# LITA_PROJECT
### Project Title
#### Sales Performance Analysis of a Retail Store
### Introduction
This is an analysis of sales performance of a retail store. It is done by analyzing data from a dataset which includes: SalesData and CustomerData. This exploration will aid in understanding market dynamics and potentially inform business decisions.
### Problem Statement 
The goal of the analysis is to :
1. Determine the top selling products and how it varies by region
2. To discover target markets or goods that have the greatest impact on sales success
3. Identify the areas where sales performance is lacking or could be improved
4. Finally, the goal is to create data driven plans that can aid in increasing sales, improving customer happiness and driving corporate growth
### Tools used
1. Mcrosoft Excel; For Data cleaning, Preparation and Analysis
2. SQL (Structured Query Language); Data Preparation and Analysis
3. Power BI; For Data Visualization
 ### Data Analysis
 MICROSOFT EXCEL; In the SalesData dataset, there are 7 columns (OrderId, CustomerID, Product, Region, OrderDate, Quantity, Unit Price). 
 - To get the total sales, I created a new column (SALES) where Quantity column and Unit Price column were multiplied together.
 ```=F2*G2```
 - Then I went ahead to the pivot section to summarize the data into;
 Total Sales by Product, Total Sales by Region, Total Sales by Month, Average Sales per product.
 ![Pivot Reporting](https://github.com/user-attachments/assets/dd5aab33-a970-4a5e-bf02-cb01e5c4bc7c)
  In the CustomerData dataset, there are 8 columns (CustomerID, CustomerName, Region, SubscriptionType, SubscriptionStart, SubscriptionEnd, Canceled, Revenue).
  - Pivot Section ; Total Revenue by Region, Total Revenue by SubscriptionType, SubsciptionType by Count of CustomerID.
  ![pivot reporting 2](https://github.com/user-attachments/assets/b28346b0-91f4-40f5-8c6e-6591622d4334)
 SQL; I created a database LITA_PROJECT ```create database LITA_PROJECT```
Then the dataset was imported from Excel after which several structured queries were written to retrieve the right columns needed to find;
- Total sales for each product category, Number of Sales transactions in each region, Highest selling product by total sales value. 
  ```SQL
  SELECT Top (1) Product, SUM([ Sales]) AS TotalSales FROM SalesData GROUP BY Product ORDER BY TotalSales DESC
```
```SQL
SELECT Region, COUNT(OrderID) AS NumOfTransactions
FROM SalesData
GROUP BY Region
```
- To calculate total revenue by product, monthly sales totals for the current year, Top 5 customers by total purchase amount, percentage of total sales contributed by each region, products with no sales in the last quater,
  ```SQL
  SELECT Product, SUM([ Sales]) AS TotalRevenue FROM SalesData GROUP BY Product
```

```SQL
SELECT Month(OrderDate) AS Month,
    SUM([ Sales]) AS MonthlySalesTotal
FROM SalesData WHERE YEAR(OrderDate) = 2024
GROUP BY Month(OrderDate)
ORDER BY Month
```

```SQL
SELECT Top (5) [Customer Id],
 SUM([ Sales]) AS TotalPurchaseAmount FROM SalesData
GROUP BY [Customer Id]
ORDER BY TotalPurchaseAmount DESC
```

```SQL
SELECT Region, SUM([ Sales]) AS RegionTotalSales,
FORMAT(ROUND((SUM([ Sales]) / CAST((SELECT SUM([ Sales]) FROM salesdata) AS DECIMAL(10,2)) * 100), 1), '0.#') 
AS PercentageOfTotalSales
FROM salesdata
GROUP BY Region
ORDER BY PercentageOfTotalSales DESC
```

```SQL
SELECT Product FROM salesdata
GROUP BY Product
HAVING SUM(CASE 
WHEN OrderDate BETWEEN '2024-06-01' AND '2024-08-31' 
THEN 1 ELSE 0 END) = 0
```
### Data Visualization
POWER BI
- I imported data from Excel Workbook
- After importing, I transformed the data and checked for column quality, column profile and column distribution.
- I closed and applied then changed to Report view for Visualization
- SALES OVERVIEW OF SalesData AND CustomerData
  - TOP SELLING PRODUCTS IN SALESDATA
  ![power BI visualization](https://github.com/user-attachments/assets/a147ab72-3536-4f0d-b991-4f2e96ef6ef6)
  - RESULT INTERPRETATION; From the visualization above, the top selling product is Shoes with the total sales of 3.09 million which accounts for (29.16% of the total revenue). Followed by shirt which has the total sales of 2.45 million (23.14% of the total revenue)
- TOP SELLING SERVICE IN CUSTOMERDATA
   ![power BI visualization 5](https://github.com/user-attachments/assets/6eb89297-e695-4948-81ca-24e3eaccef90)
  -  RESULT INTERPRETATION; From the visualization above, the top selling product is Basic subscriptiontype with the total sales of 75 million which accounts for (49.9% of the total revenue). Followed by premium subscriptiontype which has the total sales of 38 million (25.08% of the total revenue)
 
- REGIONAL PERFORMANCE
    ![power BI visualization 3](https://github.com/user-attachments/assets/6ed6f1d4-b20e-4c41-8bea-6f25f601ef68)
    - RESULT INTERPRETATION; From the visualization above, South region has the highest sales(4.7millon) in the four regions followed by East region (2.5million) of the total revenue.
  -  MONTHLY SALES TREND

![power BI visualization 4](https://github.com/user-attachments/assets/de347b53-cf8e-4b99-9ff5-9200a5b99926)

![power BI visualization 6](https://github.com/user-attachments/assets/6045a964-62f7-45f1-a2d6-7fd7eb7dbdcd)

 RESULT INTERPRETATION; From the visualization above,the month of February had the highest sales recorded (2.75 million) followed by July (1.38 million)

 ### Recommendation
