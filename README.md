# Credit Risk Modeling — Expected Loss Framework

This project develops a forward-looking credit risk modeling framework using the LendingClub consumer loan dataset. The goal is to estimate portfolio credit risk using the standard banking expected loss equation:

Expected Loss = PD × LGD × EAD

Where:

- **PD (Probability of Default)** estimates the likelihood that a borrower defaults  
- **LGD (Loss Given Default)** estimates the portion of exposure lost if default occurs  
- **EAD (Exposure at Default)** represents the loan exposure  

The framework integrates machine learning models with financial risk modeling techniques to evaluate portfolio credit risk.

---

# Project Objectives

The project aims to:

- Build a **Probability of Default (PD) model**
- Estimate **Loss Given Default (LGD)** using a two-stage modeling approach
- Compute **Expected Loss (EL)** for each loan
- Analyze **portfolio-level credit risk**
- Identify **risk drivers and portfolio risk segments**

---

# Dataset

**Source:** LendingClub Consumer Loan Dataset  

The dataset contains borrower financial and loan information including:

- loan amount
- interest rate
- borrower income
- debt-to-income ratio
- loan purpose
- credit grade
- credit history variables

The dataset contains **over 2 million loans**, enabling large-scale portfolio analysis.

---

# Modeling Framework

The project follows a structured credit risk modeling pipeline.

Borrower Features  
↓  
Probability of Default (PD)  
↓  
Loss Given Default (LGD)  
↓  
Exposure at Default (EAD)  
↓  
Expected Loss = PD × LGD × EAD

---

# 1️⃣ Probability of Default (PD)

A **logistic regression model** predicts borrower default risk using borrower financial and credit characteristics.

### Model Performance

| Metric | Value |
|------|------|
| ROC-AUC | ~0.72 |
| Calibration | Strong alignment between predicted and observed default rates |

The model demonstrates **reasonable discriminatory power** for consumer credit data.

---

# 2️⃣ Loss Given Default (LGD)

LGD is modeled using a **two-stage approach**.

### Stage 1 — Full Loss Classification

Predicts whether a default results in **complete loss**.

### Stage 2 — Partial Loss Regression

Estimates the **fractional loss** for partially recovered loans.

These two stages are combined to produce the **expected LGD** for each loan.

---

# 3️⃣ Expected Loss Framework

Expected Loss is computed using:

EL = PD × LGD × EAD

This produces a **loan-level expected loss estimate** and enables portfolio aggregation.

---

# Portfolio Risk Results

| Metric | Value |
|------|------|
| Total Portfolio Expected Loss | $4.32B |
| Average Expected Loss per Loan | $1,911 |
| Portfolio Expected Loss Rate | 12.7% |

These estimates represent the expected credit losses across the modeled portfolio.

---

# Risk Segmentation Analysis

Portfolio risk varies significantly across borrower characteristics.

### Expected Loss by Credit Grade

Average expected loss increases monotonically from **Grade A to Grade G**, indicating consistent alignment between borrower credit quality and estimated portfolio risk.

Example results:

| Grade | Avg Expected Loss |
|------|------|
| A | ~$505 |
| B | ~$1,167 |
| C | ~$2,047 |
| D | ~$3,074 |
| E | ~$4,667 |
| F | ~$6,544 |
| G | ~$7,571 |

This pattern validates that the model captures the underlying credit risk structure.

---

### Expected Loss by Loan Purpose

Loan purpose also influences credit risk.

Highest expected losses occur for:

- **Small business loans**
- **Debt consolidation loans**

Lower expected losses are observed for:

- medical loans
- major purchases
- general personal loans

---

# Model Diagnostics

Several diagnostics confirm model reliability.

### PD Distribution

Most borrowers fall within low PD ranges, with a smaller high-risk tail — a typical structure in consumer lending portfolios.

### ROC Curve

The model shows **clear separation between good and bad loans**, consistent with ROC-AUC ≈ 0.72.

### Calibration Analysis

Predicted default probabilities closely match observed default rates across risk deciles.

This indicates the model produces **well-calibrated probability estimates**.

---

# Key Risk Drivers

The model identifies several key determinants of borrower risk.

**Primary drivers of higher default risk**

- Lower credit grades (E, F, G)
- Higher installment burdens
- Riskier sub-grade categories

**Factors associated with lower risk**

- Higher credit grades (A and B)
- shorter loan terms
- stronger borrower credit profiles

Credit grade emerges as the strongest predictor, which is expected because it summarizes multiple borrower credit characteristics.

---

# Tools and Technologies

Python libraries used:

- pandas
- numpy
- scikit-learn
- matplotlib

Development environment:

- Python
- Jupyter Notebook
- VS Code

---

# Repository Structure

