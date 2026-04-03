# Credit Risk Analysis Report

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Dataset Overview](#2-dataset-overview)
3. [Data Preparation](#3-data-preparation)
4. [Key Findings](#4-key-findings)
   - [4.1 Loan Grade](#41-loan-grade-is-a-major-driver-of-default-risk)
   - [4.2 Previous Default History](#42-previous-default-history-is-a-strong-warning-sign)
   - [4.3 Affordability Pressure](#43-affordability-pressure-is-closely-linked-to-default)
   - [4.4 Home Ownership Status](#44-home-ownership-status-provides-useful-risk-context)
   - [4.5 Risk Concentration](#45-risk-is-concentrated-in-identifiable-borrower-groups)
   - [4.6 Data Quality](#46-data-quality-should-be-improved-before-operational-rollout)
5. [Business Implications](#5-business-implications)
6. [Recommendations](#6-recommendations)
7. [Conclusion](#7-conclusion)
8. [Visualisations](#8-visualisations)

---

## 1. Introduction

This report presents the findings from an analysis of the credit risk dataset, with the aim of identifying the main factors associated with loan default and highlighting actions the business can take to improve lending decisions. The analysis focused on borrower characteristics, loan features, affordability measures, and repayment outcomes to understand where risk is concentrated within the portfolio.

The central question guiding this work was:

> **Which customer and loan characteristics are most strongly linked to default, and how can the company use these insights to reduce portfolio risk while improving decision-making?**

The analysis is intended to support stakeholders in understanding the scale of current credit risk, the segments contributing most to default, and the practical steps that can be taken to strengthen risk management, underwriting, and monitoring processes.

---

## 2. Dataset Overview

The dataset contained **32,581 loan records** and **29 variables**, covering a mix of borrower demographics, financial profile, loan characteristics, and repayment outcome.

The main target variable used throughout the analysis was `loan_status`, where:

| Value | Meaning |
|-------|---------|
| `0` | Non-default |
| `1` | Default |

### Variables Included

| Category | Variables |
|----------|-----------|
| Borrower Demographics | `age`, `home_ownership`, `employment_length` |
| Financial Profile | `income`, `debt_to_income_ratio` |
| Loan Characteristics | `loan_amount`, `interest_rate`, `loan_purpose`, `loan_grade` |
| Affordability Measures | `loan_to_income_ratio`, `loan_percent_income` |
| Repayment History | `previous_default_history` |

This provided a strong basis for analysing default behaviour across different customer groups and financial conditions.

---

## 3. Data Preparation

Before conducting the analysis, the dataset was reviewed for completeness, consistency, and unusual values. This step was necessary to ensure that the findings were based on reasonable and interpretable data.

### Issues Identified

| Issue | Detail |
|-------|--------|
| Missing values — `loan_int_rate` | ~9.6% of records affected |
| Missing values — `person_emp_length` | ~2.8% of records affected |
| Unrealistic outliers | Borrower ages above 100; employment lengths above 100 years |
| Overlapping variables | `loan_percent_income` and `loan_to_income_ratio` appear to capture similar information |

> **Note:** These issues did not prevent analysis, but they should be addressed if the dataset is to be used in operational reporting or predictive modelling on a live basis. The quality review showed that while the dataset is suitable for insight generation, stronger input controls and validation checks would improve reliability in future use.

---

## 4. Key Findings

### 4.1 Loan Grade is a Major Driver of Default Risk

One of the clearest findings in the dataset was the relationship between loan grade and default. Default rates rose sharply as loan grade worsened.

| Loan Grade | Approx. Default Rate |
|------------|----------------------|
| A | ~10% |
| B | Low–moderate |
| C–D | Moderate–high |
| E–F | High |
| G | ~98% |

This is a very strong separation in performance. It shows that the grade system is already capturing meaningful differences in borrower quality and credit risk. It also suggests that the business has an opportunity to make more structured use of loan grades in approval decisions, exception handling, pricing, and post-approval monitoring.

The scale of difference between the best and worst grades is particularly important. A Grade G borrower is many times more likely to default than a Grade A borrower, meaning that high-risk grades contribute disproportionately to portfolio losses.

---

### 4.2 Previous Default History is a Strong Warning Sign

Borrowers with a previous default on file showed significantly worse repayment performance than customers with no prior default history. This was one of the **strongest behavioural signals** in the dataset.

This finding aligns with the broader principle that past repayment behaviour is often a strong indicator of future credit performance. Customers who have already demonstrated difficulty repaying credit obligations appear to present a substantially higher risk of defaulting again.

> **Business Implication:** Prior default history should not be treated as a minor background variable. It should instead be considered a **core risk flag** within the underwriting process. Applications from customers with a previous default record should receive more careful review, and where appropriate, tighter lending limits or enhanced affordability checks.

---

### 4.3 Affordability Pressure is Closely Linked to Default

The analysis showed that repayment risk is strongly associated with financial pressure, particularly among borrowers with:

- Lower income
- Higher debt-to-income ratios
- Higher loan-to-income ratios

This suggests that affordability plays a central role in repayment outcomes. Borrowers who are already stretched relative to their income are more vulnerable to missing payments and falling into default.

This is especially important because it points to a **controllable area** for the business. While external economic conditions may affect borrowers, the company can reduce exposure by strengthening affordability checks during the approval process.

The findings also suggest that the size of the loan relative to a borrower's income matters significantly. Larger loans may be suitable for some applicants, but for lower-income borrowers or those carrying higher debt burdens, the same loan size may represent far greater risk.

---

### 4.4 Home Ownership Status Provides Useful Risk Context

Another meaningful finding was the difference in default rates by home ownership status. Borrowers in **rented accommodation had higher default rates** than those who owned a home or had a mortgage.

This does not mean home ownership alone should determine lending decisions. However, it does appear to act as a useful proxy for financial stability or resilience. Renters may face greater financial pressure, less wealth protection, or fewer buffers against income shocks than homeowners.

As a result, home ownership should be viewed as a **contextual risk factor**. When combined with low income, high debt burden, or prior default history, it may help identify customers who need closer review.

---

### 4.5 Risk is Concentrated in Identifiable Borrower Groups

A key strategic finding from the analysis is that default is **not evenly distributed** across the portfolio. Instead, it is concentrated within particular segments, especially borrowers with combinations of:

- Weak loan grades
- Prior defaults
- Low affordability
- High financial stress
- Rented housing status

> **Strategic Takeaway:** The company does not need to apply blanket tightening across the full portfolio. A more targeted approach would likely be more effective. By focusing policy changes on the riskiest segments, the business can reduce default exposure without unnecessarily restricting lending to stronger customers.

---

### 4.6 Data Quality Should be Improved Before Operational Rollout

Although the analysis produced clear and useful findings, a number of data quality issues were identified that would need to be addressed before using the dataset in an automated or production-based decision environment.

**Main concerns:**
- Missing interest rate values
- Missing employment length values
- Unrealistic outliers in age and employment length
- Overlapping variables measuring similar affordability concepts

> These issues do not invalidate the analysis, but they do reduce confidence in any system that would rely on the data for repeatable operational decisions. Stronger field validation, completeness checks, and outlier controls should be introduced as part of future data governance improvements.

---

## 5. Business Implications

The findings show that credit risk in this portfolio is shaped primarily by three broad factors:

```
1. Loan quality (grade)
2. Repayment history (prior defaults)
3. Affordability pressure (income, DTI, LTI)
```

The business implication is not that all lending should become more restrictive. Instead, the analysis supports a **more selective and segmented strategy**:

- Lower-risk customers may continue to be approved efficiently
- Higher-risk customers can be identified earlier and assessed using tighter criteria

This approach would help the business:

- Reduce default exposure
- Improve consistency in approval decisions
- Prioritise collections and monitoring resources more effectively
- Improve overall portfolio quality without applying blunt restrictions across the whole customer base

---

## 6. Recommendations

### 6.1 Introduce Stricter Review Rules for Weaker Loan Grades

The company should use loan grade more actively in decision-making. Lower grades (especially **E to G**) should trigger enhanced review or require additional justification before approval.

**Expected measurable outcomes:**

| Metric | Expected Impact |
|--------|----------------|
| Approvals in weakest grades | Reduce by 10–20% |
| Default in those segments | Reduce by 5–15% |
| Overall portfolio default rate | Improve by ~1–3 percentage points |

---

### 6.2 Make Previous Default History a Mandatory Escalation Trigger

Applications from borrowers with prior defaults should be automatically flagged for deeper review.

**Expected measurable outcomes:**

| Metric | Expected Impact |
|--------|----------------|
| Exposure to repeat-defaulter segments | Reduce by 15–25% |
| Defaults from prior-default customers | Lower by 10–20% |
| Collections & monitoring allocation | Improved focus |

---

### 6.3 Strengthen Affordability Checks Using DTI and LTI Thresholds

Affordability measures should be used more explicitly in approval rules. Borrowers with high debt-to-income or high loan-to-income levels should be subject to tighter controls.

**Expected measurable outcomes:**

| Metric | Expected Impact |
|--------|----------------|
| Default among financially stretched borrowers | Reduce by 8–15% |
| Loan quality in lower-income segments | Improved |
| Losses driven by poor affordability assessment | Reduced |

---

### 6.4 Create a Formal Risk Segmentation Framework

Borrowers should be grouped into clear risk categories based on combinations of loan grade, affordability, prior default history, and key borrower profile indicators.

| Segment | Description |
|---------|-------------|
|  Low Risk | Strong grade, no prior defaults, solid affordability |
|  Moderate Risk | Mixed signals; standard review applies |
|  High Risk | Multiple risk indicators present |
|  Very High Risk | Weak grade, prior default, poor affordability |

**Expected measurable outcomes:**
- Improve consistency in lending decisions
- Reduce manual review time for low-risk applications by 15–30%
- Improve focus on high-risk cases, leading to earlier intervention

---

### 6.5 Apply Earlier Monitoring to Vulnerable Borrower Groups

Borrowers with multiple risk signals should be monitored more closely after approval, especially in the early stages of the loan.

**Expected measurable outcomes:**
- Improve early arrears intervention
- Reduce progression from missed payment to full default
- Strengthen recovery performance in the highest-risk segments

---

### 6.6 Improve Data Quality Controls

Before the analysis is used operationally, input validation and reporting standards should be strengthened.

**Expected measurable outcomes:**

| Metric | Target |
|--------|--------|
| Missing-field rates | Reduce to below 2% |
| Dashboard & scorecard confidence | Improved |
| Readiness for predictive modelling | Stronger foundation |

---

## 7. Conclusion

This analysis shows that loan default risk is substantial within the portfolio, with an **overall default rate of 21.8%**. More importantly, the risk is not spread evenly — it is concentrated in identifiable borrower groups, particularly those with:

- Weaker loan grades
- Previous default history
- Stronger signs of affordability stress

The findings suggest that the business can improve portfolio performance by focusing on **targeted interventions** rather than broad restrictions. Stronger use of loan grade, tighter treatment of prior-default borrowers, more rigorous affordability checks, and clearer risk segmentation would all help reduce credit losses while preserving a more balanced lending strategy.

> **Summary:** The dataset provides clear evidence that better segmentation and more focused credit controls could support lower default rates, improved decision consistency, and stronger portfolio quality over time.

---

## 8. Visualisations

### 8.1 Dashboard

> 📊 **[Dashboard Placeholder]**
>
> _Insert interactive dashboard here (e.g. Power BI embed, Tableau Public link, or Streamlit app)._
>
> **Suggested panels:**
> - Overall default rate (KPI card — 21.8%)
> - Default rate by loan grade (bar chart)
> - Default rate by prior default history (grouped bar)
> - Default rate by home ownership status (pie / bar)
> - Debt-to-income distribution by default outcome (box plot or histogram)
> - Risk segment distribution across portfolio (stacked bar)

---

### 8.2 Spreadsheet Data

> 📋 **[Spreadsheet Placeholder]**
>
> _Attach or link the underlying data workbook here (e.g. Excel / Google Sheets)._
>
> **Suggested tabs:**
> - `Raw Data` — cleaned dataset (32,581 records)
> - `Default by Grade` — summary table of default rates per loan grade
> - `Segment Summary` — borrower counts and default rates by risk segment
> - `Affordability Metrics` — DTI / LTI breakdowns by default status
> - `Recommendations Tracker` — measurable outcomes per recommendation

---

*Report prepared for internal stakeholder review. Data sourced from the credit risk loan dataset (32,581 records, 29 variables).*


