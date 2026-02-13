# AI-Driven Inventory Intelligence System  
**Demand Signal Extraction • Price Imputation • Decision Analytics (Databricks Lakehouse)**

---

## Overview
This project builds an end-to-end **retail inventory intelligence pipeline** using the **M5 Forecasting (Accuracy)** dataset.  
It transforms raw multi-table sales and price data into **decision-ready weekly analytics** using **data engineering + machine learning**.

The core challenge addressed is **structurally missing price data**, which breaks revenue and KPI analysis.  
A supervised ML model imputes prices while preserving realistic distribution behavior.

---

## Architecture — Lakehouse Pipeline

### Bronze Layer — Raw Tables
- calendar
- sales_train_evaluation
- sell_prices

No transformations. Immutable source layer.

---

### Silver Layer — Cleaned Daily Dataset
Key Steps:
- Store & category scoping
- Wide → Long normalization
- Calendar joins
- Event & SNAP enrichment
- Missing price flags
- Integrity validation

**Output Table:**  
`silver_daily_sales_v2`

---

### Gold Layer — Weekly Intelligence + ML Imputation
Key Steps:
- Daily → Weekly aggregation
- Temporal demand signals (lags, rolling avg, volatility)
- Supervised ML price imputation
- Distribution validation
- Final price clipping safeguard

**Output Table:**  
`gold_weekly_inventory_intelligence_v1`

---

## Key Outcomes

| Metric | Result |
|-------|--------|
| Weekly Rows | ~740k |
| Final Price Null Rate | 0% |
| Observed Price Coverage | ~66% |
| Imputed Coverage | ~34% |
| Distribution Alignment | Median preserved, realistic variance |

---

## Technical Stack
- Databricks Lakehouse  
- PySpark / SQL / Python  
- Spark ML  
- Delta Tables  
- Bronze → Silver → Gold Architecture  

---

## Repository Structure
```text
inventory-intelligence/
│
├── notebooks/
│   ├── 01_bronze_ingestion.ipynb
│   ├── 02_silver_pipeline.ipynb
│   └── 03_gold_ml_imputation.ipynb
│
├── images/
│
└── README.md
