# IT Asset Risk & Data Quality Analytics

## Overview

This project analyzes IT asset data from multiple sources to identify
data quality issues, inconsistencies and devices requiring further
investigation.

The project combines data integration, exploratory data analysis,
statistical analysis and risk classification to answer the following
question:

> Which computers require attention and why?

## Objectives

The main objectives of the project are:

- identify data quality issues across IT asset sources;
- detect inconsistencies between systems;
- quantify the prevalence of different data quality problems;
- identify factors associated with higher device risk;
- classify devices into Low, Medium and High Risk categories;
- prioritize data quality problems for IT teams;
- develop a monitoring dashboard.

## Data Sources

The analysis combines information from multiple IT asset sources,
including:

- SharePoint
- Primend
- device logs
- location information
- login activity
- hardware and warranty information

The data integration process creates a consolidated dataset for
analysis.

## Methodology

The project follows the following workflow:

1. Data loading and preparation
2. Data cleaning and standardization
3. Data integration
4. Exploratory Data Analysis
5. Data quality assessment
6. Risk indicator creation
7. Statistical analysis
8. Risk scoring
9. Logistic Regression analysis
10. Model evaluation
11. Risk prioritization
12. Dashboard development
13. Recommendations

## Risk Indicators

The following data quality indicators were created:

- `missing_login_data`
- `missing_from_sharepoint`
- `missing_from_primend`
- `inactive_device`
- `location_mismatch`

These indicators are combined into a risk score used to classify
devices into Low, Medium and High Risk categories.

## Key Findings

The analysis identified 141 computers:

| Risk Level | Computers | Percentage |
|------------|-----------|------------|
| Low | 41 | 29.1% |
| Medium | 60 | 42.6% |
| High | 40 | 28.4% |

The most widespread data quality issue was location mismatch.

However, the strongest association with High Risk was observed for
devices missing from Primend.

### Main Risk Drivers

| Risk Indicator | Odds Ratio |
|----------------|------------|
| Missing from Primend | 27.24 |
| Missing login data | 6.81 |
| Inactive device | 2.02 |
| Missing from SharePoint | 1.34 |
| Location mismatch | 1.15 |

This demonstrates that the most common data quality problem is not
necessarily the most important risk driver.

## Statistical Analysis

The relationship between asset status and risk level was statistically
significant:

- Chi-square = 221.89
- p-value < 0.001
- Cramér's V = 0.887

This indicates a strong association between asset status and the
constructed risk classification.

## Risk Classification

A Logistic Regression model was used to examine the relationship
between data quality indicators and the constructed High Risk category.

Model performance on the test set:

| Metric | Score |
|--------|-------|
| Accuracy | 94.4% |
| Precision | 100.0% |
| Recall | 80.0% |
| F1-score | 88.9% |
| ROC-AUC | 98.1% |

A classification threshold of 0.30 was selected based on the
precision-recall trade-off.

## Important Methodological Note

The High Risk label is constructed from the same data quality
indicators used as model features.

Therefore, the Logistic Regression model should be interpreted as a
statistical validation of the relationship between the indicators and
the constructed High Risk classification rather than as an independent
prediction of future operational risk.

An independently observed future outcome would be required to evaluate
true predictive performance.

## Dashboard

The project includes a monitoring dashboard covering:

- overall risk distribution;
- data quality issues;
- risk drivers;
- model performance.

The dashboard can serve as a foundation for future monitoring once
historical data snapshots become available.

## Recommendations

The analysis suggests several priorities for IT teams:

1. Investigate devices missing from Primend.
2. Improve collection of login activity data.
3. Validate location mapping rules.
4. Review High Risk devices, especially those affected by multiple
   data quality issues.
5. Establish continuous monitoring of data quality metrics.
6. Use the risk model as a decision-support tool rather than a
   replacement for IT investigation.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Scikit-learn
- Jupyter Notebook

## Project Structure

```text
IT-Asset-Risk-Analytics/
│
├── DataExploration.ipynb
├── README.md
├── requirements.txt
├── data/
│   └── README.md
└── images/
    └── dashboard.png
