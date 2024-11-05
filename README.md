# TITLE: LITA_DATA-PROJECT
# project Overview


This data analysis project aims to provide insights into sales and subscription performance from 2023 to 2024. By examining different aspects of sales data and customers, we aim to identify trends, offer data-driven recommendations, and better understand the company's performance.
### DATA SOurces
An Excel dataset *LITA Capstone _Datase_ cvs* consisting of sales and customer data was provided 
### Data Analysis Tools
_ SQL (Structured Query Language) for manipulating rational data
_ PowerBI for Creating reports and Visualization
_ Microsoft Excel for  Data cleaning, visualization, and data analysis [download here](https://microsoft.com)
### Data Cleaning
 Excel was used to clean data by performing the following functions
    _Data loading and inspection
    _Removing duplicates
     _Removing black data
   ### Data Analysis SQL Project 1 FOR SALES DATA
   
    Helped to answer some of the following questions;
     i retrieve the total sales for each product category
     
     ii find the number of sales transactions in each region
     
     iii  find the top 3 regions by subscription cancellations 
     
    iv   find the highest-selling product by total sales value. 
    
     v   calculate total revenue per product. 
     
    vi   calculate monthly sales totals for the current year. 
    
   vii   find the top 5 customers by total purchase amount. 
   
viii  calculate the percentage of total sales contributed by each region. 

ix  identify products with no sales in the last quarter. 
  
  ```SQL 
      SELECT Product, SUM(Revenue) AS TOTAL SALES
 from [dbo].[ALINAFE LITA]
 Group by Product
```


```SQL
 SELECT REGION, COUNT(Quantity) AS NUMBER_OF_TRANSACTION
 FROM [dbo].[ALINAFE LITA]
 GROUP BY REGION
```
```SQL
Select Top 3 region, count(canceled) as subscription_cancellations
from [dbo].[REAL Customer _Data Capstone]
Group by Region
Order by subscription_cancellations DESC

```SQL
  SELECT Top 1 product, SUM(Revenue) AS HIGHEST_SELLING_PRODUCT
FROM [dbo].[ALINAFE LITA]
GROUP BY product
ORDER BY HIGHEST_SELLING_PRODUCT DESC
```

```SQL
SELECT PRODUCT, SUM(Revenue) AS TOTAL_REVENUE
FROM [dbo].[ALINAFE LITA]
Group by Product
```

```SQL
select OrderDate, Sum(Revenue) AS Monthly sales
From [dbo].[ALINAFE LITA]
WHERE OrderDate between '2024-01-01' AND '2024-12-31'
Group by OrderDate
Order by OrderDate
```
``SQL
SELECT Top 5 customer_id, SUM(Revenue) AS total_purchase
FROM [dbo].[ALINAFE LITA]
GROUP BY customer_id
ORDER BY total_purchase DESC
```
```SQL
SELECT 
    Region, 
    SUM(Revenue) AS region_total_sales, 
    (SUM(Revenue) * 100.0 / (SELECT SUM(Revenue) FROM[dbo].[ALINAFE LITA] )) AS percentage_of_total_sales 
FROM 
   [dbo].[ALINAFE LITA] 
GROUP BY region,
```

```SQL
SELECT 
    product 
FROM 
    [dbo].[ALINAFE LITA]
WHERE 
    OrderDate < DATEADD(QUARTER, -1, GETDATE()) 
GROUP BY 
    product 
HAVING 
    SUM(Revenue) = 0
```

```SQL
 SELECT 
    FORMAT(OrderDate, 'yyyy-MM') AS month, 
    SUM(Revenue) AS monthly_Total_sales
FROM 
    [dbo].[ALINAFE LITA]
WHERE 
    YEAR(OrderDate) = YEAR(GETDATE()) 
GROUP BY 
    FORMAT(OrderDate, 'yyyy-MM');

	Alter table [dbo].[ALINAFE LITA]
	drop column total_sales

	select * from [dbo].[ALINAFE LITA]
```

### Excel data analysis for sales data
The following questions were asked;
I Perform an initial exploration of the sales data. Use pivot tables to summarize total sales by product, region, and month 

 ii Use Excel formulas to calculate metrics such as average sales per product and total revenue by region
 
iii Create any other interesting report 

<img width="928" alt="image" src="https://github.com/user-attachments/assets/6d3189cf-1c2c-46f1-9daf-dc3ba1d1da86">
<img width="219" alt="image" src="https://github.com/user-attachments/assets/d2f0f332-9e04-4414-a45a-d5dc7d4015ce">
<img width="505" alt="image" src="https://github.com/user-attachments/assets/b273767c-ae33-4742-9fb5-d3c514ae4b64">
<img width="230" alt="image" src="https://github.com/user-attachments/assets/bb1e58a0-b24f-4575-bffd-900e706e2113">
![image](https://github.com/user-attachments/assets/d1eaad0c-0cdf-4a68-84dc-213115b1a5de)
![image](https://github.com/user-attachments/assets/350b7ad2-16ef-4148-8fca-70990e312458)

### Power BI Visualization for sales data
<img width="613" alt="image" src="https://github.com/user-attachments/assets/b72ab591-8ff7-4fa6-8efb-aced9834afbf">
<img width="608" alt="image" src="https://github.com/user-attachments/assets/097374ee-df21-4b9d-affa-3af27a424277">
<img width="608" alt="image" src="https://github.com/user-attachments/assets/00bcb857-5933-4e06-aa2b-5cefa6be284b">


### Exercise 2 For Customer data; 
#### SQL DATA ANALYSIS
I retrieve the total number of customers from each region

``` SQL
ii SELECT Region, SUM(CustomerID) AS TOTAL_CUSTOMER
 from [dbo].[REAL Customer _Data Capstone]
 Group by Region
```

iii find the most popular subscription type by the number of customers

```SQL
Select Top 1 SubscriptionType,
    COUNT(CustomerID) as CustomerCount
FROM [dbo].[REAL Customer _Data Capstone]
GROUP BY subscription type
ORDER BY CustomerCount DESC;
```

iv Find customers who canceled their subscription within 6 months

```SQL
SELECT CustomerID
FROM[dbo].[REAL Customer _Data Capstone]
WHERE canceled = '1' 
AND subscription_Duration <= 6
Group by CustomerID
```

v Calculate the average subscription duration for all customers

 ```SQL
 SELECT AVG(Subscription_Duration) AS Average_Duration
FROM [dbo].[REAL Customer _Data Capstone]
```

vi Find customers with subscriptions longer than 12 months

```SQL
Select CustomerID
FROM [dbo].[REAL Customer _Data Capstone]
WHERE Subscription_Duration > 12
```

vi calculate total revenue by subscription type

```SQL
Select SubscriptionType, sum(Revenue)as Total_Revenue
from [dbo].[REAL Customer _Data Capstone]
group by subscription type
```

vii Find the top 3 regions by subscription cancellations

```SQL 
Select Top 3 region, count(canceled) as subscription_cancellations
from [dbo].[REAL Customer _Data Capstone]
Group by Region
Order by subscription_cancellations DESC
```

Viii Find the total number of active and canceled subscriptions

```SQL
select customerID,count(canceled) AS ACTIVE_CANCELLATIONS
 from [dbo].[REAL Customer _Data Capstone]
 Where Canceled = '1'
 group by CustomerID
```

```SQL
 select customerID,count(canceled) AS NON_ACTIVE_CANCELLATIONS
 from [dbo].[REAL Customer _Data Capstone]
 Where Canceled = '0'
 group by CustomerID
```

### Data visualization Excel fro Custo
![image](https://github.com/user-attachments/assets/f9b229b0-54d2-4fab-a2f5-65477a8f4eae)
<img width="368" alt="image" src="https://github.com/user-attachments/assets/b1cee71a-a277-4f3d-b39d-c5f792965a5e">
<img width="392" alt="image" src="https://github.com/user-attachments/assets/217a5ad5-5508-49f2-b2a6-f91d10ae0a3a">

### Power BI visualization

<img width="579" alt="image" src="https://github.com/user-attachments/assets/78cbf726-b270-46bc-8c91-0a9230f521dc">

### LImitations
 I could not remove the black columns in Excel. Fortunately, it has not affected anything or any value, but it is showing in the pivot table of Excel

 ### Recommendation
 The company should increase the total sales of products like socks and jackets to generate more revenue
 For customer data, even though the number of customers who canceled their subscriptions did not exceed those who canceled, the number was quite high, the company should find strategies to ensure that many customers do not cancel their subscriptions to increase the revenue


