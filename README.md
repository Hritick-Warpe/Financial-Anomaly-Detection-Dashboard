# Financial Transaction Anomaly Detection & Audit Reporting Dashboard

An end-to-end audit analytics pipeline that analyzes 217,441 real-world financial transactions to detect anomalous, high-risk entries — simulating a real-world audit/claims investigation workflow from raw data to an executive-ready dashboard.

## Overview

This project takes a large financial transaction dataset and runs it through a full audit analytics pipeline:

1. **Data extraction & querying** (SQL/MySQL) — surfacing duplicate payments, high-value outliers, and merchant/location-level spend concentration
2. **Anomaly detection** (Python, scikit-learn) — an Isolation Forest model statistically flags high-risk transactions beyond what fixed-threshold rules alone would catch
3. **Automated reporting** (Excel VBA) — auto-formats and highlights exception reports, cutting manual report-prep effort
4. **Interactive dashboard** (Power BI) — a 5-visual dashboard surfacing total flagged exposure, merchant risk ranking, and geographic distribution

## Key Findings

| Metric | Value |
|---|---|
| Total transactions analyzed | 217,441 |
| Transactions flagged as anomalous | 4,345 (≈2%) |
| Total flagged exposure | ₹176.21M |
| Merchants covered | 10 |
| Locations covered | 5 (New York, London, Tokyo, Los Angeles, San Francisco) |

## Tools & Tech Stack

- **SQL (MySQL)** — data storage, querying, audit checks
- **Python** — Pandas, NumPy, scikit-learn (Isolation Forest)
- **Excel VBA** — automated exception-report formatting
- **Power BI** — interactive dashboard (KPI card, bar chart, map, table, slicer)

## Project Structure

```
├── README.md                  → this file
├── sql/
│   └── audit_queries.sql      → database setup + all audit queries
├── python/
│   └── anomaly_detection.ipynb → Isolation Forest model + analysis
├── dashboard/
│   └── dashboard_screenshot.png → Power BI dashboard preview
└── docs/
    └── project_summary.pdf     → full written findings report
```

## How It Works

### 1. SQL — Data Loading & Audit Queries
The raw dataset is loaded into a MySQL database. Audit-style queries identify:
- Top high-value transactions
- Per-account transaction concentration
- Duplicate payment patterns (same account, same amount, multiple occurrences)
- Location-wise withdrawal patterns

See [`sql/audit_queries.sql`](./sql/audit_queries.sql) for the full query set.

### 2. Python — Anomaly Detection
An **Isolation Forest** model (unsupervised ML, ideal for outlier detection without labeled fraud data) is trained on transaction amounts to flag statistically anomalous entries — catching risk patterns that fixed-rule thresholds would miss.

See [`python/anomaly_detection.ipynb`](./python/anomaly_detection.ipynb).

### 3. Excel VBA — Automated Reporting
A VBA macro auto-formats the flagged-transaction report: bolding headers, auto-fitting columns, and conditionally highlighting transactions above a risk threshold — removing manual formatting work.

### 4. Power BI — Dashboard
An interactive dashboard with:
- **KPI Card** — total flagged exposure
- **Bar Chart** — flagged amount by merchant
- **Map** — geographic distribution of flagged transactions
- **Table** — full transaction-level detail
- **Slicer** — drill-down filter by location

## Dataset Source

[Kaggle — Financial Anomaly Data](https://www.kaggle.com/) (217,441 simulated financial transactions across multiple accounts, merchants, and locations)

## Author

**Hritick Warpe**
BCA Graduate | Data Analyst | [LinkedIn](#) | hritickwarpe@gmail.com
