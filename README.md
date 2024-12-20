# LITA-CAPSTONE-PROJECT

[PROJECT OVERVIEW](PROJECT-OVERVIEW)

[Top Selling Products](Top-Selling-Products)

[DATA DESCRIPTION](DATA-DESCRIPTION)

[DASHBOARD REVIEW](DASHBOARD-REVIEW)

[METHODOLOGY](METHODOLOGY)

[DATA ANALYSIS](DATA-ANALYSIS)

[Data Summary](Data-Summary)

[Key Insights](Key-Insights)

[Recommendations](Recommendations)

[Conclusions](Conclusions)




## PROJECT OVERVIEW:
---
This report presents an analysis of total sales/revenue across various products, summarizing the performance and identifying the highest-earning product.

### Top Selling Products
---
Regional Performances
Monthly Sales Trend
PowerBI for visualization and storytelling

### DATA DESCRIPTION
---
This dataset includes the following Columns:

Order Number

Customer Id

products

region

Order Date

Quantity

Unit Price

### DASHBOARD REVIEW
---
Customer Id
products: Items sold in the store
region: The other regional branches of the store ( North, South, East West)
Order Date: Date order was placed
Quantity: The number of units of the product ordered in each transaction
Unit Price: The cost per unit of the product acquired

STATISTICS ABOUT THE DATASET:
Number of Unique Customers: 9921
Number of Products: 6 
Total Sales:  2,101,090.00 
 Total Region: 4

