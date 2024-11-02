# Lita-Capstone-Project-2-


## Table of Contents
___
1. [Project Overview](#project-overview)
2. [Tools Used](#tools-used)
3. [Data Exploration](#data-exploration)
4. [Excel Analysis](#excel-analysis)
5. [SQL Queries](#sql-queries)
6. [PowerBI Dashboard](#powerbi-dashboard)
7. [Appendices](#appendices)


### PROJECT 2  - Customer Segmentation for AME Subscription Service 

#### Project Overview
___
This project shows the analysis of customer segmentation for AME subscription service. This analysis was carried out by exploring the customer data for a subscription service to identify key trends in cancellation and renewals. The goal of the project is to understand customer behaviour, track subscription types and identity key trends in cancellation and renewals. 

#### Tools Used
___
This project employs a combination of data exploration, SQL querying, and data visualization techniques using:

- Microsoft Excel for data exploration and calculation
- SQL Server for data querying and analysis
- Power BI for interactive dashboard creation


#### Data Exploration
___
* Excel Analysis
-Analysis on customer data using pivot tables to find subscription patterns

-Average subscription duration and identification of the most popular 
subscription types


-Subscription type distribution by region


-Cancellation rates by subscription type



#### SQL Queries 2
- Total number of customers from each region
QUERY:
```
SELECT Region, COUNT(CustomerID) AS Total_No_of_Customers
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
GROUP BY Region
```

- Most popular subscription type by the number of customers
QUERY:
```
SELECT SubscriptionType, COUNT(CustomerID) AS No_of_Customer
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
GROUP BY SubscriptionType
```

- Customers who canceled their subscription within 6 months
QUERY:
```
SELECT CustomerName, Canceled, SubscriptionStart 
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
WHERE Canceled = 0 AND
MONTH(SubscriptionStart)
BETWEEN 1 AND 6
```

- Average subscription duration for all customers
QUERY:
```
SELECT Count(CustomerID) AS All_Customers, AVG(DATEDIFF(DAY,SubscriptionStart,SubscriptionEnd)) 
AS Average_Subscription_Duration 
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
WHERE SubscriptionEnd IS NOT NULL
```

- Customers with subscriptions longer than 12 months
QUERY:
```
SELECT CustomerName,SubscriptionType,SubscriptionStart,SubscriptionEnd 
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
WHERE DATEDIFF(MONTH, SubscriptionStart,SubscriptionEnd)>=12
```

- Total revenue by subscription type
QUERY:
```
SELECT SubscriptionType, SUM(Revenue) AS Total_Revenue
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
GROUP BY SubscriptionType
```

- Top 3 regions by subscription cancellations
QUERY:
```
SELECT TOP 3 Region, Canceled 
FROM [dbo].[LITACAPSTONE CUSTOMER DATA]
```

- Total number of active and canceled subscriptions
QUERY:
```
SELECT SUM(CASE WHEN Canceled=0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
SUM(CASE WHEN Canceled=1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM [dbo].[LITACAPSTONE CUSTOMER DATA] 
GROUP BY CustomerID
```


#### PowerBI Dashboard 2
___
- Create visualizations for:
    - Customer segmentation by region and subscription type
    [Insert screenshot here]

    - Cancellation rates by subscription type and region
    [Insert screenshot here]

    - Average subscription duration by subscription type
    [Insert screenshot here]

    - Total revenue by subscription type
    [Insert screenshot here]

    - Active and canceled subscription counts
    [Insert screenshot here]


*Interactive Analysis*
- Add slicers for region, subscription type, and date range.
- Enable drill-down capabilities for detailed analysis.

Final Deliverable
- A comprehensive Power BI dashboard showcasing customer segments, cancellations, and subscription trends.
- Accompanied by a report detailing findings and insights from Excel and SQL analyses.


#### Appendices
___
* Capstone Sales Dataset






























