# **Attrition Rate Analysis Dashboard (Power BI)**

## **Overview**
Employee turnover is one of the most critical workforce challenges organizations face. Understanding why employees leave and identifying patterns across departments and compensation levels can help HR leaders develop targeted retention strategies.

This Power BI project analyzes employee attrition trends using HR data and provides interactive insights into workforce stability and salary distribution. The solution combines data modeling, Power Query transformations, DAX calculations, and interactive visualizations to support data-driven decision making.

**Tools Used:**  
- Power BI Desktop
- Power Query (M) for data transformation
- DAX for KPI calculations and business logic
- Data Modeling using a star-schema approach
- HR Analytics Dataset (Kaggle)

---

## **Business Questions**
- What is the overall attrition rate?
- How does attrition vary across salary ranges?

---

## Data Model
Data from kaggle.com (HR Analytics Datasets: https://www.kaggle.com/datasets/muhammadehabmuhammad/hr-analytics-datasets), containing 3 table: a fact table, named HR, and 2 dimension tables, named Employee and Department.


| Table      | Type       | Description                                       |
| ---------- | ---------- | ------------------------------------------------- |
| HR         | Fact Table | Employee workforce events and termination records |
| Employees  | Dimension  | Employee demographic and salary information       |
| Department | Dimension  | Department hierarchy and attributes               |


I set the relationship between the table: HR and Employees have a one-to-one relationship, because there is a unique ID value in both. HR and Department have a many-to-one relationship, with the value 'Department' that is present multiple times in the HR table and as a unique value in the Department Table

<img width="1061" height="634" alt="image" src="https://github.com/user-attachments/assets/b55f551e-f01b-4468-b95d-146ce68f5c3a" />

## Data Preparation

Key transformations performed in Power Query include:

- Data quality validation and duplicate ID checks
- Creation of an Attrition Flag based on termination status
- Salary band segmentation for comparative analysis
- Data cleansing and standardization


## Key Metrics (DAX)
### Attrition Classification 
```
Attrition =
IF (
    ISBLANK ( 'HR Data'[Termination Date] ),
    "No",
    "Yes"
)
```
### Headcount
```
'HC': `COUNT('HR data'[ID])`
```
### Attrition Rate
```
Attrition % =
DIVIDE(
    CALCULATE(
        COUNT('HR Data'[ID]),
        'HR Data'[Attrition] = "Yes"
    ),
    COUNT('HR Data'[ID])
)
```

### Overall Average Attrition Rate
```
Overall Attrition % =
CALCULATE(
    AVERAGEX(
        'Department Bridge',
        [Attrition %]
    ),
    REMOVEFILTERS(
        Employees[Salary Group]
    )
)
```
### Attrition Variance
```
Attrition Variance % =
DIVIDE(
    [Attrition %] - [Overall Attrition %],
    [Overall Attrition %]
)
```

## Dashboard Features
### Salary Band Analysis

**Visual** Clustered Column Chart

#### Purpose

Analyze workforce distribution across salary bands and identify employee segments exposed to higher turnover risk.

---

### Attrition Trend Analysis

**Visual** Stacked Area Chart

#### Purpose

Track employee exits over time and monitor turnover trends.

---

### Attrition Distribution

**Visual** 100% Stacked Bar Chart
#### Purpose

Shows the proportion of active versus terminated employees, providing a clear view of overall workforce retention and attrition.

---

### Attrition Benchmark Panel

**Visual** KPI Cards with Conditional Formatting

#### Purpose

Compare salary-group attrition rates against the company average.

#### Indicators
```
🟢 Better than average
🟡 In line with average
🔴 Worse than average
```




<img width="1287" height="730" alt="image" src="https://github.com/user-attachments/assets/0f711123-027a-43c5-adc3-282604610f53" />




## Key Insights

#### Overall Attrition rate is 29 %
#### Higher Attrition in Lower Salary Bands

Employees in the **€30k–€33k** salary range show the highest attrition levels, indicating that compensation may be a significant driver of employee retention.


---

## Skills Demonstrated

#### Power BI

- Data Modeling
- Power Query
- DAX
- Interactive Reporting & KPI Development
- Conditional Formatting
