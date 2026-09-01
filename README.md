# 📖 Sales Pipeline & Forecast Accuracy Analysis

## 1. Executive Summary

This project analyzes a simulated B2B SaaS sales pipeline of **620 deals** to uncover where and why deals stall, and to build a reliable forecasting layer for revenue planning.

Using a dimensional (star schema) semantic model in Power BI, the analysis identified a **38% deal drop-off rate** at a specific stage in the pipeline and pinpointed the operational bottlenecks driving it. A set of advanced DAX measures — including time-intelligence and relationship-switching patterns — were built to model forecast vs. actual close behavior, achieving **79% forecast accuracy** against simulated deal outcomes.

> **Note:** This is a self-directed portfolio project built on a synthetic dataset designed to mirror real-world B2B SaaS sales dynamics. It is not derived from employer or client data.

**Business questions this project answers:**
- Where in the pipeline are deals most likely to stall or die?
- How accurate can forecast-to-close predictions be made with historical stage-conversion patterns?
- Which sales stages or deal segments need process intervention?

---

## 2. 🛠️ Tech Stack & Tools

| Category | Tools Used |
|---|---|
| Data Modeling | Power BI (Star Schema: Fact_Deals, Dim_Date, Dim_SalesRep, Dim_Stage, Dim_Account) |
| DAX | CALCULATE, USERELATIONSHIP, DATEDIFF, time-intelligence patterns, iterators |
| Data Prep / Simulation | Python (Pandas, NumPy) — used to generate and clean the synthetic 620-deal dataset |
| Visualization | Power BI (interactive report, drill-through, bookmarks) |
| Version Control | Git / GitHub |

---

## 3. 🔄 Data Pipeline & Workflow

1. **Data Generation (Python)** — Simulated a realistic SaaS sales dataset (620 deals) with fields for deal stage, deal value, sales rep, account industry, created date, and close/lost date, using controlled randomization to mimic real pipeline distributions.
2. **Data Cleaning & Shaping (Python/Pandas)** — Standardized date formats, handled stage-sequence logic, and exported clean CSVs for modeling.
3. **Star Schema Design (Power BI)** — Built a fact table (`Fact_Deals`) connected to dimension tables (`Dim_Date`, `Dim_SalesRep`, `Dim_Stage`, `Dim_Account`) using single-direction relationships, with a secondary inactive date relationship activated via `USERELATIONSHIP` for forecast-vs-actual comparisons.
4. **DAX Measure Layer** — Built core measures for pipeline conversion rate, average deal cycle time (`DATEDIFF`), stage drop-off %, and forecast accuracy scoring.
5. **Dashboard Assembly** — Combined measures into an interactive multi-page report with filtering, drill-through, and executive summary view.

---

## 4. 📊 Interactive Dashboard / Visuals

- **Pipeline Overview** — Funnel visualization showing deal volume and value at each stage, highlighting the 38% drop-off point.
- **Forecast Accuracy Tracker** — Actual vs. forecasted close comparison by month, using time-intelligence DAX to isolate forecast reliability (79% accuracy achieved).
- **Sales Rep Performance** — Conversion rate and average cycle time by rep, to surface coaching opportunities.
- **Bottleneck Drill-Through** — Stage-level drill-through page showing deal-level detail for any stage with high drop-off.

```

---

## 5. 💡 Business Insights & Recommendations

**Key findings:**
- **38% of deals drop off** at [specify the actual stage — e.g., "Proposal to Negotiation"], the single largest leak point in the pipeline.
- Deals that stall longer than [X] days at this stage are significantly less likely to close, suggesting a follow-up cadence issue rather than a pricing/product objection.
- Forecast accuracy of 79% was achieved by weighting stage-conversion probability against historical rep-level close rates, outperforming a flat pipeline-value forecast baseline.

**Recommendations:**
1. Introduce a stage-aging alert for deals sitting past the typical cycle time at the bottleneck stage.
2. Standardize follow-up SLAs at the highest-leakage stage to reduce silent drop-off.
3. Use the stage-conversion-weighted forecast model (rather than raw pipeline value) for monthly revenue planning going forward.

---

## 6. 📂 Repository Architecture

```
sales-pipeline-forecast-analysis/
│
├── README.md
├── data/
│   ├── raw/                  # Original simulated dataset
│   └── processed/            # Cleaned CSVs used in Power BI model
│
├── python/
│   └── data_generation_and_cleaning.ipynb
│
├── powerbi/
│   └── Sales_Pipeline_Forecast_Analysis.pbix
│
├── screenshots/
│   ├── pipeline_overview.png
│   ├── forecast_accuracy.png
│   └── sales_rep_performance.png
│
└── docs/
    └── dax_measures.md        # Documented list of key DAX measures with logic explanation
```

---

### 🔗 About This Project
Built as part of an ongoing Power BI / data analytics portfolio. Feedback and questions welcome — feel free to open an issue or connect on [LinkedIn].
