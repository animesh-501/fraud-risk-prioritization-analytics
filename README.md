# Fraud Risk Prioritization & Operational Analytics

**Animesh Choubey** | MSBA, Cal State East Bay
Python · SQL / BigQuery · LightGBM · NetworkX · pandas · scikit-learn

---

## Project Overview

Built a fraud risk scoring system that prioritizes transaction review queues using cost-sensitive modeling and graph-based fraud ring detection. The project focuses on **operational decision-making**, not just model accuracy.

---

## ▶️ Start Here

## [Open the Business Narrative Notebook](./00_master_business_walkthrough.ipynb)

Full analytical story: problem framing, modeling, fraud ring detection, SQL workflows, cost model, and operational recommendation.

---

## Key Business Questions

1. Can transactions be scored reliably enough to prioritize analyst review?
2. Are fraudsters operating individually or in coordinated rings?
3. Can each flagged transaction be explained in plain language?
4. What model performance translates to in **dollars**, and where is the optimal threshold?

---

## Key Results

| Metric                     | Baseline | Final    | Target |
| -------------------------- | -------- | -------- | ------ |
| PR-AUC                     | 0.27     | **0.40** | 0.42   |
| Precision @ 2% review rate | —        | **53%**  | 25%    |
| Recall @ threshold 0.10    | —        | **58%**  | 60%    |

---

## Business Impact

At ~50K transactions/month:

* ~$200K estimated fraud prevented
* ~$40K analyst review cost
* **~5× operational ROI**

---

## Analytical Approach

**Tabular signals plateaued.** After 5 feature engineering iterations, individual-transaction modeling plateaued at PR-AUC ≈ 0.40.

**Graph analysis changed the signal.** Building a network of cards, devices, and email domains exposed coordinated fraud rings.
The **fraud-neighbor ratio** became the single most predictive feature.

**Operational explainability built in.**
118K+ validation transactions received plain-language explanations combining model contributions + network signals, exportable for analyst queues.

---

## SQL Demonstrated

Production-style BigQuery workflows:

* Daily fraud ops monitoring dashboard query
* Ranked analyst review queue
* Precision by score band reporting
* Card-level repeat exposure detection
* Weekly fraud reason summaries

---

## Repo Structure

```
fraud-risk-prioritization-analytics/
│
├── README.md
├── 00_master_business_walkthrough.ipynb   ← Start here
│
├── technical-notebooks/
│   ├── 01_EDA_and_Preprocessing.ipynb
│   ├── 02_Modeling_and_Evaluation.ipynb
│   ├── 03_Graph_Analysis_Fraud_Ring_Detection.ipynb
│   ├── 04_Explainability_Analyst_Reports.ipynb
│   └── 05_Validation_Charts.ipynb
```

---

## Skills Demonstrated

* Fraud risk modeling
* Cost-sensitive threshold optimization
* Graph/network fraud detection
* SQL for operational analytics
* Explainable ML for analyst workflows
* Business impact translation (ROI, cost curves)

---

## How to Run

```bash
git clone https://github.com/animesh-501/fraud-risk-prioritization-analytics
cd fraud-risk-prioritization-analytics
pip install pandas numpy matplotlib scikit-learn lightgbm networkx
jupyter notebook 00_master_business_walkthrough.ipynb
```

* Business notebook runs on **simulated data**
* Technical notebooks use the **IEEE-CIS Fraud Detection dataset (Kaggle)**

---

MSBA Capstone — California State University East Bay (2025)
