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
  ```SELECT Top (1) Product, SUM([ Sales]) AS TotalSales
FROM SalesData
GROUP BY Product
ORDER BY TotalSales DESC
```


