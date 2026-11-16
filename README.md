# Bank Loan Default Risk Analysis

An end-to-end exploratory data analysis (EDA) of consumer loan data, built in Python and Jupyter Notebook. The project cleans a raw lending dataset and investigates which borrower and loan characteristics are linked to **loan default**.

> Final project for the AI-Driven Data Analytics Program.

---

## Problem Statement

Which borrower and loan characteristics (credit grade, term, purpose, income, debt-to-income ratio, interest rate, state) are associated with loan default (*Charged Off*), and how does credit risk vary across segments and over time? The goal is to identify where a lender is most exposed and what could be done to reduce losses.

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
| Jupyter Notebook (Anaconda) | Code and explanations in one document |
| Pandas, NumPy | Data loading, cleaning, grouping and calculations |


## Methodology

1. **Data loading and overview:** shape, data types, `head()`, `info()`, `describe()` and a missing-value check on all 111 columns
2. **Pre-processing:**
   - Removed 54 empty columns, 9 single-value columns and 6 free-text columns
   - Handled missing values (median or mode fill, 0/1 flags where a blank means "no event")
   - Checked for duplicates
   - Converted text to numbers and dates, and corrected 90 credit-line dates read in the wrong century
   - Created derived columns: default flag, issue year and month, credit history, loan-to-income ratio, income, DTI and loan-size bands, and net return
   - Flagged income outliers with the IQR rule and capped income at the 99th percentile for charts
