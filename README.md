# PowerBI_HR_Metrics
//HR Metrics

1.Download file HR.employee_Attrition.csv from Kaggle.com (https://www.kaggle.com/datasets/rishikeshkonapure/hr-analytics-prediction/data)

2.Import data: Home > Get data > Text/CSV 

3.Transform Data > Remove Columns (unecessary columns) > Reorder Column (in order to have the primary key as first column) > Remove Duplicates

//Page 1: "HC - Drill through N":
//Card "Total Headcount": 

4.Visualizations > Add data to your visual > card
5.Add data to your visual > drag field EmployeeNumber into Fields > select "count(Distinct)"

//Column Chart 1: 
6.Visualizations > Add data to your visual > Clustered column chart
7.Add data to your visual > drag field "Department" in the X-axis 
8.Add data to your visual > drag field EmployeeNumber in the Y-axis > select "count(Distinct)"

//Bar Chart:
Visualizations > Add data to your visual > Clustered bar chart
9.Bar Chart: Add data to your visual > drag field "EducationField" in the Y-axis 
10.Add data to your visual > drag field EmployeeNumber in the X-axis > select "count(Distinct)"
9.Column Chart 2: Add data to your visual > drag field "Job Role" in the X-axis 
10.Add data to your visual > drag field EmployeeNumber in the Y-axis > select "count(Distinct)"

//Page 2: "HC - Drill through Y:
10.Card "Total Headcount": Add data to your visual > drag field EmployeeNumber into Fields > select "count(Distinct)"

11.Column Chart: Add data to your visual > drag field "Department", "EducationField" and "JobROle" in the X-axis > sort 			axis > "Count of EmployeeNumber" > Sort descending
Add data to your visual > drag field EmployeeNumber in the Y-axis > select "count(Distinct)"

