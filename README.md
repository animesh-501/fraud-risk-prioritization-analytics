# Fraud Risk Prioritization & Operational Analytics

**Animesh Choubey** | MSBA, Cal State East Bay

`Python` `SQL / BigQuery` `LightGBM` `NetworkX` `pandas` `scikit-learn`

---

## [Open the Business Narrative Notebook](./00_master_business_walkthrough.ipynb)

*Start here. Full analytical story — problem, approach, fraud ring detection, SQL, cost model, and recommendation.*

---

## What This Project Is

A fraud analytics project built on 590K real e-commerce transactions. The focus is on **analytical decision-making and operational usefulness** — not model complexity.

Four questions a fraud operations team actually cares about:

1. Can we score transactions by risk reliably enough to prioritize a review queue?
2. Are fraudsters acting alone, or in coordinated rings sharing devices and cards?
3. When a transaction is flagged, can we explain *why* in plain language?
4. What does performance translate to in dollars — and at what threshold is it worth running?

---

## Key Results

| Metric | Baseline | Final | Target |
|--------|----------|-------|--------|
| PR-AUC | 0.27 | **0.40** | 0.42 |
| Precision @ 2% review rate | -- | **53%** | 25% |
| Recall @ threshold 0.10 | -- | **~58%** | 60% |

> At 50K transactions/month: **~$200K prevented monthly** vs ~$40K review ops cost — approximately **5x ROI**.

---

## Repo Structure

```
fraud-risk-prioritization-analytics/
|
+-- README.md
+-- 00_master_business_walkthrough.ipynb        <- Start here
|
+-- technical-notebooks/
    +-- 01_EDA_and_Preprocessing.ipynb
    +-- 02_Modeling_and_Evaluation.ipynb
    +-- 03_Graph_Analysis_Fraud_Ring_Detection.ipynb
    +-- 04_Explainability_Analyst_Reports.ipynb
    +-- 05_Validation_Charts.ipynb
```

---

## What the Business Notebook Covers

| # | Section | What It Shows |
|---|---------|---------------|
| 1 | Business Problem | Two-sided cost of fraud — missing fraud vs over-blocking |
| 2 | The Data | 590K transactions, 3.5% fraud rate, why accuracy is the wrong metric |
| 3 | Analytical Approach | LightGBM rationale, PR-AUC vs ROC-AUC, leakage-safe design |
| 4 | Feature Engineering | What each layer added v1 to v5, where the tabular model plateaued |
| 5 | Fraud Ring Detection | Entity graph, network visualisation, how rings become visible |
| 6 | Results & Threshold | Performance charts, threshold selection as a business decision |
| 7 | Analyst Outputs | Plain-language reason texts, flag priority tiers, case export |
| 8 | SQL Analysis | 5 BigQuery queries — ops monitoring, review queue, ring detection |
| 9 | Cost Model | Fraud in dollars, ROI on review ops, optimal threshold curve |
| 10 | Recommendation | What I would actually tell the fraud ops team to do |

---

## SQL Demonstrated

Five production-style BigQuery queries:

- Daily ops monitoring — did flag volume spike overnight?
- Analyst review queue — ranked, priority-tiered, ready to work
- Precision by score band — stakeholder-readable performance table
- Card-level repeat exposure — ring detection without a graph database
- Weekly reason summary — what types of fraud are being caught?

---

## Analytical Approach — In Brief

**Individual signals hit a ceiling.** After iterative feature engineering across 5 model versions, the tabular model plateaued at PR-AUC ~0.40. More individual-transaction features produced diminishing returns.

**Graph analysis changed the problem.** Mapping cards, devices, and email domains as a network made coordinated fraud rings visible. The fraud-neighbour ratio — what fraction of an entity's connections are confirmed fraud — became the single most predictive feature in the final model.

**Every flag has a reason.** 118,108 validation transactions each received a plain-language explanation combining model contributions with network signals. CSV-ready for Tableau or any review queue tool.

---

## How to Run

```bash
git clone https://github.com/animesh-501/fraud-risk-prioritization-analytics
cd fraud-risk-prioritization-analytics
pip install pandas numpy matplotlib scikit-learn lightgbm networkx
jupyter notebook 00_master_business_walkthrough.ipynb
```

> The business narrative notebook runs on **simulated data** — no download needed.
> Technical notebooks use the [IEEE-CIS dataset (Kaggle)](https://www.kaggle.com/c/ieee-fraud-detection/data).

---

*MSBA Capstone — California State University East Bay, 2025*
