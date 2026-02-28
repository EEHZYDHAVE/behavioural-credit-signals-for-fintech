# Expanding Access to "Credit Invisible" Segments

**High-Growth Underwriting: Discovering Behavioral Signals for Credit-Invisible Borrowers**

<hr>

## 1. Project Background & Industry Context

Fintech lenders pursuing rapid growth often look beyond traditional banked customers toward credit-invisible or thin-file users, individuals with limited or no formal credit history. These users, frequently younger and from non-traditional educational backgrounds, are typically excluded by legacy credit scoring systems despite being economically active.

For fintechs, lending to these segments represents a clear growth opportunity. However, the absence of reliable bureau-based data introduces uncertainty around borrower risk. Traditional demographic proxies, such as education level or marital status, are often used in place of credit history, but their effectiveness in predicting repayment behavior remains limited and inconsistent.

As a result, fintechs are increasingly pushed to explore whether behavioral information embedded in payment history can provide more reliable insight into creditworthiness than static borrower attributes.



## 2. The Problem Statement

> Our Fintech aims to capture market share by lending to **"Credit Invisible"** or **"Thin-File"** borrowers, specifically younger users and those with non-traditional educational backgrounds, who are typically rejected by legacy banks. However, aggressive expansion into these segments risks a spike in Non-Performing Loans (NPLs). The challenge is to identify alternative behavioral signals within payment history that can predict creditworthiness better than a static demographic profile.



## 3. The Business Problem

This project is grounded in a core growth-risk tension faced by fintech lenders:

**How can a fintech expand lending to credit-invisible borrowers without triggering a disproportionate increase in Non-Performing Loans (NPLs)?**

Aggressive expansion into thin-file segments can accelerate customer acquisition and portfolio growth, but reliance on weak demographic proxies may lead to poor risk selection. The central challenge is not whether to grow, but how to assess risk when traditional credit signals are absent.

Specifically, the problem is to identify alternative behavioral signals within payment history that can indicate repayment reliability more effectively than static demographic profiles alone.



## 4. Problem Questions

The following questions structure the analytical investigation and define what this project must answer.

### Q1 Establishing the Baseline
> What demographic proxies are currently used to assess creditworthiness for credit-invisible borrowers, and how well do they predict NPL outcomes?

Before introducing behavioral signals, we must first evaluate what lenders rely on today, age, education level, marital status, and measure how effectively those proxies actually predict loan performance for credit-invisible segments.

### Q2 Discovering Behavioral Signals
> What payment behaviors separate good borrowers from bad ones (e.g., consistency, frequency, partial payments)?

This is the core discovery question. It explores which observable patterns in payment activity, such as regularity, timing, partial repayments, or early signs of stress, correlate with positive or negative credit outcomes.

### Q3 Comparing Signal Quality
> Do behavioral payment signals outperform demographic proxies in explaining creditworthiness outcomes, and under what conditions?

This question tests the central hypothesis of the project in an open and honest way, leaving room for findings to go in either direction. It also asks under what conditions behavioral signals are more or less reliable, adding analytical nuance beyond a simple yes/no comparison.

### Q4 Borrower Profile Segmentation
> Which borrower profiles within the credit-invisible segment show the most predictable repayment behavior?

"Credit invisible" is not a uniform group. A 22-year-old recent graduate and a 35-year-old informal trader may both lack credit scores but behave very differently. Identifying which sub-profiles are safer to lend to makes the project directly actionable for a fintech's underwriting strategy.



## 5. Analytical Focus: Behavioral Signals vs. Demographic Proxies

Rather than starting with predefined underwriting rules, this project focuses on discovering behavioral patterns that emerge naturally from payment activity over time.

Demographic variables are first evaluated on their own merit as predictors of NPL outcomes, reflecting how credit-invisible borrowers are commonly assessed today. Their performance establishes the baseline against which behavioral signals are tested. Behavioral signals derived from payment history are then explored as potential alternatives, not assumed replacements, but candidates to be rigorously compared against observed outcomes.

