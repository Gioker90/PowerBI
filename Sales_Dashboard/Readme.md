# PowerBI_Sales_Dashboard

## Overview
This project focuses on creating a **single-page Power BI dashboard** to analyze sales data from six coffee shops located in different areas of Rome. The dataset, generated using https://mockaroo.com/, contains **299 orders** distributed across **three years (2024–2025)**. Each order includes 1–3 items with associated prices.

The dashboard aims to provide:
- A clear view of **overall sales trends** over the last three years.
- **Revenue breakdown by product type** (Cappuccino, Espresso, etc.).
- Year-over-year comparison of revenues with filtering capabilities.

**Tools Used:**  
- Power BI: M for ETL, data modelling, DAX, variables
- DAX  

## Business Questions
1. **Which product type contributes the most to overall revenue?**
2. **How do revenues compare across different years?**
3. **What is the best performing shop? What the worst?**
   
## Key Features

1.**Import data: Home** > **Get data** > **Text/CSV**

2.**Transform Data** > **Remove Column** (unecessary columns) > **Reorder Column** (in order to have the primary key as first column) > **Remove Duplicates**

3.**Create new measure**, called 'product' Revenues (in this case 'Cappuccino'), using `SUMX`. Then doing the same for all the 4 products

`

    Var prod1=SUMX(
    filter(Sales_data, Sales_data[product_1]="Cappuccino"), Sales_data[sales_id]
    )
    VAR prod2=SUMX(
    filter(Sales_data, Sales_data[product_2]="Cappuccino"), Sales_data[sales_id]
    )
     VAR prod3=SUMX(
    filter(Sales_data, Sales_data[product_3]="Cappuccino"), Sales_data[sales_id]
    )

    RETURN prod1+prod2+prod3

### Card "Revenues": 

4.**Visualizations** > **Add data to your visual** > **card**

5.**Add data to your visual** > drag measure Count of 'name of the product'  into Fields > select 

6.Creating 4 different card, each per every product

7.**Create new measure**, called 'product' Revenues (in this case 'Cappuccino'), using `COUNTX` to filter only the desired prodcut. Then doing the same for all the 4 products

`

    Var prod1=COUNTX(
    filter(Sales_data, Sales_data[product_1]="Espresso"), Sales_data[sales_id]
    )
    VAR prod2=COUNTX(
    filter(Sales_data, Sales_data[product_2]="Espresso"), Sales_data[sales_id]
    )
     VAR prod3=COUNTX(
    filter(Sales_data, Sales_data[product_3]="Espresso"), Sales_data[sales_id]
    )

    RETURN prod1+prod2+prod3

8.**Create new measure**, called Var % 'Product' Sales

`

    Var Sales_current_Y=CALCULATE([Count of Cappuccino])

    Var Sales_previous_Y=CALCULATE(
    [Count of Cappuccino], SAMEPERIODLASTYEAR(Sales_data[sales_date].[Date])
    )

    RETURN (Sales_current_Y-Sales_previous_Y)/Sales_previous_Y


## Final Insights
- **Top-performing product:** Latte consistently drives the highest revenue across all shops, while Matcha being the worst selling product
- **Year-over-year growth:** Overall sales increased by approximately **30%** from 2023 to 2024, while they are stable from 2024 to 2025
- **Shop performance:** Shop located in Trevi Fountain generated the highest revenue in 2025, while Colosseum was the lowest
