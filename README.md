# -Maven Electronics Retail Analysis|Revenue,Trends and insights
Excel + Power BI Project | Global+ Electronics+ Retailers From raw data to Business Insights

Table of contents

* [Project Overview](*project-overview)
* [Tools & Technologies](*tools--technology)
* [Dataset Overview](*dataset-overview)
* [Data Cleaning Process](*data-cleaning-process)
* [Data Modelling](*data-modelling)
* [Powerbi Measures](*power-measures)
* [Powerbi Dashboard](*powerbi-dashboard)
* [Key Insight](*key-insight)
* [Recommendation](*recommendation)

### Project overview
This project analyze global electronics retail stores data to uncover trends in revenue, Year over Year comparison, product performance customer insights, store and regional performance. 
Using Excel for data cleaning, Using SQL for data exploratory  power bi for data modelling and visualization, the project turn raw transaction records into actionable business insight.

### Tools & Technologies
* Excel
* Data modelling
* Power bi

### Dataset Overview
The dataset consists of multiple related tables Model into one
* Sales: Contains transactional data including orders, delivery dates, quantities,
currency, and links to customers, stores, and products.
* Customers : Provides customer demographics (gender, age, location) to analyze
customer behavior and segmentation.
* Products: Includes product details (brand, color, subcategory, category, unit
cost, and unit price) for product performance and profitability analysis.
* Stores: Provides store-level details (location, size, and open date) to assess
regional and store performance.
* Exchange Rates (Supporting Table): Provides conversion rates by date and
currency to ensure consistent reporting in USD.

Sample preview of the sales table
<img width="1090" height="649" alt="Screenshot 2026-02-25 044716" src="https://github.com/user-attachments/assets/9f0b40f6-274a-4436-9468-834959dd1b1d" />

### Data Cleaning Process
preform in Excel ,Data modelling and power BI:
* Converted date to proper datetime format
* Removed missing or invalid values 
* Remove duplicates
* Created new calculated feilds
* Revenue = unit_sold + unit price
* Profit_margin = profit/Revenue

### Data Modelling: 
Table sequence(Using each similar columns in each table to merge to other table)
Customers (Birthdate) + Exchange rate (Date)+ product (Deliverydate) + sales (Productkey)+ store (Storekey)+ Calender date.

### Powerbi Measures
```(Power BI dax)
SELECT*
FROM SALES ,Profit Margin = DIVIDE([Total Profit],[Revenue])
```
```(Power BI dax)
select*
FROM SALES ,Total profit YOY = VAR CY_ = [Total Profit]
VAR PY_ = [Total profit LY]
VAR PER_ = DIVIDE(CY_ - PY_, PY_)
VAR FORMAT_ = SWITCH(TRUE(),CY_> 0, UNICHAR(11165) & " " & FORMAT(PER_, "0.0%"), UNICHAR(11167) & " " & FORMAT(PER_,"0.0%"))
RETURN FORMAT_ 
```
```(Power BI dax)
SELECT *
FROM SALES ,Unit sold color = VAR CY_ = [unit sold]
VAR PY_ = [Unit sold LY]
VAR PER_ = DIVIDE(CY_ - PY_, PY_)
VAR FORMAT_ = SWITCH(TRUE(),CY_> 0,  "green", CY_ < 0 ,"Red", "Grey")
RETURN FORMAT_
```
### Powerbi Dashboard
This dashboard include the following visuals 
- Revenue and profit overtime overtime
- Profit and Revenue by category
- Revenue by Age-group
- Regional sales performance 
- Revenue and profit by Gender
- Top and buttom 10 products by profit & Revenue
* Interactive filters for Year over year comparision

;<img width="1179" height="664" alt="Screenshot 2025-10-14 175532" src="https://github.com/user-attachments/assets/fceefd37-318c-4658-bae9-650dca03a045" />
<img width="1172" height="678" alt="Screenshot 2025-10-14 175602" src="https://github.com/user-attachments/assets/f2d4e46c-c464-4de3-8fe9-71464a4d6e29" />
<img width="1183" height="673" alt="Screenshot 2025-10-14 175623" src="https://github.com/user-attachments/assets/8f5d00d9-6778-4e10-83b1-909b92af0ccd" />


### Key Insights
1.Maven Electronics generated $34.6M revenue and $20.25M profit with +2.2% YoY growth, indicating strong profitability and early recovery after the 2020 decline.
2.Computers, Desktops, and Televisions dominate sales and profit, showing heavy revenue concentration in a few core product categories.
3.Adventure Works contributes $11.8M revenue, revealing reliance on a single leading brand.
4.Adults and middle-aged customers account for 68% of total sales, identifying the primary revenue-driving demographic.
5.North America delivers over 60% of revenue and the U.S. alone $17M profit, highlighting significant geographic dependence.
6.Sales peaked in 2019 and declined from 2020, indicating a major performance shift after the peak year.
7.Audio and Games categories underperform compared to others, showing imbalance in product portfolio performance.

### Recommendation
* Invest more in top categories (Computers, Desktops, Televisions) to sustain growth.
* Reuse successful 2019 strategies to recover sales momentum.
* Diversify brands to reduce reliance on Adventure Works.
* Target adults and middle-aged customers with focused marketing.
* Expand into Europe to reduce North America dependence.
* Improve Audio and Games through pricing and bundling.
* Deploy a unified BI dashboard for performance tracking.

### Data source 

[Download Here](www.linkedin.com/in/mercydataanalyst)
