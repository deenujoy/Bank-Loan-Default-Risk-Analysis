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

The analysis follows a structured end-to-end workflow, with each phase explained in the notebook.

**1. Problem definition**
The aim is to find which borrower and loan characteristics (grade, term, purpose, income, DTI, interest rate, state) are linked to loan default, and how risk changes across segments and over time.

**2. Data collection and loading**
The raw dataset was obtained from Kaggle ("Bank Loan Dataset") and loaded into Pandas. The size, data types and a sample of rows were checked using `shape`, `dtypes`, `head()`, `info()` and `describe()`.

**3. Data pre-processing**
- Removed empty, constant and free-text columns that carry no analytical value
- Handled missing values (median or mode filling, flags where a blank means "no event", and dropping a few rows)
- Checked and removed duplicate records
- Corrected data types and formats (term, employment length, percentage fields and invalid dates)
- Created derived columns: default flag, issue year and month, credit history in years, loan-to-income ratio, income, DTI and loan-size bands, and net return
- Detected outliers using the IQR rule and capped income at the 99th percentile for charts

**4. Exploratory Data Analysis (EDA)**
- **Univariate:** distributions of loan amount, interest rate, income and DTI, plus loan status, purpose, grade, term and home ownership
- **Bivariate:** default rate compared across grade, purpose, term, income, DTI, loan size, verification status and state
- **Multivariate:** grade-by-term heatmap, correlation heatmap and default rate by grade over the years

**5. Statistical analysis**
Group summaries, pivot tables, correlation analysis and chi-square tests were used to support the findings with numbers rather than only visual impressions.

**6. Visualization**
More than 10 visuals were created with Matplotlib and Seaborn, each with a title, labelled axes and a colour scheme chosen for readability, with a short interpretation under each chart.