### METHODOLOGY
---
Data Collection
The dataset for this analysis was provided by LITA_ The Incubator Hub for leaening and training purposes. The data was provided in Excel sheet [download Here] (https://canvas.instructure.com/files/273182802/download?download_frd=1) 

The excel sheet was used for calculation and creating pivot tables to summarize the total sales by product, region, and month
The excel sheet was for easy importing of files into: SQL to write various queries
Power BI to create dashboards using various charts (Donut Chart, piechart and clustered Column Chart)

### DATA ANALYSIS
---
Calculation in Excel
Generating Total Sales =SUM(H2:H50259) Capture total sales as revenue

calculating average total sales  =AVERAGE(H2:H9922) Capture sales data average by product


- Excel Chart

![image](https://github.com/user-attachments/assets/9ae688f3-a7f9-403d-9ceb-05f19e70623e)


![image](https://github.com/user-attachments/assets/7503ea03-e713-4c3c-b552-0664e3559304)



- Pivot Table

![image](https://github.com/user-attachments/assets/030e318c-a6e3-4595-a2bf-74cfb1476428)



-SQL VISUALS
   ![image](https://github.com/user-attachments/assets/e8f9b19e-602a-40e5-bfa3-891261f14f32)


   ![image](https://github.com/user-attachments/assets/bd0b9116-eb78-43f2-991a-0a72a6981e79)


   ![image](https://github.com/user-attachments/assets/6ca6bf66-10cd-42f7-8a9e-b8e5ca5ea516)




- DASH BOARD OVERVIEW WITH POWER BI:

![image](https://github.com/user-attachments/assets/a31fe3d7-2f0a-4bec-bfbd-243382428d35)



![image](https://github.com/user-attachments/assets/f9d79395-2f97-4772-8f00-a720ab17d6da)



![image](https://github.com/user-attachments/assets/bd98e09a-ca33-4271-ac99-48d535c28f63)



### Data Summary: 
---
The data provided outlines the sales/revenue figures for six products. Here’s a detailed breakdown:

Gloves: NGN 296,900.00

Hat: NGN 316,195.00

Jacket: NGN 208,230.00

Shirt: NGN 485,600.00

Shoes: NGN 613,380.00

Socks: NGN 180,785.00

Grand Total Sales/Revenue: NGN 2,101,090.00

### Key Insights:
---

Top Performing Product: Shoes lead the revenue figures with a total of NGN 613,380.00, representing the highest share of the total revenue (approximately 29.2%).

Second Top Product: Shirts follow with a total revenue of NGN 485,600.00 (approximately 23.1%).

Lowest Performing Product: Socks have the lowest total revenue, coming in at NGN 180,785.00 (approximately 8.6%).

- Regional Insights:

Top Performing Region: The South region leads with a total revenue of NGN 927,820.00, accounting for approximately 44.2% of the total revenue.

Second Top Region: The East region follows with a total revenue of NGN 485,925.00 (approximately 23.1%).

Lowest Performing Region: The West region has the lowest total revenue, coming in at NGN 300,345.00 (approximately 14.3%).

### Recommendations:
---
Focus on Top Products: Enhance marketing and sales efforts for Shoes and Shirts, as they contribute significantly to the revenue. Consider promoting these products through special offers, discounts, and targeted advertising campaigns.

Improve Low Performing Products: Investigate the reasons for low sales of Socks and Jackets. This could involve conducting market research to understand customer preferences and adjusting the product features or pricing accordingly.

Diversification: Explore opportunities to diversify the product line based on customer feedback and market trends. Introducing new products or variations of existing products could attract a broader customer base.

Seasonal Promotions: Utilize seasonal trends to boost sales. For example, promote Jackets and Gloves more aggressively during colder months.

### Conclusion: 
---
The analysis reveals that Shoes are the highest-earning product, accounting for the largest portion of revenue. Meanwhile, the Socks category shows room for improvement in sales strategies. The overall revenue distribution indicates a healthy mix of high-performing products, which can provide valuable insights for future product development and marketing initiatives.


Queries in SQL
SQL
PROJECT 1

1.	Retrieve the total sales for each product category.
   
```
SELECT product, SUM(Quantity * UnitPrice) AS total_sales
FROM [dbo].[SalesData$]
GROUP BY product;
```
2.	Find the number of sales transactions in each region.
   
```
SELECT region, COUNT(Quantity) AS total_transactions
FROM [dbo].[SalesData$]
GROUP BY region;
```

3.	Find the highest-selling product by total sales value.
   
```
SELECT TOP 1 product, SUM(Quantity * UnitPrice) AS total_sales
FROM [dbo].[SalesData$]
GROUP BY product
ORDER BY total_sales DESC
```
4.	calculate total revenue per product.

```
SELECT product, SUM(Quantity * UnitPrice) AS total_revenue
FROM [dbo].[SalesData$]
GROUP BY product;
```

5.	calculate monthly sales totals for the current year.

```
SELECT 
    MONTH(OrderDate) AS month,
  	SUM(UnitPrice) AS total_monthly_sales
  	FROM
[dbo].[SalesData$]
    WHERE
YEAR(OrderDate) = 2024
   GROUP BY 
MONTH(OrderDate)
    ORDER BY
month;
```

8.	Find the top 5 customers by total purchase amount.

 ```  
SELECT TOP 5 
 [Customer Id], 
    SUM(Quantity * UnitPrice) AS Total_Purchase_Amount
    FROM
[dbo].[SalesData$]
    GROUP BY 
   [Customer Id]
   ORDER BY 
Total_Purchase_Amount DESC;
```

8.	calculate the percentage of total sales contributed by each region.
   
```
SELECT 
Region,
  SUM(Quantity * UnitPrice) AS Regional_Sales,
  (SUM(Quantity * UnitPrice) / 
    (SELECT SUM(Quantity * UnitPrice) FROM dbo.SalesData$)) * 100 
    AS Percentage_of_Total_Sales
    FROM 
    [dbo].[SalesData$]
    GROUP BY 
    Region
    ORDER BY 
    Regional_Sales DESC;
```

9.	identify products with no sales in the last quarter.

```   
SELECT 
    DISTINCT Product
    FROM 
    dbo.SalesData$
    WHERE 
    Product NOT IN (
    SELECT 
         Product
         FROM 
           dbo.SalesData$
           WHERE 
            OrderDate >= DATEADD(q, DATEDIFF(q, 0, GETDATE()), 0)
    )
    ORDER BY 
    Product;
  	```  


