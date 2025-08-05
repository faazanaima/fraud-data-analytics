# Online Gambling Fraud Detection via PU Learning (Pconf + Isolation Forest + AdaBoost)

## **Fraud Analytics in E-Wallet Systems: Precision-Driven Analysis of Online Gambling Transactions**

This project addresses the surge in **online gambling transactions in Indonesia** via **E-Money and digital wallets**, which financial service providers are required to block and report per regulations.

Due to **limited ground-truth labels**, this project uses **Positive-Unlabeled (PU) Learning**, specifically leveraging **Isolation Forest** and **AdaBoost Regressor (Pconf Learning)** to detect hidden frauds in partially labeled data.

---

## Problem Statement

- **Detect patterns** of online gambling fraud from anonymized transactions.
- **Predict fraud** using:
  - `reported` transactions = **confirmed fraud** (label = 1)
  - `unidentified` transactions = **unlabeled** (contains mix of fraud and non-fraud)

---

## Goals

1. **Pattern Discovery** via Exploratory Data Analysis (EDA) + Statistical Tests
2. **Build Predictive Model** using supervised and semi-supervised learning

---

## Analytic Framework

### 1. Descriptive Analytics
- Understand temporal & transactional behavior
- E.g., spikes during **weekends**, **evening hours**, or **mid-month salary dates**

### 2. Diagnostic Analytics
- Use statistical tests (Kruskal-Wallis, Spearman) to validate patterns
- Confirm significance of features like `transaction_type`, `party_type`, `amount`, `channel`, and `duration`

### 3. Predictive Analytics
- Hybrid approach:
  - **Isolation Forest** (PU Learning): Outlier detection on known frauds
  - **AdaBoost Regressor** (Pconf Learning): Fraud confidence scoring
  - Final **AdaBoost Classifier**: Fraud prediction using pseudo-labeled dataset

---

## 📈 Model Results

  - We use semi-supervised Isolation Forest and supervised AdaBoost (lr=1, n=50) to detect fraud
  - High-confidence frauds from Isolation Forest train an AdaBoost regressor to estimate fraud confidence. High scores become pseudo-positives, low scores pseudo-negatives.
  - Combined with reported frauds, this labeled data trains the final model
  - Best model (AdaBoost) achieves PR AUC 99.27% at threshold 0.48, with F2-score 95.02% (fraud), F1-score 95.4% (fraud), 82.1% (non-fraud), and 92.67% accuracy.
---

## 💰 Cost-Benefit Evaluation

> The model reduces investigation cost by 20.9% and total cost by 9.6%, demonstrating strong operational efficiency.

---

## 📌 Key Fraud Patterns

| Pattern Type | Findings |
|--------------|----------|
| Temporal     | Fraud spikes at **18:00–21:00**, weekends, and mid-month dates (14–17) |
| Channel      | **E-money** and **withdrawals** dominate fraud activity |
| Value        | Fraud is **high-value** at night and weekends |
| Regulation   | 2023 saw a major fraud spike after **stricter wallet regulations**

---

## 📚 Theoretical Basis

- **Positive-Unlabeled Learning**: Elkan & Noto (2008)
- **Pconf Learning**: Ishida et al. (2018) — *Learning from Positive Data with Confidence*
- **F2-Score Optimization**:
  - Prioritizes recall: **minimizes cost of undetected fraud**
  - Industry-validated: **FN costs are 10x–100x** higher than FP

│   ├── cost_analysis_summary.pdf
├── README.md
