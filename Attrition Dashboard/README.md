# **Attrition Rate Analysis Dashboard (Power BI)**

## **Overview**
This project analyzes employee attrition trends using HR data to help organizations understand workforce dynamics and identify risk factors. The dashboard provides insights into attrition rates by salary groups, departments, and time periods.

**Tools Used:**  
- Power BI: M for ETL, DAX, calculated columns, data modelling to manage tables' relationships, data visualizations,  
- Dataset: HR Analytics Dataset from Kaggle

---

## **Business Questions**
- What is the overall attrition rate?
- How does attrition vary across salary ranges and departments?

---

## Key Features
1. Download xslsx file from kaggle.com (HR Analytics Datasets: https://www.kaggle.com/datasets/muhammadehabmuhammad/hr-analytics-datasets), containing 3 table: a fact table, named HR, and 2 dimension tables, named Employee and Department.

2. Go to **Model view** > set the relationship between the table: HR and Employees have a one-to-one relationship, because there is a uniqe ID value in both. HR and Department have a mant-to-one relationship, with the value 'Department' that is present multiple times in the HR table and as a unique value in the Department Table

3. **Transform Data** > Looking for duplicate values in column ID > **Add Conditional Column** 'Attrition', with the following condition: 

`IF Termination Date = null THEN 'No', ELSE 'Yes'`

### Clustered Column Chart

4. Go to **Report view**: 

5. **Visualizations** > **Add data to your visual** > **Clustered Column Chart**

6. Create measure: **Calculations** > **New Measure** 'HC': `COUNT('HR data'[ID])`

7. **Add data to your visual** > drag field 'Salary' in the X-axis 

8. Right click on 'Salary' > **New Group** > create 4 groups: 30-33k, 33-36k, 36-39k, >39k

9. **Add data to your visual** > drag  Measure 'HC' in the Y-axis

### Stacked Area Chart

10. **Visualizations** > **Add data to your visual** >**Stacked Area Chart**

11. **Add data to your visual** > drag field 'Termination Date' in the X-axis 

12. **Add data to your visual** > drag Measure 'HC' in the Y-axis

### 100% Stacked Bar Chart

13. **Visualizations** > **Add data to your visual** >**100% Stacked Bar Chart**

14. **Add data to your visual** > drag  Measure 'HC' in the X-axis 

15. **Add data to your visual** > drag Field 'Attrition' in 'Legend'

### Attrition rate vs Overall av. Attrition rate panel

16. **Insert** > **Text box** to create the title of the panel and the 4 groups titles

17. Create Measure: **Calculations** > **New Measure** 'attrition %':

`DIVIDE(CALCULATE(COUNT('HR data'[ID]), 'HR data'[Attrition]="Yes"), COUNT('HR data'[ID]))` to calculate the attrition that will change based on what the user select

18. Create Measure: **Calculations** > **New Measure** 'attrition 2':

`CALCULATE(AVERAGEX('Department Bridge', [attrition %]), REMOVEFILTERS(Employees[Salary Updated (groups)]))` that, instead, won't be affected by any filtering

19. Create Measure: **Calculations** > **New Measure** 'Variation %':

`([attrition %]-[av attrition 2])/[av attrition 2]`

20. **Visualizations** > **Add data to your visual** > **Table**

21. **Add data to your visual** > drag 'Variation %' Measure in 'Columns' and filtering the first group of salary (30-33k) (**Filters**>**Filters on this visual**>drag 'Salary' Field into the filters panel) > right click on 'Variation %' > **Conditional formatting** > **Icons** > **Format style: Rules** > **based on 'Variation %'**>

`IF 'Variation %' > 0 THEN`  ![image](https://github.com/user-attachments/assets/f31473eb-40db-4fd6-853a-5d91fe359245)

`IF 'Variation %' = 0 THEN`  ![image](https://github.com/user-attachments/assets/26649a8a-54fb-4300-a4a2-1261749c42b8)

`IF' Variation %' < 0 THEN` ![image](https://github.com/user-attachments/assets/42f4da43-7c6d-444a-aee4-101d6970ede3)

22. Do the same for the other 3 groups of salary


## **Insights**
- Higher attrition observed in lower salary ranges (30–33k).
