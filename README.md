# Grupo Ortiz · Manufacturing Profitability Analysis
**Real P&L visibility across 17 plants through cost standardization, distortion detection, and unified BI reporting**
 
## Business Problem
 
Grupo Ortiz is a Mexican industrial group with 3,000+ employees and ~$40.8M MXN in monthly revenue across 17 active plastic manufacturing plants (bags, stretch film, ropes, packaging, corners, disposables), a recycling facility, a freight company, a hotel, and real estate.
 The Corporate BI team received monthly reports from 18 plants built on incompatible costing criteria: some plants used standard raw material prices without reflecting market variations, import tariffs, or freight costs; others double-counted labor and distribution line items. The result was a fragmented, non-comparable profitability picture that made investment and expansion decisions unreliable.
 The structural root cause: revenue was managed at the division level (single sales team), while costs and production were tracked plant by plant. That asymmetry distorted margin attribution across the entire group.
 
## Approach
 
- Designed standardized weekly capture formats (Excel) with mandatory fields: real MP price, variance vs. standard, assigned overhead, production volume, and waste — validated against Oracle NetSuite ERP
- Used **SACOS 4** (the only plant reporting without distortions) as the benchmark to calibrate the homologated costing model; any plant deviating more than ±2pp in equivalent operating concepts was flagged for review
- Built a star schema data model (2 dimensions: Plants, Calendar · 4 fact tables: Costs, Revenue, Production, Cash Flow) to enable any cross-sectional query without rewriting logic
- Calculated the Cash Conversion Cycle (DSO + DIO) for the first time — a KPI absent from all prior reporting
 
## Key Findings
 
| Finding | Detail |
|---|---|
| Plants with distorted margins | 14 of 17 (82%) |
| Average distortion | +10.9pp vs real margin |
| Optimistic plants (10) | Margins inflated +3.3pp to +7.8pp — omitting MP variance, tariffs, and corporate overhead |
| Pessimistic plants (4) | Margins understated −4.0pp to −6.4pp — duplicating freight and labor |
| BOLSAS 1 | Reported margin: 2.6% · Real margin: 7.7% · Had not received capex in 2 years |
| Cash Conversion Cycle | 74 days vs. 55-day sector benchmark — undetected capital at risk |

## Results
 
- **Cost variance reduced 71%**: from ±14.7% (2021) to ±4.2% (2023)
- **13 of 17 plants** closed 2023 within ±5% of budget (vs. 5 of 17 in 2021)
- **Seasonality quantified**: 10-year agricultural demand pattern enabled production planning at 130% capacity Feb–Apr, scheduled major maintenance Jul–Aug, and gave the international sales team a 6-week early window on Stretch Film export orders
- **Unified P&L dashboard** in Power BI replaced parallel, inconsistent reports from individual plant managers
 
## Tech Stack
 
| Tool | Role |
|---|---|
| Python · Pandas | Data cleaning, MP price adjustment logic, cross-validation with NetSuite |
| SQL | Star schema design · 2 dimensions · 4 fact tables |
| Power BI · DAX | Unified dashboard · Plant traffic-light KPIs · Weekly variance reporting |
| Oracle NetSuite | Cross-validation source (early implementation — not used as primary source) |
| Chart.js | Embedded interactive EDA notebook |

 
## Project Structure
 
```
grupo-ortiz-eda/
├── GO-EDA-Notebook.html       # Interactive EDA notebook (self-contained)
├── 01_pipeline_consolidacion.py
├── 03_distorsion_analysis.py
├── 04_seasonality_10yr.py
└── data/
    └── grupo_ortiz_data.csv   # Anonymized dataset
```
 
> **Confidentiality notice:** Data has been anonymized and partially adjusted for demonstration purposes. Methodology and findings remain analytically valid.
 
## Live Demo
 
[→ Explore project data room](https://drive.google.com/drive/folders/19zmmRDBs9ehXa_5uu9DnvRWcxm_OjNj8?usp=drive_link)
