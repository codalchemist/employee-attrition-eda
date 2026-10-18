# Employee Attrition & Workforce Analytics (Python EDA)

Exploratory data analysis of the IBM HR Analytics dataset to understand why employees leave and what HR can do about it.

## Project objective
A company is experiencing employee turnover. This project identifies the factors associated with attrition (overtime, pay, age, tenure, satisfaction, role, distance from home) and turns the findings into HR recommendations.

## Dataset
- **Source:** [IBM HR Analytics Employee Attrition & Performance (Kaggle)](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
- **File:** `data/WA_Fn-UseC_-HR-Employee-Attrition.csv` (1,470 employees, 35 columns)
- **Target:** `Attrition` (Yes/No). Note: this is a fictional dataset created by IBM data scientists.

## Repository contents
| File | Description |
|---|---|
| `Employee_Attrition_EDA.ipynb` | Full analysis, code, charts and written interpretation (outputs included) |
| `EDA_Report_Employee_Attrition.pdf` | Final EDA report |
| `Presentation_Employee_Attrition.pptx` | 7-slide summary presentation |
| `data/` | Dataset |
| `figures/` | All charts exported as PNG |
| `requirements.txt` | Python dependencies |

## Analysis performed
- **Data understanding:** shape, data types, data dictionary, descriptive statistics
- **Cleaning:** no missing values or duplicates; dropped 3 constant columns and an ID column; created `Attrition_flag`, labelled satisfaction/work-life columns and age groups; logical consistency checks; IQR outlier analysis (kept, since high earners are genuine senior staff)
- **Univariate:** histograms of age, income and distance; attrition count plot
- **Bivariate:** attrition rate by department, job role, overtime and age group; box plots of income, age, distance and tenure by attrition; satisfaction and work-life-balance count plots; scatter plots
- **Multivariate:** correlation heatmap, overtime x marital-status heatmap, high-risk segment analysis
- **Statistical tests:** chi-square (categorical) and Mann-Whitney U (numeric) to check differences are not chance
- **Time series:** not applicable (the data is a single snapshot with no dates)

## Key findings
- Overall attrition is **16.1%** (237 of 1,470 employees).
- **Overtime** is the strongest signal: **30.5%** attrition with overtime vs **10.4%** without (about 2.9x).
- **Sales Representatives** (39.8%) and **Laboratory Technicians** (23.9%) have the highest attrition; Research Directors the lowest (2.5%).
- Leavers are **younger, lower paid and newer**: median income $3,202 vs $5,204, median age 32 vs 36, median tenure 3 vs 6 years. Attrition is 35.8% for ages 18-25.
- **Low job satisfaction** = 22.8% attrition vs 11.3% for very high satisfaction. Bad work-life balance = 31.2% (small group, n = 80).
- **Risk factors compound:** overtime + below-median income + under 36 gives **51.5%** attrition (69 of 134). That group is 9% of staff but 29% of all leavers.
- Distance from home is a minor factor; no single numeric variable correlates strongly with attrition (strongest |r| is 0.17).

## Recommendations
1. Control overtime and track it as an early-warning indicator.
2. Target young, early-career, below-median-income staff with mentoring and visible career paths.
3. Review junior pay in the highest-attrition roles.
4. Use low satisfaction or work-life-balance scores as a trigger for manager conversations.
5. Consider retention incentives (e.g. stock options) and review travel load.

## Limitations
Fictional dataset; single snapshot (no time dimension); association is not causation; class imbalance and some small groups; no information on why people left. A predictive model is the natural next step.

## How to run
```bash
pip install -r requirements.txt
jupyter notebook Employee_Attrition_EDA.ipynb
```
Run the notebook from this folder so the relative `data/` path works.
