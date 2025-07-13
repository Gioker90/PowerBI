# PowerBI_Sales_Dashboard

First of all, I created a dataset, using https://mockaroo.com/, made of one excel file containing Sales data. The file contains the sales data of 6 coffee shops in different areas of Rome, selling 4 different types of product. There is 299 different orders distributed along 3 years (2024-2025). Every order can have from 1 to 3 items, each represented in a different columns, with a price column aside

**Goal: creating a single page dashboard that represent the overall sales trend of the shops along the last 3 years. The Dashboard shpuld represent the revenues generated per type of pèroduct, and there should be the possibility to filter the year and see the comparison, in terms of revenues, with the previous year**

1.**Import data: Home** > **Get data** > **Text/CSV**

2.**Transform Data** > **Remove Column** (unecessary columns) > **Reorder Column** (in order to have the primary key as first column) > **Remove Duplicates**

3.**Create new measure**, called 'product' Revenues (in this case 'Cappuccino'), using `SUMX` c. Then doing the same for all the 4 products

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