This two-stage approach ensures the project remains analytically honest: if demographic proxies perform well in certain conditions, that finding is equally valuable to a fintech making risk decisions.



## 6. Interpreting Creditworthiness Through Outcomes

In this project, creditworthiness is understood in practical, portfolio-relevant terms rather than abstract credit scores. It is observed through outcomes such as:

- Missed or delayed payments
- Persistent delinquency
- Transition into non-performing loan (NPL) status

These outcomes serve as the reference point against which behavioral patterns in payment history are evaluated. The emphasis is on how borrowers behave over time, allowing patterns of consistency, volatility, or deterioration to emerge organically from the data.



## 7. Project Goal

The goal of this project is to discover and examine behavioral signals embedded within payment history that may help fintech lenders safely expand access to credit for credit-invisible borrowers.

Specifically, the project aims to:

1. Evaluate how well current demographic proxies predict NPL outcomes for credit-invisible borrowers
2. Explore payment behavior patterns that correlate with positive or negative credit outcomes
3. Compare the explanatory power of behavioral payment signals against static demographic proxies
4. Identify which borrower profiles within the credit-invisible segment show the most predictable repayment behavior
5. Provide clear, interpretable insights that can inform early-stage underwriting exploration and risk assessment

> The focus is not on building a complex predictive model, but on making behavioral risk **visible**, **understandable**, and **relevant** to real-world growth decisions.

<hr>

## Part 1 Project Plan: Do Demographic Proxies Predict NPL Outcomes for Credit-Invisible Borrowers?

### Objective
Evaluate how well traditional demographic proxies; age, education, employment type, marital status — predict loan default outcomes among credit-invisible borrowers, and establish a measurable baseline for Part 2.



### Dataset
**Source:** [Home Credit Default Risk: Kaggle](https://www.kaggle.com/competitions/home-credit-default-risk/data)

| File | Purpose |
|---|---|
| `application_train.csv` | Primary table: borrower demographics, loan details, and TARGET variable |
| `bureau.csv` | Used to identify and exclude borrowers with external credit history |
| `previous_application.csv` | Used to identify and exclude borrowers with prior Home Credit history |



### Tools
| Tool | Purpose |
|---|---|
| Google Colab | Development environment |
| Python (Pandas, NumPy) | Data loading, filtering, and manipulation |
| Matplotlib / Seaborn | Data visualization |
| SciPy | Statistical testing: Chi-square, Cramér's V, Point-biserial correlation |



### Stages

**Stage 1 Variable Classification**
Categorize all available columns into three explicit buckets before any analysis begins, pure demographic proxies, loan request characteristics, and soft stability signals. Exclude `EXT_SOURCE_1/2/3` and all building-related normalized columns and document the exclusions.

**Stage 2 Exploratory Data Analysis**
Examine distributions of key demographic variables, convert `DAYS_BIRTH` to readable age in years, and check for missing values or data quality issues that need to be addressed before analysis.

**Stage 3 Univariate Signal Evaluation**
Test each demographic proxy individually against the TARGET variable. Categorical variables are assessed using Chi-square tests and Cramér's V. Continuous variables are assessed using point-biserial correlation. Output is a ranked table of variables by signal strength, strongest to weakest.

**Stage 4 Subgroup Profiling**
Cross-tabulate key demographic combinations, age group, education level, employment type and observe how NPL rates shift across combined profiles. This produces a human-readable picture of which borrower profiles within the credit-invisible segment carry the most and least risk.

**Stage 5 Baseline Verdict**
Summarize findings in plain language: which proxies carried meaningful signal, which carried almost none, and what the combined profiles reveal. This verdict becomes the measurable baseline that Part 2 will challenge with behavioral payment signals.

---

### What This Feeds Into
The signal strength rankings and baseline NPL rates produced in Part 1 become the benchmark for Part 2, where behavioral signals from `installments_payments.csv` are tested against the same population and compared directly against these results.
