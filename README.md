# Replication Package — SS-IDS Acceptance Study

This repository contains the complete analysis code and data for reproducing
all figures, tables, and statistics reported in the paper.

---

## Repository structure

```
.
├── analysis_replication.ipynb   ← Main notebook (start here)
├── README.md                    ← This file
└── survey/
    ├── results-survey736756.csv ← Anonymised survey responses (N = 89)
    └── sentences_translated.csv ← German-to-English translation map
```

---

## Prerequisites

**Python 3.9 or later** is required. Install dependencies with:

```bash
pip install pandas numpy matplotlib seaborn plotly scipy statsmodels
```

Or, using a virtual environment (recommended):

```bash
python3 -m venv .venv
source .venv/bin/activate       # macOS / Linux
# .venv\Scripts\activate        # Windows
pip install pandas numpy matplotlib seaborn plotly scipy statsmodels
pip install notebook             # if running via Jupyter Notebook
# or
pip install jupyterlab           # if running via JupyterLab
```

Tested with:

| Package      | Version |
|--------------|---------|
| Python       | 3.11    |
| pandas       | 2.2     |
| numpy        | 1.26    |
| matplotlib   | 3.8     |
| seaborn      | 0.13    |
| plotly       | 5.19    |
| scipy        | 1.12    |
| statsmodels  | 0.14    |

---

## Running the notebook

1. Clone or download this repository.
2. Make sure the `survey/` folder is present with both CSV files.
3. Launch Jupyter:

```bash
jupyter notebook analysis_replication.ipynb
# or
jupyter lab analysis_replication.ipynb
```

4. Run all cells in order: **Kernel → Restart & Run All**.

The notebook is self-contained — no internet connection is required after
installing the dependencies.

---

## Notebook structure

| Section | Content |
|---------|---------|
| 0 | Imports & Setup — library imports and file path constants |
| 1 | Data Loading & Cleaning — filter to 89 usable responses |
| 2 | Helper Functions — visualisation and statistical functions |
| 3 | Sample Overview & Dropout Analysis |
| 4 | Demographics (RQ0) — organisation type, size, role, knowledge, age |
| 5 | RQ1 Motivations & Perceptions (§5.1) |
| 6 | RQ2 Operational Preferences (§5.2) |
| 7 | RQ3 Trust & Security Concerns (§5.3) |
| 8 | Global FDR-BH Correction — full 47-test battery |
| 9 | The 5 Confirmed Findings (KF1–KF5) with post-hoc residuals |
| 10 | Open-Text Responses |
| 11 | Soundness Checks — verify sample size, effect sizes, HTL label |
| 12 | Paper Figures — regenerate all four PDF figures used in the manuscript |

---

## Statistical approach

All pairwise comparisons use χ² tests (Pearson 1900). A **single global
Benjamini–Hochberg FDR correction** is applied simultaneously across all
47 tests. Only associations with FDR-adjusted p < 0.05 and n ≥ 10 in every
subgroup are classified as statistically confirmed.

Effect sizes are reported as Cramér's V (Cramér 1946), with thresholds
V < 0.20 (small), 0.20–0.40 (medium), ≥ 0.40 (large) following Rea & Parker (2014).

Cochran's rule (Cochran 1954) is verified before each test; violations are
noted inline. Post-hoc driving-category identification uses Haberman (1973)
adjusted standardized residuals with |z| > 2 as an interpretive threshold.

5 confirmed findings survive all corrections (KF1–KF5), all involving
participation willingness (Q22/S21) crossed with security-feeling or
government-trust items (Q34, Q34Copy, Q36).

---

## Data privacy

All responses are anonymised. Free-text fields have been reviewed and any
incidentally identifying information removed before deposit. The data file
does not contain names, email addresses, or organisation identifiers.

---

## Citation

If you use this replication package, please cite the paper:

```
[citation to be added upon publication]
```

---

## Contact

For questions about the analysis or data, open an issue in this repository
or contact the corresponding author via the address listed in the paper.
