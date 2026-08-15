

# Loan Default Analysis — Power BI Report

## 📌 Overview
This project is an interactive **Power BI** report (`loan.pbix`) designed to analyze bank loan data, understand the factors influencing **loan default**, and study the demographic and financial profile of loan applicants.

The report is built on a single core table, **`Loan_default`**, and consists of **3 report pages** (1280×720 resolution).

---

## 🗂️ Data Model

Core table: **`Loan_default`**

Key columns used throughout the report (inferred from the DAX measures and visual field mappings):

| Column | Description |
|---|---|
| `LoanID` | Unique identifier for each loan |
| `LoanAmount` | Loan amount |
| `Income` | Applicant's income |
| `EmploymentType` | Employment type (employed, self-employed, unemployed, etc.) |
| `Age` / `Age Groups` | Applicant's age / age bucket (Adult, Middle Age Adult, etc.) |
| `CreditScore` / `Credit Score Bins` | Credit score and its bins (High, Medium, Low, etc.) |
| `Default` | Whether the applicant defaulted on the loan (True/False) |
| `Year` | Loan year |
| `Loan_Date_DD_MM_YYYY` | Loan date (contains an implicit date hierarchy `.[Date]`) |
| `MaritalStatus` | Marital status |
| `Purpose` | Purpose of the loan |
| `Education` | Education level |
| `Mortgage / Dependents` | Mortgage ownership / number of dependents |

---

## 📊 Report Pages

### 1️⃣ Loan Default & Overview
A general overview of loans and default rates:
- **Loan Amount by Purpose** — Total loan amount by purpose
- **Average Income by Employment Type** — Average income by employment type
- **Default Rate (%) by Employment Type** — Default rate by employment type
- **Average Loan Amount by Age Group** — Average loan value by age group
- **Default Rate (%) by Year** — Default rate trend over the years

### 2️⃣ Applicant Demographics & Financial Profile
Demographic and financial profile of applicants:
- **Median Loan Amount by Credit Score** — Median loan value by credit score
- **Donut Chart** — Proportional breakdown (by an additional Series field)
- **Total Loan (Adults) by Credit Score Bins** — Total loans for adults by credit score bins
- **Loan (Middle Age) by Mortgage / Dependence** — Middle-age group loans by mortgage/dependents
- **Number of Loans by Education Type** — Loan count by education level

### 3️⃣ Financial Risk Metrics
Advanced risk indicators:
- Two additional line charts for trend analysis
- **Ribbon Chart** — For comparing ranking and change across multiple categories
- **Decomposition Tree** — Interactive drill-down (Analyze / Explain By) to explore the root causes of default in depth

---

## 🧮 Key DAX Measures

| Measure | Purpose |
|---|---|
| `Average Income By Employment type` | Average income per employment type using `ALLEXCEPT` |
| `Average Loan by Age Group` | Average loan amount per age group |
| `Default Rate by Employment Type` | Default rate (%) per employment type |
| `Default Rate by Year` | Default rate (%) per year |
| `Loan Amount by Purpose` | Total loan amount (excluding blanks) |
| `Average Loan Amount (High Credit)` | Average loan amount for high-credit-score customers |
| `Loans by Education Type` | Loan count per education level |
| `Mediane by Credit Score bins` | Median loan amount per credit score bin |
| `Total Loan (Credit Bins)` | Total loans for adults by age and credit score bin |
| `Total Loan (Middle Age) by having mortgage` | Total loans for the middle-age group |
| `YOY Default Change` | Year-over-year percentage change in default cases |
| `YOY Loan Amount change` | Year-over-year percentage change in total loan amount |
| `YTD Loan Amount` | Year-to-date total loan amount |

> All measures are built using `CALCULATE`, `ALLEXCEPT`, `FILTER`, `AVERAGEX`, `SUMX`, `MEDIANX`, `DIVIDE`, and `DATESYTD`, making most of them respond dynamically to report filters while preserving a specific filter context (e.g., `EmploymentType` or `Year`).

---

## ⚙️ Requirements
- **Microsoft Power BI Desktop** (latest version) to open and edit `loan.pbix`
- No external data source required — the data is embedded within the report's data model

## ▶️ How to Use
1. Open `loan.pbix` with Power BI Desktop
2. Navigate between the three pages using the page tabs at the bottom
3. Use the interactive filters and the Decomposition Tree to explore default drivers in more depth
4. New DAX measures can be added or edited from the **Modeling** tab

---

## 🎯 Purpose
Helps financial/banking institutions to:
- Identify the segments most exposed to default risk
- Understand the relationship between income, employment type, credit score, and loan size
- Track default trends over time (yearly and YTD)
- Support decision-making in loan approval and risk assessment
