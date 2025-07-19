# 🛡️ Automated Financial Risk Monitoring & Fraud Reporting Workflow

This Alteryx project delivers an end-to-end **fraud detection and risk reporting pipeline** using the [PaySim Financial Transactions dataset](https://www.kaggle.com/datasets/ntnu-testimon/paysim1). It simulates real-world banking transactions, identifies high-risk patterns, and generates a structured PDF report for stakeholders.

---

## 📌 Key Objectives

- Detect **suspicious and fraudulent transactions** using logical rules and scoring techniques.
- Assign **risk tiers** (`Critical`, `High`, `Moderate`, `Low`) for better prioritization.
- Monitor patterns like **balance depletion**, **velocity of transactions**, and **risk indicators**.
- Generate **automated visual reports** using built-in Alteryx reporting tools.

---

## 🧰 Tools Used in Alteryx Workflow

| Tool | Purpose |
|------|---------|
|  **Input Data Tool** | Imports CSV data from the PaySim dataset. |
|  **Sample Tool** | Reduces dataset to 1000 rows for faster processing during testing. |
|  **Formula Tool** | Derives new fields like `is_debit`, `balance_usage`, `is_full_depletion`, and `isHighRiskType`. |
|  **Risk Scoring Logic** | Calculates `risk_score` based on conditions like amount, transaction type, and behavior. |
|  **Filter Tool** | Extracts `High` and `Critical` tier transactions for focused analysis. |
|  **Summarize Tool** | Aggregates fraud count, tier-wise metrics, and percentages. |
|  **Table Tool** | Displays structured results like fraud count per tier. |
|  **Chart Tool**  | Adds visuals like pie and bar charts for tier distribution. |
|  **Layout Tool** | Organizes all reporting components (tables + charts + text). |
|  **Render Tool** | Exports the final structured PDF or Word report (e.g., `Fraud_Risk_Report.pdf`). |

---

## 📉 Workflow Overview

1. **Data Ingestion**
   - Load `PS_20174392719_1491204439457_log.csv` from the PaySim dataset.
   - Limit to **1000 records** for faster testing and visualization.
2. **Feature Engineering**
   - Compute behavioral metrics like `balance_usage`, `is_full_depletion`, and `isHighRiskType`.
3. **Risk Scoring**
   - Score each transaction based on amount thresholds, transaction types, and patterns.
4. **Tier Assignment**
   - Apply tier logic:
     - `Critical`: High score with full balance depletion and high-risk type
     - `High`: Moderate to high score with risky behavior
     - `Moderate`: Mid-level score
     - `Low`: Minimal risk
5. **Fraud Filtering**
   - Focus on transactions where `is_fraud = 1` and tier is `High` or `Critical`.
6. **Aggregation**
   - Summarize fraud statistics across tiers.
7. **Reporting**
   - Generate tables and (optionally) charts.
   - Use `Layout` and `Render` tools to export report as PDF.

---

## 📁 Repository Structure

```bash
financial-risk-monitoring-alteryx/
├── financial-risk-monitoring-workflow.yxmd
├── README.md
├── assets/
│   └── workflow_layout.png    
