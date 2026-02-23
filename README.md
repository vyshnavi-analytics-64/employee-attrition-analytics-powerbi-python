# employee-attrition-analytics-powerbi-python
End-to-end HR analytics project using Python and Power BI

# Employee Attrition & Performance Analytics

## Overview
This project simulates a real-world HR analytics use case where raw employee data is transformed into actionable insights to understand workforce attrition, tenure patterns, and performance trends.  

The solution follows an end-to-end analytics workflow using **Python for data processing** and **Power BI for visualization and reporting**.

---

## Business Problem
Employee attrition is costly and often preventable if risks are identified early.  
HR teams need visibility into:
- Which departments experience higher attrition
- Whether attrition is concentrated among specific age or tenure groups
- How performance trends evolve over time

Raw HR data alone does not answer these questions without structured processing and analytical modeling.

---

## Solution Overview
This project addresses the problem by:
1. Cleaning and standardizing raw HR data using Python
2. Engineering key workforce metrics such as age, tenure, and attrition indicators
3. Creating analytics-ready datasets for Power BI
4. Building an interactive dashboard with DAX-based KPIs for decision support

---

## Tools & Technologies
- **Python** (Pandas) – data cleaning and feature engineering  
- **Power BI** – dashboard development and visualization  
- **DAX** – KPI and attrition metric calculations  
- **Excel** – raw data source  

---

## Data Pipeline
1. Raw employee data is ingested from Excel
2. Python scripts standardize columns and handle date logic
3. Age, tenure, and attrition flags are calculated
4. Aggregated datasets are generated for reporting
5. Power BI consumes processed data for visualization

This separation ensures clean data modeling and scalable analytics.

---

## Key Metrics & Logic
The dashboard includes:
- Total, active, and exited employees
- Attrition rate and month-over-month attrition
- Department-wise attrition analysis
- Age and tenure band segmentation
- Average performance and experience metrics

