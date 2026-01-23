# **HR Dashboard (Power BI)**

## **Overview**
The scope the project is to create a comprhenesive dahboard which give quick and complete overviem on Company's headcount, with informationabout geographical and organiztional distribution, gender, age and seniority seniority. The dashboard should be user-friendly and showing data which update weekly, in this case there is no need for 'real-time' data

**Tools Used:**  
- Power BI Desktop: M for ETL, DAX, calculated columns, data modelling to manage tables' relationships, data visualizations, visual calculations
- Power BI Service: scheduled refresh, publication 
- Dataset: HR Analytics Dataset created with https://www.mockaroo.com/

---

## **Business Questions**
- What's the company Department with the highest number of employees? And the country?
- Which is the most represented Gender in the most populated country?
- Which is the oldest country? And the one with the highest tenure?

---

## Key Features
1. I downloaded the dataset from https://www.mockaroo.com/ I save it in a SharePoint folder. This way I will be able to refresh the data from Power Bi Service. In this case, after importing the data with'import' funciont, I'll set a Weekly scheduled refresh to have updated data every week

2. Get data > SharePoint folder > 'link to the folder' > filtering 'folder path' with the exact path to the file we need


3. **Transform Data** > Looking for duplicate values in column ID, or null values 

4. **Add Conditional Column** to create Age ranges based on the value 'Age', and doing the same to create Seniority ranges


4. Go to **Report view**: 

5. Create measure: **Calculations** > **New Measure** 'HC': `DISTINCCOUNT('HC'[ID])`

6. **Visualizations** > **Add data to your visual** > **Clustered Bar Chart** > drag field 'HC' in the X-axis and Country in the Y-axis

7. **Visualizations** > **Add data to your visual** > **Table** > drag field 'HC' and 'Department' into 'Columns

8. **Visualizations** > **Add data to your visual** > **Dount Chart** drag field 'HC' in Values and 'Gender' in 'Legend'

9. **Visualizations** > **Add data to your visual** > **Column Clustered Chart** drag field 'HC' in Y-axis and 'Age Range' in Y-axis > **New visual calculation** to create a visual calculation called 'index' that, leveraging 'SWITCH', will assign a number from 1 to 5 to the Age ranges: this way I will be able to represent the column in crescent range order (<30, 30-35 etc.). I will do the same to create a Seniority range chart


## **Insights**
- Engineering Department is the one with the highest number of employees (95)
- China is the country with the highest number of employees (184), where males and females are equally represented (48%)
- Sweden is the country with the highest average age (49,3 Years) and Ukraine is the one with the highest average tenure (11,8)
