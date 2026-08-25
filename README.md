# Credit Risk Analysis Report

> **Project status:** Work in progress. The analysis narrative is available, while the final workbook and dashboard images are undergoing quality checks before publication.

## Project overview

This project examines a credit-risk portfolio to identify the borrower and loan characteristics most strongly associated with default. The goal is to turn the analysis into practical guidance for underwriting, affordability assessment, portfolio monitoring, and data-quality improvement.

The analysis addresses one central question:

> Which customer and loan characteristics are most strongly linked to default, and how can these insights support better lending decisions?

## Portfolio snapshot

| Metric | Result |
|---|---:|
| Loan records | 32,581 |
| Variables | 29 |
| Defaulted loans | 7,108 |
| Overall default rate | 21.8% |

`loan_status` is the target variable:

| Value | Meaning |
|---:|---|
| `0` | Non-default |
| `1` | Default |

The average interest-rate result is intentionally excluded from this summary until the handling of missing interest-rate values has passed final validation.

## Tools and techniques

- Microsoft Excel
- Excel Tables and structured formulas
- Data cleaning and quality checks
- PivotTables and PivotCharts
- KPI and dashboard design
- Descriptive and segmented risk analysis

## Dataset fields

Examples of the main source fields include:

| Category | Fields |
|---|---|
| Borrower profile | `person_age`, `person_income`, `person_home_ownership`, `person_emp_length` |
| Loan characteristics | `loan_intent`, `loan_grade`, `loan_amnt`, `loan_int_rate`, `loan_percent_income` |
| Credit history | `cb_person_default_on_file`, `cb_person_cred_hist_length` |
| Outcome | `loan_status` |

The workbook also contains additional borrower, location, debt, utilisation, and segmentation fields used for exploratory analysis.

## Analysis workflow

1. Reviewed field names, types, missing values, and unusual records.
2. Preserved the original source data on a separate worksheet.
3. Created a cleaned analysis table and derived labels for reporting.
4. Reconciled record counts and default totals against the source data.
5. Used PivotTables to compare default rates across borrower and loan segments.
6. Designed a dashboard to communicate the most decision-relevant findings.

## Data-quality findings

| Issue | Observation | Treatment for analysis |
|---|---|---|
| Missing `loan_int_rate` | Approximately 9.6% of records | Keep missing values distinct from genuine zero rates and disclose the exclusion in rate calculations |
| Missing `person_emp_length` | Approximately 2.8% of records | Retain as missing or assign an explicit unknown category for segmented reporting |
| Unusual age and employment values | Some values exceed plausible human ranges | Flag for review rather than silently deleting records |
| Similar affordability measures | `loan_percent_income` and other loan-to-income measures may overlap | Define each measure clearly before using both in the same decision rule |

These limitations do not prevent exploratory analysis, but they should be resolved before the workbook is used for automated lending decisions or predictive modelling.

## Preliminary findings

### Loan grade separates risk

Default rates increase as loan grade weakens. This indicates that loan grade is an important segmentation variable for underwriting, pricing, exception handling, and monitoring. Results for grades with small borrower counts should be interpreted cautiously.

### Previous default history is an important warning signal

Borrowers with a previous default on file show materially higher risk than borrowers without one. Previous default history should therefore be treated as a prominent review flag alongside affordability and current loan characteristics.

### Affordability pressure is associated with default

Default risk is higher among financially stretched borrowers, including customers with lower income or a larger loan burden relative to income. This supports stronger affordability checks and clearly documented thresholds.

### Home ownership adds context

Default behaviour varies across home-ownership groups. Home ownership should not be used as a standalone approval rule, but it may provide useful context when considered with income, debt burden, loan grade, and repayment history.

### Risk is concentrated rather than evenly distributed

The portfolio contains identifiable combinations of risk indicators, particularly weak loan grades, prior defaults, and affordability pressure. Targeted review of these segments is likely to be more useful than applying the same restriction to every borrower.

## Business recommendations

1. Apply enhanced review to weaker loan grades and document all policy exceptions.
2. Use previous default history as a mandatory escalation flag rather than a minor background field.
3. Define and test affordability thresholds using income, loan amount, and debt-to-income measures.
4. Create consistent low-, moderate-, high-, and very-high-risk segments for reporting and monitoring.
5. Monitor borrowers with multiple risk indicators earlier in the loan lifecycle.
6. Add validation rules for missing values, impossible ranges, and inconsistent field definitions.

These are analysis-led recommendations, not guaranteed performance forecasts. Any proposed policy should be tested on representative historical data before implementation.

## Visualisations

The final visuals will be inserted here after the workbook totals and missing-value treatment are validated.

Planned image locations:

```text
assets/credit-risk-dashboard.png
assets/default-rate-by-grade.png
assets/default-rate-by-history.png
assets/default-rate-by-home-ownership.png
```

Recommended README placement:

1. Put the complete dashboard immediately below this section.
2. Place the grade chart beside the loan-grade finding.
3. Place the previous-default chart beside the previous-default finding.
4. Place the home-ownership chart beside the home-ownership finding.

Example Markdown to use after an image is uploaded:

```markdown
![Credit risk dashboard](assets/credit-risk-dashboard.png)
```

## Repository structure

```text
Credit-Risk-Analysis-Report/
|-- README.md
|-- data/
|   `-- Credit-Risk-Analysis.xlsx
`-- assets/
    |-- credit-risk-dashboard.png
    |-- default-rate-by-grade.png
    |-- default-rate-by-history.png
    `-- default-rate-by-home-ownership.png
```

The `data` and `assets` folders will be added when the final workbook and exported visualisations pass quality checks.

## Validation checklist

- [x] Reconcile total records: 32,581
- [x] Reconcile defaults: 7,108
- [x] Reconcile overall default rate: 21.8%
- [ ] Finalise the treatment of missing interest-rate values
- [ ] Refresh and validate every PivotTable
- [ ] Confirm dashboard KPIs match the source totals
- [ ] Export and upload dashboard images
- [ ] Upload the final reviewed workbook
- [ ] Add the original dataset source link and usage terms

## Limitations

- The analysis is descriptive and does not establish causation.
- Missing values and unusual records can affect segment-level results.
- Results should be validated on additional data before being used as lending policy.
- Precise improvement targets require historical testing and should not be presented as guaranteed outcomes.

## Conclusion

The portfolio has an overall default rate of **21.8%**, with risk concentrated among identifiable borrower groups. Loan grade, previous default history, and affordability measures provide useful signals for more consistent underwriting and targeted monitoring. The next stage is to complete the workbook quality review, confirm every dashboard figure, and publish the supporting workbook and visualisations.

