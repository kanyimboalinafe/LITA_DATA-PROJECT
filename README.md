# TITLE: LITA_DATA-PROJECT
# project Overview
This data analysis project aims to provide insights into the sales and subscription performance starting from 2023-2024. By examining different aspects of sales data and customers, we aim to identify trends, offer data-driven recommendations, and achieve a deeper understanding of the company's performance.
### DATA SOurces
An Excel dataset *LITA Capstone _Datase_ cvs* consisting of sales and customer data was provided 
### Data Analysis Tools
_ SQL (Structured Query Language) for manipulating rational data
_ PowerBI for Creating reports and Visualization
_ Microsoft Excel for  Data cleaning, visualization, and data analysis [download_here] (https://microsoft.com)
### Data Cleaning
 Excel was used to clean data by performing the following functions
    _Data loading and inspection
    _Removing duplicates
     _Removing black data
   ### Data Analysis SQL
     Helped to answer some of the following questions;
     i retrieve the total sales for each product category
     ii find the number of sales transactions in each region
     iii  find the top 3 regions by subscription cancellations 
  
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
```
### Data visualization Excel
The following charts were created to show the sales performance
![image](https://github.com/user-attachments/assets/d1eaad0c-0cdf-4a68-84dc-213115b1a5de)
![image](https://github.com/user-attachments/assets/350b7ad2-16ef-4148-8fca-70990e312458)
<img width="340" alt="image" src="https://github.com/user-attachments/assets/aa44f370-5a79-40d6-bfbc-7f149c3900f4">


### Power BI visualization

<img width="579" alt="image" src="https://github.com/user-attachments/assets/78cbf726-b270-46bc-8c91-0a9230f521dc">



