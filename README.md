**📱 Mobile Sales Data – Power BI Dashboard**

An interactive Power BI dashboard that analyses mobile phone sales by brand, model, city, payment method and customer ratings, with time-intelligence reports (MTD and Same Period Last Year).

📊 Dashboard Pages
Page	What it shows
Dashboard	KPI cards, sales by mobile model, payment method split, sales by city (map), brand-wise sales table, monthly units sold, sales by day of week, and customer ratings funnel
MTD Report	Month-to-date sales trend with Year, Month, Mobile Model and Payment Method filters
Same Period Last Year	Current sales vs. same period last year, compared by day, quarter and year

Note: Every page has slicers for interactive filtering and a page navigator for switching between reports.

🗂️ Data Model
Sales_Data – transaction-level data (Transaction ID, Brand, Mobile Model, Units Sold, Price Per Unit, Customer Name, Customer Age, City, Payment Method, Customer Ratings, Date)
Custom_Calendar – date table (2021–2024) created in Power Query
Relationship: Sales_Data[Date] → Custom_Calendar[Date] (many-to-one)

🧮 DAX Used
DAX
Total Quantity = SUM(Sales_Data[Units Sold])

Total_Sales = SUMX(Sales_Data, Sales_Data[Units Sold] * Sales_Data[Price Per Unit])

Transactions = COUNTROWS(Sales_Data)

Average_Price = AVERAGE(Sales_Data[Price Per Unit])

MTD = TOTALMTD([Total_Sales], Custom_Calendar[Date].[Date])

Same Period Last Year =
CALCULATE([Total_Sales], SAMEPERIODLASTYEAR(Custom_Calendar[Date].[Date]))

Rating Status (Calculated Column) =
IF(Sales_Data[Customer Ratings] >= 4, "Good",
    IF(Sales_Data[Customer Ratings] > 2, "Average", "Poor"))
    
🛠️ Skills Practised
Data cleaning and transformation in Power Query
Creating a custom calendar table
Building table relationships in the data model
Writing DAX measures and calculated columns
Time intelligence (MTD, Same Period Last Year)
Dashboard design: KPI cards, charts, map, slicers and navigation
Editing visual interactions.
