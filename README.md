## Project Overview

This repository contains my solution to the **SkyGeni Sales Intelligence Challenge**, where a B2B SaaS CRO has seen win rates drop while pipeline volume looks healthy.[file:18]

The project focuses on:
- Understanding why win rate is changing.
- Identifying which segments are driving wins and losses.
- Turning analysis into a simple, actionable insight and alert system.

Key components:
- Exploratory data analysis and business insights (Part 2).
- A win rate driver decision engine (Part 3).
- A mini Sales Insight & Alert System built on top of the driver analysis (Part 4).

---

## Exploratory Analysis & Business Insights (Part 2)

The notebook `01_exploratory_analysis-1.ipynb` performs exploratory analysis on the SkyGeni dataset.

It covers:
- Data quality checks and basic profiling (distributions, outliers, missing values).
- Win-rate trends by time, segment, and pipeline stage.
- Early hypotheses on why win rate is changing across industries, regions, and lead sources.

This part sets the context and frames the key questions for the driver analysis and system design.

---

## Win Rate Driver Analysis (Part 3)

The notebook `02_Win_Rate_Driver_Analysis.ipynb` focuses on understanding which factors drive higher or lower win rate and turning that into a lightweight decision engine.[file:17]

Core ideas:
- Use segment-level statistics (industry, region, lead_source, deal_stage) to compute win rates and average deal size.
- Build a driver table with lift vs baseline win rate and a simple **driver_score** (win rate × average deal amount).
- Derive stage-aware segment win probabilities and rule-based **risk bands** for deals.

Outputs include:
- Tables and charts that highlight strong and weak segments.
- A simple, interpretable “decision engine” that scores deals and segments in a way a CRO can act on.

---

## Mini Sales Insight & Alert System (Part 4)

The notebook `03_mini-system_design.ipynb` implements a lightweight **Sales Insight & Alert System** on top of the driver analysis.

Core ideas:
- Reuse segment-level drivers to understand which combinations of industry, region, and lead_source drive high or low win rates.
- Turn segment-stage win rates into deal-level **seg_win_prob** and qualitative **risk_band** using simple rules.
- Detect stalled pipeline pockets by tracking how long deals have been in a given stage and aggregating stalled value by segment.
- Generate structured alert objects (e.g., high-performing segments, stalled pipeline, high-risk/high-value deals) that can be surfaced via email, Slack, or a dashboard.

This notebook acts as a prototype **insight engine** that could be productionized as a scheduled job and integrated with a CRM or BI tool.

---

## Repository Structure

- `skygeni_sales_data.csv` – Synthetic CRM-style deals dataset.
- `01_exploratory_analysis-1.ipynb` – Exploratory analysis and business insights (Part 2). 
- `02_Win_Rate_Driver_Analysis.ipynb` – Win rate driver analysis and decision engine (Part 3). 
- `03_mini-system_design.ipynb` – Mini Sales Insight & Alert System and alert logic (Part 4).

---

## How to Run

1. Create and activate a Python 3 environment.
2. Install dependencies (for example):  
   
    pip install pandas numpy jupyter seaborn matplotlib

3. Ensure skygeni_sales_data.csv is available at the path used in the notebooks (update paths if needed).
4. Start Jupyter:
    jupyter notebook
5. Open and run, in this order:

01_exploratory_analysis-1.ipynb to understand the data and initial business insights.

02_Win_Rate_Driver_Analysis.ipynb to see win rate drivers and the decision engine.

03_mini-system_design.ipynb to see deal-level scoring, stalled pipeline detection, and alerts a CRO can act on.
