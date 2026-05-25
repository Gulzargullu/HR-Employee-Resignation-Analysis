# HR Employee Resignation Analysis

## 📋 Project Overview

**Objective:** Identify the root causes driving high employee attrition (16.3%) and provide actionable recommendations to reduce resignations.

**Business Problem:** The company experiences a 16.3% attrition rate (237 out of 1,470 employees) but lacks clarity on key drivers behind employee resignations. This analysis identifies major factors influencing attrition and provides data-backed recommendations.


## 📊 Key Findings

- **Low Salary is the primary driver (72.6%)**
  → Avg salary gap: $2,045/month

- **Overtime increases attrition risk by 3x**
  → 30.5% (Overtime) vs 10.4% (No Overtime)

- **Sales department has highest attrition (20.6%)**

- **Sales Representatives show highest attrition (39.8%)**

- **Early tenure employees (0–2 years) are most vulnerable (29.8%)**

## 🛠 Tools & Technologies

**Database:** PostgreSQL  
**Analysis:** Python (Pandas, NumPy)  
**Visualization:** Tableau  
**Other:** SQL, Excel  

---

## 🗄 Key SQL Analysis

- Attrition rate by department  
- Salary comparison between resigned and active employees  
- Role-wise attrition distribution  
- Tenure-based attrition segmentation  

*(Detailed SQL queries available in /SQL folder)*

---

## 📊 Analysis Approach

- Data extracted using PostgreSQL for KPI generation and segmentation  
- Data cleaning and EDA performed using Python (Pandas, Seaborn)  
- Root cause analysis performed across salary, overtime, tenure, and job roles  
- Tableau dashboard developed for visualization and insights  
- Business recommendations derived from statistical patterns and trends  

---

## 📈 Dashboard Features

- Executive KPI Dashboard (Attrition Rate: 16.3%)  
- Department-wise Attrition Analysis  
- Salary vs Attrition Comparison  
- Tenure-based Attrition Trends  
- Job Role Risk Analysis  
- Interactive filters for segmentation  

---

## 💡 Key Insights (Business View)

- Employees earning significantly below company average show highest resignation probability  
- Overtime workload is strongly correlated with attrition risk  
- Sales and HR departments require immediate retention focus  
- Early-career employees are the most critical retention group  
- Compensation and workload are the strongest attrition drivers  

---

## 💡 Recommendations

### 🔴 Immediate Actions (0–3 months)
- Adjust salary for roles below market benchmark  
- Introduce overtime compensation or compensatory time-off  

### 🟡 Short-Term Actions (3–6 months)
- Improve onboarding for first 2 years of employees  
- Strengthen manager-employee engagement process  

### 🟢 Long-Term Actions (6–12 months)
- Define clear career progression paths  
- Improve promotion transparency and internal mobility  

## 📁 Project Files

```
HR_Analysis/
├── 01_postgresql_queries.sql          # All 7 analytical SQL queries
├── 02_python_eda.ipynb                # Exploratory data analysis (9 charts)
├── 03_root_cause_scoring.ipynb        # Driver assignment & segmentation
├── 04_tableau_dashboard.twbx          # Interactive Tableau workbook
├── data/
│   ├── HR_Data_for_Tableau.csv        # Cleaned data with driver flags
│   └── resigned_employees_summary.csv # Resigned employees + primary drivers
├── README.md                          # This file
└── findings_report.pdf                # Stakeholder-ready executive summary
```

---

## 🔍 Data Source

**IBM HR Analytics Employee Attrition & Performance Dataset**
- **Size:** 1,470 employees × 35 attributes
- **Source:** Kaggle (publicly available)
- **Quality:** Clean, no missing values, validated categorical encodings
- **Timeframe:** Cross-sectional snapshot (no time series)


## 📌 Outcome

Built an end-to-end HR analytics solution covering:
- Data extraction (SQL)
- Data analysis (Python)
- Visualization (Tableau)
- Business recommendations (HR strategy)

This project demonstrates strong capability in **data analysis, KPI tracking, root cause analysis, and business storytelling.**


## 🚀 Author
Gulzar Begum
Data Analyst | SQL | Power BI | Python | Tableau



## 📝 Notes

This project demonstrates:
✅ End-to-end analytics workflow (data extraction → analysis → visualization → business recommendations)
✅ Strong business problem-solving approach beyond basic reporting
✅ Multi-tool proficiency across SQL, Python, and Tableau
✅ Clear stakeholder-focused communication through insights and recommendations
✅ Statistical thinking using correlation, segmentation, and distribution analysis
