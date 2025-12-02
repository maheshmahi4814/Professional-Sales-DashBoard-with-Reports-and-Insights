# Professional-Sales-DashBoard-with-Reports-and-Insights
An end to end professional Sales Dash Board with using python, pandas, visulaizationtools ,sql ,powerbi
# Power BI Sales Analytics Dashboard  
End-to-end Data Analytics Project using Python, SQL, DAX & Power BI

---

## 📊 Project Overview
This project demonstrates a complete analytics pipeline—from raw data to an interactive business dashboard.  
The goal is to help business teams monitor *sales performance, revenue trends, returns, customer behavior, and **profitability across cities, categories, regions, and seasons*.

The dashboard is built using real-world workflow steps: Data Cleaning → EDA → SQL Modelling → DAX → Power BI Reporting.
and the rows / tuples of 40k in the data set
---

## 🚀 Key Features
- Interactive Power BI Dashboard (4 pages)
- Auto-rotating KPI visual (Profit per City)
- Fully cleaned dataset using Python
- SQL-based transformations & data modelling
- DAX measures for KPIs and advanced calculations
- Slicers with custom UI (rounded tiles)
- Trend analysis, category-level performance & return analysis
- Scatter plots for price–profit & quantity–profit patterns

---

## 🧱 Tech Stack
- *Python* (pandas, numpy, matplotlib, seaborn)
- *SQL* (MySQL / PostgreSQL)
- *Power BI Desktop & Power BI Service*
- *DAX*
- *Jupyter Notebook*

---

## 🗂 Workflow & Steps

### 1️⃣ Data Collection  
Datasets were imported into Jupyter Notebook for initial exploration and cleaning.

### 2️⃣ Data Cleaning & Preparation (Python)
Performed using pandas:
- Handling missing values  
- Converting datatypes  
- Outlier Winsorization  
- Feature extraction (Season, Month, Year)  
- Removing duplicates  
- Standardizing categorical fields  

Final cleaned dataset stored under  
(data cleaned)

---

### 3️⃣ Exploratory Data Analysis (EDA)
Key insights:
- Sales trend by month  
- Category-level contribution  
- High-return products  
- Profitability distribution  
- Outlier behavior & skewness  
- Seasonality patterns  

Visuals generated using Matplotlib & Seaborn.

---

### 4️⃣ SQL Analysis & Modelling  

Included:
- Fact & Dimension model creation  
- Joins for category-region mapping  
- Aggregations by city, category, season  
- Business-level calculated tables  

---

### 5️⃣ Power BI Data Modelling
Model consists of:
- *FactSales table*
- *DimCity*
- *DimCategory*
- *DimProduct*
- *DimDate*
- *DimRegion*

Relationships built using Star Schema.

---
Report Preview:
Page 1:
<img width="1667" height="942" alt="Screenshot 2025-12-02 141851" src="https://github.com/user-attachments/assets/0eb70616-19ba-4025-867e-56947dd34cff" />
Page 2:
<img width="1657" height="919" alt="Screenshot 2025-12-02 141912" src="https://github.com/user-attachments/assets/f2f9b12f-c78f-47eb-b13c-b2de1d0274ce" />
Page 3:
<img width="1661" height="945" alt="Screenshot 2025-12-02 141925" src="https://github.com/user-attachments/assets/8c621c16-7a47-4792-a7a1-d586cfc2e761" />

Page 4:
<img width="1699" height="974" alt="Screenshot 2025-12-02 141939" src="https://github.com/user-attachments/assets/f6ccf42a-5f53-4e59-bfba-71c16f87d2c9" />
Page 5:
<img width="1667" height="916" alt="Screenshot 2025-12-02 141953" src="https://github.com/user-attachments/assets/410663e3-852c-4949-9571-30cfe2c21051" />




### 6️⃣ DAX Measures (partial list)


Examples:
```DAX
Total Sales = SUM(FactSales[Sales])
Total Profit = SUM(FactSales[Profit])
AOV = [Total Sales] / DISTINCTCOUNT(FactSales[OrderID])

Profit Per City = 
VAR SelStep = SELECTEDVALUE(CityRotation[Step])
VAR SelectedCity =
    SWITCH(
        SelStep,
        1, "Chennai",
        2, "Bangalore",
        3, "Delhi",
        4, "Mumbai"
    )
RETURN
CALCULATE([Total Profit], DimCity[City] = SelectedCity)
