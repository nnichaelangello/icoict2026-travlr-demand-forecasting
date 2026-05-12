# Spatio-Temporal Graph-Enhanced Accommodation Demand Forecasting Using KD-Tree

> **ICOICT 2026 Travlr Data Challenge**
> International Conference on Information and Communication Technology — Telkom University, Bandung, Indonesia

---

## Abstract

This study proposes a spatio-temporal graph-based forecasting framework that constructs a spatial proximity network using KD-Tree between 1,455 hotel properties and 522,948 tourism activities. PageRank and Degree Centrality features are extracted from the resulting bipartite graph and integrated as supplementary predictive features. Validation is conducted through a 2x3 algorithm-agnostic experimental matrix (LightGBM, XGBoost, Random Forest; Baseline vs. Proposed) with 5-Fold Cross-Validation. LightGBM Proposed achieves the lowest RMSE (1.1670 +/- 0.1862) with a statistically significant 3.35% reduction (p=0.0033). SHAP Out-of-Fold analysis reveals PageRank as the most influential predictor (SHAP=0.2230).

---

## Repository Structure

```
├── spatio_temporal_graph_accommodation_demand_forecasting.ipynb   # Main notebook
└── README.md
```

---

## Notebook Contents

The main notebook (`spatio_temporal_graph_accommodation_demand_forecasting.ipynb`) covers the full experimental pipeline:

1. Data acquisition and preprocessing
2. Spatial graph construction using KD-Tree
3. Topological feature extraction (PageRank, Degree Centrality)
4. Feature engineering
5. 5-Fold Cross-Validation (Baseline vs. Proposed, 3 algorithms)
6. Statistical significance analysis (Paired T-Test, Nemenyi CD)
7. SHAP Out-of-Fold interpretability analysis
8. Computational profiling

---

## Dataset

Datasets are provided by **Travlr** as part of the ICOICT 2026 Data Challenge:

- **RowZero:** [https://rowzero.com/workbook/81AADA4374D23AE03777992C](https://rowzero.com/workbook/81AADA4374D23AE03777992C)
- **Kaggle:** [https://www.kaggle.com/datasets/noviananggis/icoict-challenge-2026](https://www.kaggle.com/datasets/noviananggis/icoict-challenge-2026)

Three datasets are used:

| Dataset | Records | Description |
|---|---|---|
| Accommodation Transactions | 3,734 | Booking transaction data per property |
| Accommodation Metadata | 3,694,025 | Ratings, price, availability, coordinates |
| Tourism Activities | 522,948 | Activity category, price, rating, coordinates |

---

## Key Results

| Model | RMSE | MAE | R2 |
|---|---|---|---|
| LightGBM Baseline | 1.2076 | 0.5872 | -0.0408 |
| LightGBM Proposed | **1.1670** | 0.5742 | 0.0448 |
| XGBoost Baseline | 1.2015 | 0.5800 | -0.0327 |
| XGBoost Proposed | 1.1955 | 0.5786 | -0.0256 |
| RandomForest Baseline | 1.2119 | 0.5584 | -0.0500 |
| RandomForest Proposed | 1.1946 | **0.5498** | -0.0218 |

**Top SHAP Feature:** PageRank (mean SHAP = 0.2230)

---

## Methodology Overview

```
Raw Datasets
     |
     v
Data Preprocessing & Inner Join (1,455 labeled instances)
     |
     v
KD-Tree Spatial Graph Construction
(8,979 nodes, 43,650 edges, k=30 nearest activities per hotel)
     |
     v
Topological Feature Extraction
(PageRank alpha=0.85, Degree Centrality)
     |
     v
2x3 Algorithm-Agnostic Experiment
(LightGBM / XGBoost / RandomForest x Baseline / Proposed)
     |
     v
5-Fold Cross-Validation + Statistical Analysis
     |
     v
SHAP Out-of-Fold Interpretability
```

---

## Challenge

This repository is submitted as part of the **ICOICT 2026 Travlr Data Challenge**.
More information: [https://icoict.telkomuniversity.ac.id/challenge2026/](https://icoict.telkomuniversity.ac.id/challenge2026/)
