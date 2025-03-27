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

9. Visualizations > Add data to your visual > Clustered bar chart

10.Bar Chart: Add data to your visual > drag field "EducationField" in the Y-axis 

11.Add data to your visual > drag field EmployeeNumber in the X-axis > select "count(Distinct)"

//Column Chart 2: 

12.Visualizations > Add data to your visual > Clustered column chart

13.Add data to your visual > drag field "Job Role" in the X-axis 

14.Add data to your visual > drag field EmployeeNumber in the Y-axis > select "count(Distinct)"

//Page 2: "HC - Drill through Y":

//Card "Total Headcount": 

15.Visualizations > Add data to your visual > card

16.Add data to your visual > drag field EmployeeNumber into Fields > select "count(Distinct)"

//Column Chart

17.Visualizations > Add data to your visual > Clustered column chart

18.Column Chart: Add data to your visual > drag field "Department", "EducationField" and "JobROle" in the X-axis > sort axis > "Count of EmployeeNumber" > Sort descending

19.Add data to your visual > drag field EmployeeNumber in the Y-axis > select "count(Distinct)"

