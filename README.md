# Bank Loan Default Risk Analysis (Python)

An end-to-end exploratory data analysis (EDA) of consumer loan data, built in Python and Jupyter Notebook. The project cleans a raw lending dataset and investigates which borrower and loan characteristics are linked to **loan default**, using `groupby`, pivot tables, correlation analysis, statistical tests and 15 visualizations, each with a written interpretation.

> Final project for the AI-Driven Data Analytics Program.

---

## Problem Statement

Which borrower and loan characteristics (credit grade, term, purpose, income, debt-to-income ratio, interest rate, state) are associated with loan default (*Charged Off*), and how does credit risk vary across segments and over time? The goal is to find where a lender is most exposed and what could be done to reduce losses.

## Domain

Finance: consumer lending and credit risk. Default analysis supports credit policy, risk-based pricing, portfolio monitoring and loss forecasting.

## Dataset

- **Source:** Kaggle, [Bank Loan Dataset](https://www.kaggle.com/datasets/puneetpainuly/bank-loan-dataset) by Puneet Painuly (Lending Club case study data)
- **Period:** loans issued June 2007 to December 2011
- **Size:** 39,717 rows and 111 columns (raw); 39,644 rows and 51 columns (after cleaning)
- **Target:** `loan_status` (*Fully Paid*, *Charged Off*, *Current*), converted to a default flag for completed loans

The raw file is included unchanged. Please check the original Kaggle page for the dataset's licence and terms of use.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Python 3 | Main programming language |
| Jupyter Notebook (Anaconda) | Code, charts and explanations in one document |
| Pandas, NumPy | Data loading, cleaning, grouping, pivot tables and calculations |
| Matplotlib, Seaborn | Visualizations |
| SciPy | Chi-square tests of association |

## Project Workflow

1. **Data loading and inspection:** shape, data types, `head()`, `info()`, `describe()` and a missing-value check on all 111 columns
2. **Pre-processing:**
   - Removed 54 empty columns, 9 single-value columns and 6 free-text columns
   - Handled missing values (median or mode fill, and 0/1 flags where a blank means "no event")
   - Checked for duplicates
   - Converted text to numbers and dates, and corrected 90 credit-line dates read in the wrong century
   - Created derived columns: default flag, issue year and month, credit history, loan-to-income ratio, income, DTI and loan-size bands, and net return
   - Flagged income outliers with the IQR rule and capped income at the 99th percentile for charts
3. **Exploratory data analysis:** univariate, bivariate and multivariate analysis
4. **Pivot tables:** five pivot tables (tables only) comparing default rate, interest rate, loan counts and net return across two variables at once
5. **Visualizations:** 15 charts (histograms, bar charts, pie chart, box plots, line charts, scatter plot and heatmaps) in one teal and orange colour theme, each followed by a written interpretation
6. **Statistical testing:** chi-square tests for the link between default and categorical variables
7. **Insights, conclusion and recommendations**

## Key Insights

Default rate is the share of completed loans (Fully Paid or Charged Off) that were Charged Off. The overall rate is **14.4%** across 38,504 completed loans.

1. **Credit grade is the strongest risk signal.** Default rises from about 5.9% for grade A to about 33% for grades F and G.
2. **60-month loans default far more than 36-month loans** (25.2% vs 10.9%), yet they carry only a slightly higher interest rate for the same grade.
3. **Small business loans are the riskiest purpose** (26.7%), while wedding, major purchase and car loans are the safest (about 10%).
4. **Lower income, larger loans and higher DTI mean higher default.** Borrowers earning under $30K default at 18.0% versus 10.8% above $100K.
5. **Interest rate is the numeric variable most linked to default** (correlation about 0.21), so lenders were already charging more for riskier loans.
6. **Risk varies by state and by year.** Among states with 300+ completed loans, Nevada (22.6%) is the highest and Texas (11.6%) the lowest. Default fell from 18.0% for 2007 loans to 12.4% for 2009 and rose to 15.7% for 2011.
7. **Verified income did not mean lower default** (16.7% verified vs 12.6% not verified), probably because riskier or larger applications are verified more often.
8. **Riskier grades still earned more on average** before funding and servicing costs, because high interest compensated for defaults.

## Recommendations

- Tighten approval or add a risk premium for 60-month loans in grades D to G
- Review small business lending with lower limits, extra documentation or collateral
- Apply loan size and DTI limits for lower-income applicants
- Monitor state-level and issue-year risk and adjust pricing early
- Do not treat income verification as a safeguard on its own

## Limitations

- All 1,140 *Current* loans are 60-month loans from 2011 and are excluded from default rates, so the 60-month and 2011 rates may change as those loans finish.
- 73 rows with no last payment date (almost all early charge-offs) were dropped, so the default rate is very slightly understated (14.4% instead of about 14.6%).
- Results show association, not causation. Net return ignores funding cost, servicing cost and timing of cash flows.
- Some groups are small (for example grade G and some states and purposes), so their rates are less reliable.

## Repository Structure

```
bank-loan-default-risk-analysis/
│
├── README.md
├── loan_default_analysis_full_project.ipynb   # Full analysis notebook
├── loan.csv                                   # Raw dataset (unchanged)
└── loan_cleaned.csv                           # Cleaned dataset created by the notebook
```

## How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/bank-loan-default-risk-analysis.git
   cd bank-loan-default-risk-analysis
   ```
2. Install the requirements:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy jupyter
   ```
3. Start Jupyter and open the notebook:
   ```bash
   jupyter notebook
   ```
4. Keep `loan.csv` in the same folder as the notebook (or change the path in the loading cell), then choose **Kernel > Restart & Run All**.

Some cells change the data and should only run once, so always run the notebook from the top.

## Author

**<Deenu>**
Data / Business Analyst | Finance and Banking
