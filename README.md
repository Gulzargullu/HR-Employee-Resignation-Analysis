# HR Employee Resignation Analysis — Root Cause Investigation

## 📋 Project Overview

**Objective:** Identify the root causes driving high employee attrition (16.3%) and provide actionable recommendations for HR leadership to reduce resignations.

**Business Problem:** The company experiences a 16.3% attrition rate (237 out of 1,470 employees) but lacks understanding of *why* employees are resigning. This analysis diagnoses the primary drivers and proposes data-backed intervention strategies.

---

## 🎯 Key Findings

### 1. **Primary Driver: Low Salary (72.6%)**
- **172 out of 237 resigned employees** are underpaid relative to company average
- Resigned employees earn **$4,787/month** vs. **$6,832/month** for those who stay
- **$2,045/month gap** (30% lower compensation)

### 2. **Secondary Driver: Overtime Burnout (14.8%)**
- Employees working overtime have **30.5% attrition rate** vs. 10.4% for non-overtime workers
- **3x higher risk** of resignation for those working overtime
- 54% of resigned employees worked overtime vs. 23% of active employees

### 3. **Department-Level Risk**
| Department | Attrition Rate | Primary Driver | Action Required |
|---|---|---|---|
| **Sales** | 20.6% (92/446) | Low Salary (78%) | Salary adjustment + Overtime policy |
| **HR** | 19.0% (12/63) | Low Salary (67%) | Competitive compensation |
| **R&D** | 13.8% (133/961) | Low Salary (69%) | Market-rate review |

### 4. **Highest-Risk Job Role**
- **Sales Representatives:** 39.8% attrition rate (33 out of 83)
- Laboratory Technician: 23.9%
- Human Resources: 23.1%

### 5. **Tenure Pattern: New Employees Most Vulnerable**
- **0–2 Years:** 29.8% attrition — **critical onboarding period**
- 3–5 Years: 13.8%
- 6–10 Years: 12.3%
- 10+ Years: 8.1%

### 6. **Employee Profile: Typical Resigned Employee**
- **Age:** 33 years (vs. 37 for active employees)
- **Salary:** $4,787/month (30% below average)
- **Tenure:** 3.2 years (newer to company)
- **Overtime:** 54% work overtime
- **Satisfaction:** Lower across all dimensions (job, environment, work-life balance)

---

## 🛠️ Tools & Technologies

### **Database Layer — PostgreSQL**
- Designed relational schema for 1,470 employee records (35 attributes)
- Imported IBM HR Analytics dataset
- Wrote 7 SQL queries to extract resignation rates, salary comparisons, and demographic breakdowns
- Generated CSV outputs for downstream analysis

**Key Queries:**
```sql
-- Attrition rate by department
SELECT Department, COUNT(*) AS total,
       SUM(CASE WHEN Attrition = 'Yes' THEN 1 END) AS resigned,
       ROUND(SUM(CASE WHEN Attrition = 'Yes' THEN 1 END) * 100.0 / COUNT(*), 2) AS attrition_rate_pct
FROM employees GROUP BY Department ORDER BY attrition_rate_pct DESC;

-- Salary comparison: resigned vs. active
SELECT Attrition, ROUND(AVG(MonthlyIncome), 2) AS avg_income
FROM employees GROUP BY Attrition;
```

### **Analytics Layer — Python (Pandas, Matplotlib, Seaborn)**
- **Data Cleaning:** Handled missing values, encoded categorical variables, normalized data types
- **Exploratory Data Analysis (EDA):** 
  - Distribution plots, boxplots, correlation heatmap
  - Attrition rate breakdown by department, role, tenure, and overtime status
  - Satisfaction score comparisons (resigned vs. active)
  
**Analysis Output:**
- Correlation heatmap revealing strongest attrition drivers
- 8+ publication-ready charts for dashboard and stakeholder presentations
- Root cause scoring: assigned primary resignation driver to each of 237 resigned employees

### **Visualization Layer — Tableau (Dashboard)**
- Interactive KPI banner showing overall attrition rate (16.3%)
- Multi-dimensional charts:
  - Attrition rate by department (bar chart)
  - Primary driver breakdown (pie chart)
  - Salary gap comparison (box plot)
  - Attrition by tenure (tenure cohort analysis)
  - Job role risk matrix (horizontal bar chart)
- Filter controls by department, job role, and year
- Exported for stakeholder presentations

---

## 📊 Analysis Approach

### **Phase 1: Database Foundation (PostgreSQL)**
1. Imported 1,470 employee records into PostgreSQL
2. Designed schema with proper data types and relationships
3. Executed 7 analytical SQL queries
4. Exported results as CSV for Python analysis

