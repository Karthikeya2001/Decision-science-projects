# 🛒 Causal Framework for A/B Testing: From EDA to Treatment Effect Estimation

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-Logistic%20Regression-orange)
![SciPy](https://img.shields.io/badge/SciPy-Hypothesis%20Testing-8CAAE6?logo=scipy&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 👥 Who Should Read This

| Audience | What to focus on |
|---|---|
| **Business Analysts** | Business Context, Key Findings, Business Recommendation |
| **Hiring Managers** | Notebook Flow, Skills Demonstrated, Key Takeaway |
| **Technical Reviewers** | Methodologies, Why Each Method Was Used, Reproducibility |

---

## 📌 Project Overview

This project simulates a real-world **Product Analytics** workflow used to evaluate whether a new product feature should be launched.

Using a synthetic Quick Commerce dataset, it assesses the impact of a **One-Click Checkout** experience on user conversion through a structured experimentation framework combining:

- Exploratory Data Analysis (EDA)
- Experiment Validation
- Hypothesis Testing
- Two-Proportion Z-Test
- Logistic Regression
- Treatment Effect Analysis
- Root Cause Analysis (RCA)

> **Core Question:** Did the feature create a meaningful and statistically reliable improvement — and should the company roll it out?

---

## 🏪 Business Context

A Quick Commerce platform introduces a **One-Click Checkout** feature designed to reduce purchase friction. The Product Team wants to understand:

- Does the new checkout experience increase conversions?
- Is the uplift statistically significant?
- Can the uplift be causally attributed to the feature?
- What factors drive conversion behaviour?
- Are some user segments affected differently?

---

## 🔄 Project Workflow

```
Business Problem
       ↓
Synthetic Data Generation
       ↓
EDA & Data Quality Checks
       ↓
Experiment Validation
       ↓
Hypothesis Testing
       ↓
Two-Proportion Z-Test
       ↓
Covariate-Adjusted Logistic Regression
       ↓
Odds Ratio Interpretation
       ↓
Segment-Level Analysis
       ↓
Business Recommendation
```

---

## 📓 Notebook Flow

Here is what to expect when you open the notebook end-to-end:

1. **Project setup** — environment notes and library imports
2. **Data ingestion & EDA** — baseline conversion rates, sample sizes, and balance checks
3. **Metric definition & pre-processing** — define conversion events and prepare the analysis-ready dataset
4. **Randomization checks** — covariate balance diagnostics to validate experiment integrity
5. **Primary causal analysis** — A/B test comparisons using adjusted estimators
6. **Robustness checks** — alternative estimators, sensitivity to covariates, and sample splits
7. **Heterogeneous treatment effect (HTE) analysis** — identify high-impact user segments
8. **Summary & recommendations** — business interpretation and rollout guidance

> Key assumptions and limitations are flagged inline within analysis cells (e.g., unobserved confounding, data quality caveats). All steps are reproducible — re-run each cell to validate results.

---

## 📊 Dataset

Since production experimentation datasets are rarely publicly available, a synthetic dataset was created to mimic a real Quick Commerce checkout funnel.

| Feature | Description |
|---|---|
| `user_id` | Unique user identifier |
| `group` | Control vs Treatment |
| `converted` | Conversion outcome (binary) |
| `cart_value` | Basket value |
| `time_spent_min` | Session duration in minutes |
| `device_type` | Desktop / Mobile / Tablet |
| `user_type` | New vs Returning User |

> The synthetic data intentionally includes behavioural patterns and confounding factors commonly encountered in product experimentation.

---

## 🧪 Methodologies

### 1. Exploratory Data Analysis

- Data profiling & missing value assessment
- Distribution analysis & outlier detection
- Segment and correlation analysis

> **Objective:** Understand behavioural patterns and identify potential conversion drivers.

---

### 2. Experiment Validation & Randomization Checks

Before evaluating treatment impact, the experiment was checked for integrity:

- Control vs Treatment group comparison
- Group distribution review
- Conversion baseline analysis
- Covariate balance diagnostics and confounder inspection

> **Why:** Proper randomization avoids selection bias and ensures group comparability — the foundation of credible causal claims. Any imbalance detected here informs the need for adjustment techniques downstream.

---

### 3. Hypothesis Testing

| Hypothesis | Statement |
|---|---|
| **H₀ (Null)** | The One-Click Checkout feature has *no* impact on conversion. |
| **H₁ (Alternative)** | The One-Click Checkout feature *improves* conversion. |

---

### 4. Two-Proportion Z-Test

Used to determine whether conversion differences between Control and Treatment groups are statistically significant.

**Outputs:**
- Conversion Rates
- Absolute & Relative Uplift
- Z Statistic
- P-Value

> **Why:** A/B testing provides a randomised-control framework to directly compare treatment vs control. It is the backbone for measuring immediate differences in conversion rates and determining whether observed uplift exceeds random variation.

---

### 5. Logistic Regression (Statsmodels)

A multivariable logistic regression model was built to evaluate treatment effects while controlling for confounders.

**Variables included:**
- Treatment Exposure
- Cart Value
- Session Duration
- Device Type
- User Type

> **Why:** Regression adjustment reduces variance from baseline covariates and corrects for any residual imbalance between groups — producing more reliable causal effect estimates than a raw rate comparison alone.

---

### 6. Odds Ratio Interpretation

Model coefficients were translated into Odds Ratios to improve business interpretability.

**Questions addressed:**
- How much more likely is a treated user to convert?
- Which factors increase or decrease conversion likelihood?
- Which variables have the strongest influence on conversion?

---

### 7. Root Cause Analysis & Heterogeneous Treatment Effects (HTE)

Beyond statistical significance, additional analyses investigated:

- *Why* conversion changed
- *Which* variables influenced outcomes most
- Whether treatment effects varied across user segments (e.g., by device, user type, or behaviour)

> **Why:** Identifying segments with differential impact enables targeted rollouts, personalisation strategies, and improved ROI — moving the analysis from "did it work?" to "for whom did it work best?"

---

## 📈 Key Findings

### ✅ Treatment Effect
The One-Click Checkout feature produced a **statistically and practically significant increase** in conversion rate.

### 🔍 Conversion Drivers
After controlling for user and session characteristics:
- Treatment exposure remained a **meaningful predictor** of conversion.
- Cart value showed a **significant negative relationship** with conversion.
- Device type and user type exhibited limited explanatory power within the current dataset.

### 👥 Segment Insights
Segmentation analysis was performed to evaluate whether treatment effects differed across user groups and behavioural cohorts — identifying where the feature created the most value.

---

## 💼 Business Recommendation

### 🚀 Recommended Action

> ✅ **Roll out the One-Click Checkout feature.**

### 📊 How to Interpret the Results

| Outcome | Business Decision |
|---|---|
| Statistically & practically significant positive uplift | Proceed with broader rollout |
| Null or marginal result | Iterate on the feature; explore high-impact segments |
| Negative result | Rollback; investigate root cause before re-testing |

Confidence intervals and sensitivity tests quantify risk and help prioritise next steps — whether that means further experimentation, additional data collection, or product iteration.

### 🔭 Follow-up Investigations

- Analyse high-value cart abandonment patterns
- Evaluate treatment effects across additional customer segments
- Monitor guardrail metrics post-launch
- Validate long-term impact through continued experimentation

---

## 🛠️ Tech Stack

### Language
![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white&style=flat)

### Libraries

| Library | Purpose |
|---|---|
| `Pandas` | Data manipulation |
| `NumPy` | Numerical computing |
| `Matplotlib` / `Seaborn` | Data visualisation |
| `SciPy` | Statistical testing |
| `Statsmodels` | Logistic regression |

### Statistical Methods
- Two-Proportion Z-Test
- Logistic Regression & Odds Ratio Analysis
- Hypothesis Testing (Statistical & Practical Significance)
- Heterogeneous Treatment Effect Analysis

---

## 📁 Repository Structure

```
notebooks/
│
├── Causal_framework_and_conversion.ipynb   # Main analysis notebook
│
├── README.md
│
└── assets/                                 # Supporting visuals/outputs
```

---

## 🧠 Skills Demonstrated

### Product Analytics
- Experiment Design & A/B Testing
- Conversion Analysis
- Treatment Effect Evaluation
- Heterogeneous Treatment Effects & Segmentation

### Business Analysis
- Hypothesis Development
- Root Cause Analysis
- Evidence-Based Decision Frameworks
- Statistical vs Practical Significance Distinction

### Statistics
- Statistical Significance Testing & Confidence Intervals
- Logistic Regression & Odds Ratios
- Multivariable & Covariate-Adjusted Analysis

### Data Science
- Exploratory Data Analysis
- Feature Engineering & Data Validation
- Model Interpretation & Reproducibility

---

## 💡 Key Takeaway

This project demonstrates how experimentation can move beyond reporting metrics toward **evidence-based decision making**.

Rather than stopping at a statistically significant result, the analysis investigates:

> *What changed, why it changed, for whom it changed — and whether the business should act on it.*

The framework is adaptable to product experimentation problems across **e-commerce, fintech, SaaS, and consumer technology** companies.

---

*Made with ❤️ using Python and open-source statistical libraries.*