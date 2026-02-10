## Project Overview

This repository contains my solution to the **SkyGeni Sales Intelligence Challenge**, where a B2B SaaS CRO has seen win rates drop while pipeline volume looks healthy. 

The project focuses on:
- Understanding why win rate is changing.
- Identifying which segments are driving wins and losses.
- Turning analysis into a simple, actionable insight and alert system.

Key components:
- Exploratory data analysis and business insights (Part 2).
- A win rate driver decision engine (Part 3).
- A mini Sales Insight & Alert System built on top of the driver analysis (Part 4).

---

## Mini Sales Insight & Alert System (Part 4)

The notebook `mini-system_design.ipynb` implements a lightweight alerting layer on top of the win rate driver analysis. 

Core ideas:
- Use segment-level drivers to understand which combinations of industry, region, and lead_source drive high or low win rates.
- Turn segment win rates into deal-level scores and qualitative risk bands using simple rules.
- Trigger human-readable alerts when performance changes or the pipeline composition drifts. 

Alerts implemented:
- Win-rate drop in key segments over time (recent vs historical).
- Emerging high-value driver segments based on win rate × average deal amount.
- Pipeline skewed toward low-fit segments by value.
- Stage stalling by segment using historical median sales cycle length. 

This notebook acts as a prototype “insight engine” that could later be productionized as a scheduled job and integrated with a CRM or BI tool. 

---

## Repository Structure

- `skygeni_sales_data.csv` – Synthetic CRM-style deals dataset. 
- `Win_Rate_Driver_Analysis.ipynb` – EDA and win rate driver analysis. 
- `mini-system_design.ipynb` – Mini Sales Insight & Alert System and alert logic. 

---

## How to Run

1. Create and activate a Python 3 environment.
2. Install dependencies (for example):
   pip install pandas numpy jupyter
3. Ensure skygeni_sales_data.csv is available at the path used in the notebooks (update paths if needed). 
4. Start Jupyter:
  jupyter notebook
5. Open and run:
  Win_Rate_Driver_Analysis.ipynb to understand drivers and metrics.
  mini-system_design.ipynb to see deal-level scoring and alerts a CRO can act on. 