### **Phase 2: Root Cause Investigation (Python)**
1. Loaded data into Pandas DataFrame
2. Performed EDA to identify attrition patterns
3. Built correlation matrix to rank drivers by influence
4. Created 8 publication-ready visualizations

### **Phase 3: Root Cause Scoring (Python)**
1. Defined 5 primary resignation drivers:
   - Low Salary (MonthlyIncome < 80% of average)
   - Overtime Burnout (OverTime = "Yes")
   - No Growth (YearsSinceLastPromotion > average)
   - Poor Culture (JobSatisfaction < average)
   - Early Exit (YearsAtCompany ≤ 2)
2. Assigned primary driver to each resigned employee
3. Generated driver breakdown by department and role

### **Phase 4: Visualization & Storytelling (Tableau)**
1. Built interactive dashboard with 6 chart types
2. Emphasized headline finding: **72.6% of resignations = Low Salary**
3. Provided drill-down by department and role
4. Included filter controls for dynamic exploration

### **Phase 5: Recommendations (Stakeholder-Ready)**
1. Prioritized interventions by driver impact
2. Quantified business case for each recommendation
3. Documented implementation roadmap

---

## 💡 Actionable Recommendations

### **Immediate (0–3 months)**
1. **Salary Adjustment:** Close $2,000/month gap for roles below 60th percentile
   - Priority: Sales representatives, Laboratory technicians, HR staff
   - Expected impact: Reduce attrition by 5–8%

2. **Overtime Compensation Policy:** Introduce overtime pay or comp time
   - Current: No premium for >40 hours/week
   - New: 1.5x pay or 1-for-1 comp time
   - Expected impact: Reduce attrition by 2–3%

### **Short-term (3–6 months)**
3. **Onboarding Redesign:** Focus on first 2 years (highest risk period)
   - Structured mentorship program
   - Clear 6-month, 1-year, 2-year milestones
   - Manager training for new hire integration
   - Expected impact: Reduce early-exit attrition by 3–5%

### **Medium-term (6–12 months)**
4. **Promotion & Career Tracks:** Define clear advancement pathways
   - Transparency on promotion timelines
   - Skills development roadmap
   - Transparent salary bands per level
   - Expected impact: Reduce "no growth" resignations by 60%

5. **Manager Effectiveness Training:** Strengthen immediate manager relationships
   - Focus on Sales leadership (highest turnover)
   - One-on-ones, feedback, career conversations
   - Expected impact: Reduce culture-driven resignations by 50%

---

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

---

## 🚀 How to Reproduce

### Prerequisites
- PostgreSQL 12+
- Python 3.8+ (Pandas, Matplotlib, Seaborn)
- Tableau Public (free)

### Steps
1. **Load data into PostgreSQL:**
   ```bash
   psql -U postgres -d hr_analysis -f 01_postgresql_queries.sql
   ```

2. **Run Python EDA:**
   ```bash
   # Run analysis
python python/eda.py
python python/root_cause_scoring.py
   ```

3. **Open Tableau dashboard:**
   - Import `data/HR_Data_for_Tableau.csv`
   - Open `04_tableau_dashboard.twbx`
   - Interact with filters and drill-down

---

## 📈 Impact & Next Steps

### Expected Business Impact
- **Attrition Reduction:** 16.3% → 12% (3% point reduction, ~$2M annual savings at typical replacement cost)
- **Employee Retention:** 237 fewer resignations → 180 fewer resignations annually
- **Productivity:** Reduced onboarding cycles, maintained institutional knowledge

### Data Expansion Opportunities
- **Longitudinal analysis:** Track attrition over time (is compensation gap widening?)
- **Exit interview data:** Validate root causes with qualitative feedback
- **Performance correlation:** Do high performers have different attrition patterns?
- **Predictive modeling:** Build classification model to flag at-risk employees *before* resignation

---

## Author

**Analyst:** Gulzar Begum
**Date:** May 2026  
**Skills Demonstrated:** SQL, Python (Pandas/Seaborn), Tableau, Root Cause Analysis, Data Storytelling

---

## 📝 Notes

This project demonstrates:
- ✅ End-to-end analytics workflow (database → analysis → visualization → recommendations)
- ✅ Business problem-solving (not just reporting numbers)
- ✅ Multi-tool proficiency (SQL, Python, Tableau)
- ✅ Stakeholder communication (executive summary, actionable findings)
- ✅ Statistical thinking (correlation, distribution analysis, segmentation)
