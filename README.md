# Fraud Risk Prioritization & Operational Analytics

**Animesh Choubey** | MSBA, Cal State East Bay  
Python · SQL / BigQuery · LightGBM · NetworkX · pandas · scikit-learn

---

## The Problem

Fraud detection is not just a modeling problem — it's a resource allocation problem.

At ~50K transactions/month, a team of analysts cannot review everything. The real question is: **which transactions should they look at first?**

This project builds a cost-sensitive scoring system that concentrates fraud into a reviewable queue, detects coordinated fraud rings, and gives analysts plain-language explanations for every flagged transaction.

---

## Key Results

| Metric | Value |
|--------|-------|
| Dataset | IEEE-CIS Fraud Detection — 590,540 e-commerce transactions |
| Baseline PR-AUC | 0.27 |
| Final PR-AUC | **0.40** (+48%) |
| Precision @ 2% review rate | **53%** (target: 25%) |
| Recall @ threshold 0.10 | **58%** |
| Transactions explained | **118K+** with plain-language analyst notes |
| Estimated fraud prevented / month | **~$200K** |
| Analyst review cost / month | ~$40K |
| Net operational ROI | **5×** |

---

## What Changed the Signal

Tabular features plateaued at PR-AUC 0.40 after 5 engineering iterations.

Graph analysis broke through. By building a network of shared cards, devices, and email domains across transactions, fraud rings became visible. The **fraud-neighbor ratio** — what fraction of a node's connections are confirmed fraud — became the single most predictive feature.

---

## Start Here

### [Open the Business Narrative Notebook](./00_master_business_walkthrough.ipynb)

Full analytical story: problem framing, feature engineering iterations, graph-based ring detection, SQL workflows, cost model, and operational recommendation.

---

## Repository Structure

```
fraud-risk-prioritization-analytics/
│
├── 00_master_business_walkthrough.ipynb   ← Start here
│
├── technical-notebooks/
│   ├── 01_EDA_and_Preprocessing.ipynb
│   ├── 02_Modeling_and_Evaluation.ipynb
│   ├── 03_Graph_Analysis_Fraud_Ring_Detection.ipynb
│   ├── 04_Explainability_Analyst_Reports.ipynb
│   └── 05_Validation_Charts.ipynb
│
└── README.md
```

---

## SQL Demonstrated

Production-style BigQuery workflows included:

- Daily fraud ops monitoring dashboard
- Ranked analyst review queue by risk score
- Precision by score band reporting
- Card-level repeat exposure detection
- Weekly fraud reason summaries

---

## How to Run

```bash
git clone https://github.com/animesh-501/fraud-risk-prioritization-analytics
cd fraud-risk-prioritization-analytics
pip install pandas numpy matplotlib scikit-learn lightgbm networkx
jupyter notebook 00_master_business_walkthrough.ipynb
```

The business notebook runs on simulated data. Technical notebooks use the IEEE-CIS Fraud Detection dataset (available on Kaggle).

---

## Skills Demonstrated

- Cost-sensitive fraud modeling
- Graph / network fraud ring detection
- Threshold optimization (F2 metric, cost curves)
- Explainable ML for analyst workflows
- SQL for operational analytics
- Business impact translation (ROI, cost model)

---

MSBA Capstone — California State University East Bay · 2026  
[linkedin.com/in/choubey-animesh](https://linkedin.com/in/choubey-animesh) · [animesh-501.github.io](https://animesh-501.github.io)
