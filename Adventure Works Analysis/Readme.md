### 📊 Adventure Works Excel Dashboard

## 📘 Project Overview
The **Adventure Works Dashboard** is an interactive Excel-based business intelligence report built using **Power Query**, **Power Pivot**, and **Pivot Charts**.  
It analyzes sales performance, production cost, profit, and customer insights for the Adventure Works dataset.

This project demonstrates **data modeling**, **DAX calculations**, and **dashboard design** for professional Excel analytics.

## 🎯 Objectives
- Combine and clean data from multiple sources using **Power Query**
- Build a **Data Model** connecting Fact and Dimension tables
- Use **DAX formulas** for dynamic calculations
- Visualize business KPIs using **interactive dashboards**

## 🗂️ Data Sources
The project uses data from the **AdventureWorks** dataset, including:

- FactInternetSales  
- Fact_Internet_Sales_New  
- DimProduct, DimProductSubCategory, DimProductCategory  
- DimCustomer  
- DimDate  
- DimSalesTerritory  

## 🧩 Data Preparation Steps

### 🔹 Power Query
1. Imported data from multiple Excel files.  
2. Appended FactInternetSales and Fact_Internet_Sales_New into a single fact table.  
3. Merged product-related tables: DimProduct + DimProductSubCategory + DimProductCategory  
4. Cleaned and formatted all columns (date, numeric, text).

### 🔹 Data Model (Power Pivot)
Relationships were created between Fact and Dimension tables:

FactInternetSales[ProductKey] → DimProduct[ProductKey]  
FactInternetSales[CustomerKey] → DimCustomer[CustomerKey]  
FactInternetSales[SalesTerritoryKey] → DimSalesTerritory[SalesTerritoryKey]  
FactInternetSales[OrderDate] → DimDate[DateKey]  

Added calculated columns and DAX measures for analysis.

## 🧮 Key DAX Calculations

### 📅 Date Fields (from OrderDateKey)
OrderDate = DATE(LEFT([OrderDateKey],4), MID([OrderDateKey],5,2), RIGHT([OrderDateKey],2))  
Year = YEAR([OrderDate])  
MonthNo = MONTH([OrderDate])  
MonthFullName = FORMAT([OrderDate],"MMMM")  
Quarter = "Q" & FORMAT([OrderDate],"Q")  
YearMonth = FORMAT([OrderDate],"YYYY-MMM")  
WeekdayNo = WEEKDAY([OrderDate],2)  
WeekdayName = FORMAT([OrderDate],"dddd")  
FinancialMonth = IF(MONTH([OrderDate])>=7, MONTH([OrderDate])-6, MONTH([OrderDate])+6)  
FinancialQuarter = "Q" & INT(( [FinancialMonth]-1 )/3)+1  

### 💰 Measures
Total Sales := SUMX(FactInternetSales, FactInternetSales[UnitPrice] * FactInternetSales[OrderQuantity] * (1 - FactInternetSales[UnitPriceDiscountPct]))  
Total Production Cost := SUMX(FactInternetSales, FactInternetSales[ProductStandardCost] * FactInternetSales[OrderQuantity])  
Total Profit := [Total Sales] - [Total Production Cost]  
Profit Margin % := DIVIDE([Total Profit], [Total Sales], 0)  

## 📅 Calendar Table (DimDate)
A full calendar table was created in Power Pivot using DAX:

Calendar =  
ADDCOLUMNS(  
    CALENDAR(DATE(2010,1,1), DATE(2025,12,31)),  
    "Year", YEAR([Date]),  
    "MonthNo", MONTH([Date]),  
    "MonthName", FORMAT([Date],"MMMM"),  
    "Quarter", "Q" & FORMAT([Date],"Q"),  
    "YearMonth", FORMAT([Date],"YYYY-MMM"),  
    "WeekdayName", FORMAT([Date],"dddd"),  
    "FinancialMonth", IF(MONTH([Date])>=7, MONTH([Date])-6, MONTH([Date])+6),  
    "FinancialQuarter", "Q" & INT((IF(MONTH([Date])>=7, MONTH([Date])-6, MONTH([Date])+6)-1)/3)+1  
)  

## 📊 Dashboard Components
1️⃣ KPI Cards  
- Total Sales  
- Total Profit  
- Profit Margin %  
- Total Customers  

2️⃣ Charts  
- Combo Chart: Sales vs Production Cost by Year  
- Pie Chart: Gender-wise Sales  
- Bar Chart: Top 5 Products by Profit  
- Column Chart: Territory-wise Sales  
- Line Chart: Month-wise Sales Trend  

3️⃣ Filters (Slicers)  
- Year  
- Month  
- Country / Sales Territory  

## 📈 Key Insights
- 2013 recorded the highest sales and profit margin.  
- Europe and North America were the top-performing territories.  
- Profit margin maintained at around 41% across the period.  
- Gender contribution to total sales was almost equal.  
- Top-selling products were from the Mountain Bike category.

## 🧰 Tools & Technologies
- Microsoft Excel  
- Power Query  
- Power Pivot  
- DAX  
- Pivot Tables & Pivot Charts  
- Excel Slicers & Formatting  

## 🚀 How to Use
1. Download the Excel file.  
2. Enable Data Model and Power Pivot in Excel.  
3. Use Slicers (Year, Month, Country) to filter and interact with the dashboard.  
4. Explore KPIs and charts dynamically.  

## 📦 Deliverables
- Combined Fact Table: FactInternetSales_All.xlsx  
- Dimension Tables: DimProduct, DimCustomer, DimDate, DimSalesTerritory  
- Final Dashboard File: AdventureWorks_Dashboard.xlsx  
- Documentation: README.docx  

## 🏁 Conclusion
This project demonstrates how to transform raw Adventure Works data into meaningful insights using Excel’s Business Intelligence features.  
It integrates ETL using Power Query, Data Modeling using Power Pivot, DAX Calculations, and Interactive Dashboards — all within Microsoft Excel.

## 👩‍💻 Author

-**LinkedIn-** www.linkedin.com/in/sai-subhashree-14681520b

-**EmailID-** saidalal02@gmail.com

<img width="1413" height="648" alt="image" src="https://github.com/user-attachments/assets/18603762-e605-4a0f-97c4-985a17f221e8" />




