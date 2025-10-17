# MAUDE Safety Signals (2021–2024)

**Author:** Michael S. Mohle  
**Course:** WGU D502 – Data Analytics Capstone  
**Release:** v1.0.0-maude-2021-2024  
**Repository:** [https://github.com/mspmohle/maude-safety-signals-2021-2024](https://github.com/mspmohle/maude-safety-signals-2021-2024)

---

## Project Overview
This project implements a reproducible analytics pipeline to detect potential safety signals in the **FDA MAUDE** (Manufacturer and User Facility Device Experience) database covering years **2021–2024**.  

The purpose of this work is to provide regulatory-compliance and quality-assurance teams with a **data-driven early warning system** for identifying device-problem combinations that exhibit disproportionate adverse-event reporting.  
The analysis supports the broader organizational goal of improving **post-market surveillance** and patient safety through proactive signal monitoring.

---

## Methodology
The workflow follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** framework:

1. **Business Understanding:** Define safety-monitoring objectives and success metrics.  
2. **Data Understanding:** Acquire MAUDE bulk CSVs, validate schema, and assess data completeness.  
3. **Data Preparation:** Standardize keys, normalize brand/problem mappings, and construct a quarterly index.  
4. **Modeling:**  
   - Compute **Proportional Reporting Ratio (PRR)** and **Reporting Odds Ratio (ROR)**.  
   - Apply **Benjamini–Hochberg False Discovery Rate (FDR)** correction.  
   - Conduct **Interrupted Time Series (ITS)** analysis for intervention effects.  
5. **Evaluation:** Interpret visual and statistical results to identify actionable signals.  
6. **Deployment:** Package as an executable Jupyter Notebook with clear documentation.

---

## Results Summary
- Identified **ALARIS Pump Module × Problem 1135** as a statistically significant outlier (PRR ≈ 128.7; ROR ≈ 3546.5; *p* < 0.001).  
- ITS regression demonstrated a **negative post-intervention slope**, indicating a reduction in incident frequency after 2024-Q1.  
- All visuals (Top-12 bar chart, PRR/ROR table, and ITS plot) are generated directly from the notebook for consistent labeling and scale control.

---

## Repository Structure
maude-safety-signals-2021-2024/
│
├── notebooks/
│ └── maude_signals.ipynb # Main Jupyter notebook (full workflow)
│
├── environment.yml # Reproducible Conda environment
├── LICENSE # MIT License
├── README.md # Project overview and instructions
└── screenshots/ # Optional figures for presentation/report


---

## Data Handling
Raw MAUDE data files are **not included** in this repository to comply with FDA redistribution policy and to maintain manageable repository size.  

However, all analyses are fully **reproducible** using public data from the FDA portal.  
The notebook provides clear instructions and URLs for downloading MAUDE bulk data directly from:

> **FDA MAUDE Portal:**  
> [https://www.accessdata.fda.gov/scripts/cdrh/cfdocs/cfMAUDE/search.cfm](https://www.accessdata.fda.gov/scripts/cdrh/cfdocs/cfMAUDE/search.cfm)

---

## Reproducibility
To recreate the analysis:

# 1. Clone the repository
```bash
git clone https://github.com/mspmohle/maude-safety-signals-2021-2024.git
cd maude-safety-signals-2021-2024

# 2. Create the environment
conda env create -f environment.yml
conda activate maude-signals

# 3. Launch the notebook
jupyter notebook notebooks/maude_signals.ipynb

All outputs, including figures and tables, will be generated automatically.

Key Recommendations
	1	Targeted Follow-Up: Specialized triage and release-gate checks for high-signal device/problem pairs.
	2	Quarterly Surveillance: Refresh PRR/ROR estimates and ITS models, maintaining a live safety-dashboard for QA leadership.
These recommendations connect the analysis to actionable quality-improvement processes.

Evidence of Completion
	•	Final Notebook: notebooks/maude_signals.ipynb
	•	Environment Spec: environment.yml
	•	GitHub Release: v1.0.0-maude-2021-2024
	•	Repository: https://github.com/mspmohle/maude-safety-signals-2021-2024

References

Benjamini, Y., & Hochberg, Y. (1995). Controlling the false discovery rate: A practical and powerful approach to multiple testing. Journal of the Royal Statistical Society: Series B (Methodological), 57(1), 289–300.
Bernal, J. L., Cummins, S., & Gasparrini, A. (2017). Interrupted time series regression for the evaluation of public health interventions: A tutorial. International Journal of Epidemiology, 46(1), 348–355.*
U.S. Food & Drug Administration. (n.d.). Manufacturer and User Facility Device Experience (MAUDE).
van Puijenbroek, E. P., Bate, A., Leufkens, H. G. M., Lindquist, M., Orre, R., & Egberts, A. C. G. (2002). A comparison of measures of disproportionality for signal detection in spontaneous reporting systems for adverse drug reactions. Pharmacoepidemiology and Drug Safety, 11(1), 3–10.*

© 2025 Michael S. Mohle. Licensed under the MIT License.


