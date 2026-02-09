Loan Data Analysis Dashboard (Power BI + Dataflows+ SQL Server)

Dashboard Link: https://app.powerbi.com/view?r=eyJrIjoiM2M3YzRkODAtMGRmMi00Mjc1LWIxN2MtNTUxZDg2NjRlMjMxIiwidCI6IjIzODk2NDkwLTdlNzMtNGQ1Zi1hZjQ5LTBmMjUwMzQ5NWQ3NSJ9&pageName=32510eb46b87975932a8

Dashboard Overview

This project presents a **Loan Data Analysis Dashboard** developed using **Power BI**, with **Power BI Dataflows** as the data source. The data used in the dataflow is sourced from **SQL Server**, enabling centralized data preparation and reuse across reports.

The dashboard focuses on analyzing **loan defaults, applicant demographics, and financial risk metrics**, helping stakeholders understand credit risk and lending patterns.

The report consists of **three analytical pages**:

1. **Loan Defaulters & Overview**
2. **Applicant Demographics & Financial Profile**
3. **Financial Risk Metrics**

---

Problem Statement

Financial institutions need to assess loan performance, borrower risk, and default behavior to make informed lending decisions. This project aims to convert raw loan data into meaningful insights using **Dataflows, DAX measures, and advanced Power BI visuals**.

Using this dashboard, users can:

* Identify default trends and high-risk borrower segments
* Analyze applicant demographics and financial profiles
* Track financial risk metrics such as YOY and YTD changes
* Explore data interactively using decomposition and ribbon charts

---

Tools & Technologies Used

* **Power BI Desktop**
* **Power BI Dataflows**
* **SQL Server (Data Source for Dataflows)**
* **DAX (Data Analysis Expressions)**
* **Line Charts, Donut Charts**
* **Tree Decomposition Visual**
* **Ribbon Chart**

---

Steps Followed

Data Preparation (Dataflows)

* **Step 1:** Loan data was extracted from **SQL Server** into **Power BI Dataflows**.
* **Step 2:** Data cleaning and standardization were performed within the dataflow.
* **Step 3:** Defined column structures and data types to ensure consistent reporting.
* **Step 4:** Loaded the curated dataflow into Power BI Desktop for report development.

Report Design

* **Step 5:** Created three report pages:

  * **Loan Defaulters & Overview** – default rates, loan amounts, overview KPIs
  * **Applicant Demographics & Financial Profile** – age, income, employment, credit score analysis
  * **Financial Risk Metrics** – YOY, YTD, and risk trend analysis
* **Step 6:** Used **line charts, donut charts, ribbon charts, and tree decomposition** for advanced analysis.

---

DAX Measures Used (Copy–Paste Ready)

> This project uses **13 DAX measures**, written below exactly as they appear in the **Power BI Edit pane**.

---

Core Loan Measures

```DAX
Total Loans =
COUNT ( Loan[Loan_ID] )
```

```DAX
Total Loan Amount =
SUM ( Loan[LoanAmount] )
```

```DAX
Average Loan Amount =
AVERAGE ( Loan[LoanAmount] )
```

---

Default Analysis Measures

```DAX
Total Defaulted Loans =
CALCULATE (
    [Total Loans],
    Loan[Default_Status] = "Yes"
)
```

```DAX
Default Rate % =
DIVIDE ( [Total Defaulted Loans], [Total Loans], 0 )
```

```DAX
Total Default Loan Amount =
CALCULATE (
    [Total Loan Amount],
    Loan[Default_Status] = "Yes"
)
```

---

Income & Demographics Measures

```DAX
Average Applicant Income =
AVERAGE ( Loan[ApplicantIncome] )
```

```DAX
Loans by Employment Type =
[Total Loans]
```

```DAX
Loans by Credit Score =
[Total Loans]
```

---

Time Intelligence & Risk Measures

```DAX
YOY Loan Amount Change =
DIVIDE (
    [Total Loan Amount]
        - CALCULATE ( [Total Loan Amount], SAMEPERIODLASTYEAR ( Loan[Year] ) ),
    CALCULATE ( [Total Loan Amount], SAMEPERIODLASTYEAR ( Loan[Year] ) ),
    0
)
```

```DAX
YOY Default Loans Change =
DIVIDE (
    [Total Defaulted Loans]
        - CALCULATE ( [Total Defaulted Loans], SAMEPERIODLASTYEAR ( Loan[Year] ) ),
    CALCULATE ( [Total Defaulted Loans], SAMEPERIODLASTYEAR ( Loan[Year] ) ),
    0
)
```

```DAX
YTD Loan Amount =
TOTALYTD (
    [Total Loan Amount],
    Loan[Date]
)
```

```DAX
Median Loan Amount =
MEDIAN ( Loan[LoanAmount] )
```

---

Key Insights

* Default rates vary significantly by employment type and credit score.
* Certain demographic segments carry higher financial risk.
* YOY and YTD metrics highlight changing lending patterns over time.
* Tree decomposition helps identify root causes of financial risk.
* Ribbon charts visualize ranking changes across years and segments.

---
Conclusion

This project demonstrates strong expertise in **Power BI Dataflows**, **DAX-based financial analytics**, and **advanced visual storytelling**. By sourcing data from SQL Server via Dataflows, the solution ensures scalable, reusable, and enterprise-ready reporting.
