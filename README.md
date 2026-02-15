# Advanced Analytics – Global Tourism Project

*Advanced SQL analytics using window functions and CTEs to explore global tourism performance, segmentation, and country shares.*

This repository represents the **final step** of the **Global Tourism Statistics** project — following the  
[Data Warehouse (DWH)](https://github.com/Daniele1388/DWH---Global-Tourism-Project) and  
[Exploratory Data Analysis (EDA)](https://github.com/Daniele1388/EDA---Global-Tourism-Project) phases.  

While the DWH provides the **data architecture** and the EDA ensures **data quality and consistency**,  
this **Advanced Analytics** layer focuses on extracting **insights and patterns** from the Gold Layer  
through advanced SQL modeling, performance metrics, and segmentation logic.

---

## Data Source Dependency

All scripts in this repository depend on the **Gold Layer** of the [Global Tourism Data Warehouse](https://github.com/Daniele1388/DWH---Global-Tourism-Project).  

Ensure that the following **views** are available in your SQL Server environment before execution:  

`fact_domestic_tourism`, `fact_inbound_tourism`, `fact_outbound_tourism`, `fact_tourism_industries`,`fact_sdg` and all related dimension tables (`dim_country`, `dim_indicator`, `dim_unit_of_measure`, `dim_year`).  

This repository also complements the [Exploratory Data Analysis (EDA)](https://github.com/Daniele1388/EDA---Global-Tourism-Project) section, which validates and prepares the Gold Layer for advanced analytics.

---

## Analytical Framework

The analytical model follows a modular, multi-layered approach to evaluate tourism performance and segmentation over time.  

![Advanced Analytics](Docs/Advanced_Analytics.png?v=2)

1. **Change Over Time** → Analyzes year-over-year differences and trends.  
2. **Cumulative Analysis** → Computes running totals and averages using window functions.  
3. **Performance Analysis** → Evaluates countries against historical averages.  
4. **Part-to-Whole Analysis** → Calculates relative contributions to global totals.  
5. **Data Segmentation** → Groups indicators into strategic categories and tiers.  
6. **Reporting & Tier Classification** → Consolidates all metrics into a unified analytical model for visualization and interpretation.

Each module is parameterized and reusable, supporting dynamic execution via `sp_executesql`.

---

## Objectives

The goal of this repository is to:

- Perform **advanced SQL-based analytical modeling** on tourism datasets.  
- Measure **performance, growth, and distribution patterns** over time.  
- Identify **dominant, emerging, and marginal markets** in global tourism.  
- Build a reusable **analytical layer** for future Power BI / Tableau reporting.  

---

## Analytical Modules

All scripts are written in **T-SQL**, fully documented, and organized by analytical type.

| Category | Description |
|-----------|-------------|
| **Change Over Time** | Calculates year-over-year change and percentage growth using `LAG()` and arithmetic comparisons. |
| **Cumulative Analysis** | Uses window functions (`SUM() OVER`, `AVG() OVER`) to track running totals and averages. |
| **Performance Analysis** | Compares actual values vs. long-term averages to flag “Above/Below Average” years. |
| **Part-to-Whole Analysis** | Calculates each country’s percentage contribution to total global tourism values. |
| **Data Segmentation** | Groups indicators into macro-segments (Volume, Capacity, Economic, Transport, Source Markets) and computes their global share. |
| **Reporting & Tier Classification** | Creates a unified tourism view (`vw_fact_tourism_all`) and a reusable function `fn_segment_tier()` to calculate country shares, assign segment tiers (5% / 1% / 0.2%), and enable consolidated reporting across all fact tables. |

---

## Insights & Methodology

Each analytical query follows a **structured, reusable workflow**:

-  **CTEs (Common Table Expressions)** to create logical computation stages.  
-  **Window functions** for ranking, cumulative sums, and moving averages.  
-  **Dynamic SQL** for flexible parameterization (`@Country`, `@Indicator`, `@Units`).  
-  **Comparative metrics** for share, growth, and performance classification.  

Together, these techniques ensure both **transparency and analytical power**, forming a bridge between SQL-based computation and BI visualization.

---

## Example Insights

- France is the top country for total inbound arrivals in the dataset (1995–2022). 
- The **Cumulative Analysis** confirms a steady growth trend from 1995–2019 before the 2020 drop.  
- **Performance Analysis** identifies “High” and “Low” performance years vs. average historical trends.  
- The **Part-to-Whole module** highlights each country’s relative weight within global inbound and outbound tourism.  
- The **Segmentation Analysis** aggregates indicators into strategic macro-areas (Demand, Capacity, Economic Impact, etc.) and ranks their shares globally.  
- The **Reporting module** consolidates all facts and segments into a unified reporting structure with tier classification.

---

## Tools & Environment

- **Microsoft SQL Server (T-SQL)** — Main analytical engine.  
- **Draw.io** — Diagram design (`Advanced_Analytics.png`).  
- **GitHub** — Version control and documentation.  
- *(Optional)* Power BI for visualization.

---

## Repository Structure

```
ADVANCE-ANALYTICS---Global-Tourism-Project/
│
├── sql_scripts/
│ ├── Change_over_time.sql
│ ├── Cumulative Analysis.sql
│ ├── Performance Analysis.sql
│ ├── Part-to_Whole.sql
│ ├── Data Segmentation.sql
│ ├── Reporting.sql
│
├── docs/
│ ├── Advance_Analytics.png
│ ├── Advance Analytics.drawio
│ ├── Tourism Indicator Segmentation.md
│ ├── Segment Tier.md
│
└── README.md
```

---

## Next Steps

- [ ] Implement **Power BI dashboards** connected to the Gold Layer for interactive visualization of key tourism metrics and analytical outputs.

---

## License

This repository is part of the **Global Tourism Statistics** ecosystem and released under the **MIT License**.  

---

## About Me

Hi, I’m **Daniele Amoroso** 
HR Generalist transitioning into **Data Analytics and Data Science**, with a focus on **SQL, Python, and AI-driven analytics**.  

I’m building end-to-end portfolio projects that connect business understanding with data-driven storytelling.  

Connect with me on [LinkedIn](https://www.linkedin.com/in/daniele-a-080786b7/).
