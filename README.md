# LITA-CAPSTONE-PROJECT


## PROJECT OVERVIEW:
Making reference to the data and capstone project document shared earlier, by analyzing the sales performance of a retail store and carrying out the following exploratory process of the sales data to uncover key insights such as

### Top Selling Products
Regional Performances
Monthly Sales Trend and By telling a compelling story and building an interactive dashboard Power Bi report: To gather insight, Highlight findings And making business decisions.

### DATA DESCRIPTION:
This dataset includes the following Columns:

Order Number
Customer Id
products
region
Order Date
Quantity
Unit Price
DASH BOARD REVIEW:
Customer Id
products: Items sold in the store
region: The other regional branches of the store ( North, South, East West)
Order Date: Date order was palced
Quantity: The number of units of the product ordered in each transaction
Unit Price: The aquisition cost per unit of the product
STATISTICS ABOUT THE DATASET:
Number of Unique Customers: 50,000 Number of Products: 6 Total Sales: 10587500 image Total Region: 4

### METHODOLOGY:
Data Collection
The dataset for this analysis was provided by LITA_ The Incubator Hub for leaening and training purposes. The data was provided in Excel sheet [download Here] (https://canvas.instructure.com/files/273182802/download?download_frd=1) or https://eu.docworkspace.com/d/sILre1-uDAsKJzrgG?sa=wa&ps=1&fn=LITA%20Capstone%20Dataset%20(1).xlsx The excel sheet making it accessible to

analyse the excel sheet The excel sheet was further converted to CSV format for easy importing of files into:
SQL to write various queries
Power BI to create dashboards using various charts (pieChart and clustered Column Chart)
DATA ANALYSIS:
Calculation in Excel
Generating Total Sales (=F2* G2) Capture total sales as revenue

calculating average sales by product  =AVERAGEIF($C1:$C50001,$C2,$H1:$H50001) Capture sales data average by product

*calculating total revenue by region  ==SUMIF($D1:$D50001,$D12630,$H1:$H50001) Capture total revenue by region sales data

Excel Chart
my project capstone chart1

my project capstone chart2

Pivot Table
Capturesales new pivot table

Queries in SQL
SQL
PROJECT 1

1.	Retrieve the total sales for each product category.
SELECT product, SUM(Quantity * UnitPrice) AS total_sales
FROM [dbo].[SalesData$]
GROUP BY product;

2.	Find the number of sales transactions in each region.
SELECT region, COUNT(Quantity) AS total_transactions
FROM [dbo].[SalesData$]
GROUP BY region;

3.	Find the highest-selling product by total sales value.
SELECT TOP 1 product, SUM(Quantity * UnitPrice) AS total_sales
FROM [dbo].[SalesData$]
GROUP BY product
ORDER BY total_sales DESC

4.	calculate total revenue per product.

SELECT product, SUM(Quantity * UnitPrice) AS total_revenue
FROM [dbo].[SalesData$]
GROUP BY product;

5.	calculate monthly sales totals for the current year.
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

6.	Find the top 5 customers by total purchase amount.
SELECT TOP 5 
    [Customer Id], 
    SUM(Quantity * UnitPrice) AS Total_Purchase_Amount
FROM 
    [dbo].[SalesData$]
GROUP BY 
   [Customer Id]
ORDER BY 
Total_Purchase_Amount DESC;

7.	calculate the percentage of total sales contributed by each region.
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

8.	identify products with no sales in the last quarter.
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

   -SQL VISUALS
   ![image](https://github.com/user-attachments/assets/e8f9b19e-602a-40e5-bfa3-891261f14f32)

   ![image](https://github.com/user-attachments/assets/bd0b9116-eb78-43f2-991a-0a72a6981e79)

   ![image](https://github.com/user-attachments/assets/6ca6bf66-10cd-42f7-8a9e-b8e5ca5ea516)



DASH BOARD OVERVIEW WITH POWER BI:
image

INSIGHTS GENERATION:

Insights on Total Sales (Revenue) In The Different Regions
South Region: Leads in Total sales and generates more revenue with 4,675,000 which indicates a potentially larger transaction values per sale.
East Region: Close behind is the East region with total sales of 2,450,000 which is about 23.14% of the total Sales. This indicates a competitive market with a strong transaction
North Region: Shows great performance with 1,950,000 in sales and 18.42% of Total Sales (Revenue), showing consistent customer interest in the retail shop and the items stocked in it
West Region: Shows equally a good market as it is actively competitive with the Northern market with a close range performance of 1,512,500 and 14.29% of the total revenue. indicating steady purchasing activity.
Insights on the total revenue generated by each product
Shoes: Leads in Total sales and generates more revenue with 3,087,500 which indicates a potentially higher priced item or larger quantity of the item sold.
Shirt: Close behind is shirt with total sales of 2,450,000 which is about 23.14% of the total Sales. This indicates a competitive market and categorised as the second best purchased product
Chart Display my project capstone chart2

RECOMMENDATION:
Region Comparison: Implement targeted marketing strategies, campaign or advert to create more awareness in the North and West region especially so as to curate more sales and generate more revenue

Sales Optimization: Make most effective use of the market trend by stocking more items with lead revenue generating power which are (Shoes and Shirts)

CONCLUSION:
The retail shops in the North ancd west region needs more focus and attention on

boosting revenue through marketing strategies
studying of market trend within the region to adequately decode the hihgest selling product in the region, so as to stock more.
