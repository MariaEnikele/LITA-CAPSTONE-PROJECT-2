# LITA-CAPSTONE-PROJECT-2

### Project Title:Customer Segmentation for a Subscription Service
[Project Oveview](#project_overview)
[Data Sources](#data-sources)
[Tools Used](#tools-used)
[Data Cleaning and Preparations](#data-cleaning-and-preparations)
[Exploratory Data Analysis](#exploratory-data-analysis)
[Data Analysis](#data-analysis)
[Data Visualization](#Data-visualization)
### Project Oveview
---
This data is to explore sales data to uncover key insights such as Understanding Customer behaviour, Track subscription types, and Identify Key trends in cancellation and renewals

### Data Sources
---
The primary source of data used is LITA Capstone Dataset and this is a dataset downloaded from the Canvas LMS platform.

### Tools Used
---
- Microsoft Excel [download Here](https://www.microsoft.com).
  1. Data cleaning
  2. Data Analysis
  3. Visualization
- SQL-Structured Query Language for querying of data
- Power BI for data analysis and visualization
- Github for Porfolio Building
  
### Data Cleaning and Preparations
---
In the initial phase of the Data cleaning and preparation, I performed the following action;
1. Data loading and Inspection
2. Handling missing variables
3. Data cleaning and formatting

### Exploratory Data Analysis
---
EDA involved the exploring of the Data to answer some questions such as;
- What is the subscription patterns of customers
- What is the average subscription duration and identify the most popular subscription types
- Identify key trends in renewals and cancellation

### Data Analysis
---
Enclosed are some of the line of codes/queries used in my analysis
```SQL
---------------Retrieve the total number of customers from each region--------
SELECT 
    Region,
    COUNT(DISTINCT CustomerID) AS TotalCustomers
FROM 
    [dbo].[customer data CSV]
GROUP BY 
    Region;
-------------find the most popular subscription type by the number of customers-----------
	SELECT TOP 1
    SubscriptionType,
    COUNT(DISTINCT CustomerID) AS CustomerCount
FROM 
    [dbo].[customer data CSV]
GROUP BY 
    SubscriptionType
ORDER BY 
    CustomerCount DESC;
-----------Find customers who canceled their subscription within 6 months---------
	SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd
FROM [dbo].[customer data CSV]
WHERE Canceled = 'True'
  AND DATEDIFF(month, SubscriptionStart, SubscriptionEnd) <= 6;

 -------------calculate the average subscription duration for all customers------
  SELECT AVG(DATEDIFF(month, SubscriptionStart, SubscriptionEnd)) AS AverageSubscriptionDuration
FROM [dbo].[customer data CSV];

-------------find customers with subscriptions longer than 12 months-------------
SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd
FROM [dbo].[customer data CSV]
WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12;

------------calculate total revenue by subscription type---------------
SELECT SubscriptionType, SUM(CAST(REPLACE(Revenue, ',', '') AS INT)) AS TotalRevenue
FROM [dbo].[customer data CSV]
GROUP BY SubscriptionType;

-------------- find the top 3 regions by subscription cancellations------------
SELECT TOP 3 Region, COUNT(*) AS CancellationCount
FROM [dbo].[customer data CSV]
WHERE Canceled = 'True'
GROUP BY Region
ORDER BY CancellationCount DESC;

-----------------Find the total number of active and canceled subscriptions--------------
SELECT 
    COUNT(CASE WHEN Canceled = 'True' THEN 1 END) AS CanceledSubscriptions,
    COUNT(CASE WHEN Canceled = 'False' THEN 1 END) AS ActiveSubscriptions
FROM [dbo].[customer data CSV];

Excel Formulas used to calculate difference from start date to end date
=F2-E2

```
### Data Visualization
## Subscription Patterns
- In the North and East regions the most popular subscription type is the Basic
- South has majorly the Premium subscription type
- West has the standard subscription type
  ![Count of subscription type](https://github.com/user-attachments/assets/20b771c1-97b7-4392-80d7-97d0adaf714c)
## Average subscription duration and identify the most popular 
- The average subscription accross all types is about 365.35 Days and the most popular is the "Basic"
![average period of subscription](https://github.com/user-attachments/assets/2ac8aa68-54ff-4892-bad0-126cc981b06f)
## Average revenue by subscription type and region
![average revenue by region and subscription type](https://github.com/user-attachments/assets/3ecb3212-af99-485e-a6e8-2e71bd2f7848)
![chart ave  revenue](https://github.com/user-attachments/assets/61534b6e-2e28-40a6-b05b-2e11f1cc44d1)

###SQL
## Total number of customers from each region
![total number of customer in each region proj 2](https://github.com/user-attachments/assets/cadeea92-51df-489f-9a11-1f952d610641)
##  Most popular subscription type by the number of customers
![POPULAR SUBSCRIPTION TYPE BY CUSTOER PROJ2](https://github.com/user-attachments/assets/36e19086-f092-4674-86c3-5d9836541657)
## Find customers who canceled their subscription within 6 months
![CUSTOMERS WHO CANCELLED THEIR SUBSCRIPTION LESS THAN 6MTH](https://github.com/user-attachments/assets/824a3b76-ec47-4222-b5e3-cc0ea354975b)
## Average subscription duration for all customers(months)
![AVERAGE SUBSCRIPTION IN MONTHS](https://github.com/user-attachments/assets/02904a89-0589-4330-b5ce-ad248d04bfc4)
## Customers with subscriptions longer than 12 months
![subscription longer than 12 months proj2](https://github.com/user-attachments/assets/da2dda84-70fb-42d4-9272-a07465bf7441)
## Total revenue by subscription type
![calculate revenue by subscription type](https://github.com/user-attachments/assets/9ae84e65-752c-4a3a-9450-b19a431f5974)
## The top 3 regions by subscription cancellations
![TOP 3 REGION BY SUBSCRIPTION CANCELLATION](https://github.com/user-attachments/assets/eaf5b385-5596-482a-b643-b91efa298266)
## Find the total number of active and canceled subscriptions.
![total number of active and canceled subscriptions  PROJ 2](https://github.com/user-attachments/assets/dde4585c-4ef5-4a9b-9418-0d4891fb78f2)

