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
SELECT Region, COUNT(CustomerID) AS Total_Customers
FROM subscriptions
GROUP BY Region;
SELECT SubscriptionType, COUNT(CustomerID) AS Total_Customers
FROM subscriptions
GROUP BY SubscriptionType
ORDER BY Total_Customers DESC
LIMIT 1;

SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd, Canceled
FROM subscriptions
WHERE Canceled = TRUE
AND DATEDIFF(SubscriptionEnd, SubscriptionStart) <= 180;

SELECT AVG(DATEDIFF(SubscriptionEnd, SubscriptionStart)) AS Average_Subscription_Duration
FROM subscriptions;

SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd
FROM subscriptions
WHERE DATEDIFF(SubscriptionEnd, SubscriptionStart) > 365;




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



