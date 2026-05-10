# GAICRA: Geospatial AI Credit Risk Assessment
## A Fairness-Constrained Framework for Equitable Mortgage Access

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Paper:** *Closing the credit desert: a fairness-constrained geospatial AI framework
for predicting and marketing equitable mortgage access in underserved American communities*

**Journal:** Financial Economics Letters (under review, [YEAR])

**Author:** Amir Hasan Khan | Wright State University | khan.295@wright.edu

---

## Overview
GAICRA integrates three components:
1. **GCEI** -- Geospatial Credit Exclusion Index (4-component spatial deprivation measure)
2. **FC-CRC** -- Fairness-Constrained Credit Risk Classifier (XGBoost with ECOA compliance)
3. **SMAM** -- Spatial Marketing Allocation Model (budget-constrained CDFI outreach optimizer)

Applied to 2022 HMDA data across 8 U.S. states (n = 1,578,187 applications, 37,546 census tracts).

---

## Repository Structure
```
GAICRA/
|-- gaicra_pipeline.ipynb   # Full pipeline: data loading through model + maps
|-- requirements.txt        # Python package versions
|-- outputs/                # Generated figures (PNG)
|   |-- gcei_lisa_maps_final.png
|   |-- shap_importance_final.png
|   |-- shap_beeswarm_final.png
|   |-- fap_full_audit.png
|   |-- cdfi_priority_map.png
|-- README.md
```

---

## Data Sources (all free, publicly available)
Download these files and place them in `data/raw/` before running the notebook:

| Dataset | Agency | URL |
|---------|--------|-----|
| HMDA LAR 2022 (8 states) | CFPB | https://ffiec.cfpb.gov/data-browser/data/2022 |
| ACS 5-Year 2022 (B05001, B19013, B03002, B25003, B15003) | Census | https://data.census.gov |
| FFIEC Census Flat File 2020 | FFIEC | https://www.ffiec.gov/censusapp.htm |
| FDIC Summary of Deposits 2022 | FDIC | https://banks.data.fdic.gov/api/branches |
| BLS LAUS Annual 2022 | BLS | https://www.bls.gov/lau/ |
| IRS SOI ZIP Code Data 2022 | IRS | https://www.irs.gov/statistics/soi-tax-stats-individual-income-tax-statistics-zip-code-data-soi |
| TIGER/Line Tract Shapefiles 2022 | Census | https://www.census.gov/cgi-bin/geo/shapefiles/index.php |
| HUD ZIP-Tract Crosswalk Q4 2022 | HUD | https://www.huduser.gov/portal/datasets/usps_crosswalk.html |

---

## How to Run
```bash
# 1. Clone the repository
git clone https://github.com/[yourusername]/GAICRA.git
cd GAICRA

# 2. Install dependencies
pip install -r requirements.txt

# 3. Create folder structure
mkdir -p data/raw/{hmda,acs,ffiec,fdic,bls,irs,shapefiles} data/processed data/tableau_exports models outputs

# 4. Download data (see table above), place in data/raw/ subfolders

# 5. Open and run the notebook
jupyter lab gaicra_pipeline.ipynb
# Run cells 1-12 in order. Cell 3 unzips shapefiles. Total runtime: ~45-90 min.
```

---

## Key Results
| Metric | Value |
|--------|-------|
| Census tracts analyzed | 37,546 |
| Global Moran I (GCEI) | 0.436 (p < 0.001) |
| High-High credit desert tracts | 4,864 |
| FC-CRC AUROC | 0.736 |
| Disparate Impact Ratio | [UPDATE after re-run] |
| Denied class recall | 43.9% at threshold 0.785 |
| CDFI outreach efficiency gain | 3.2x |

---

## Citation
If you use this code, please cite:
```
Khan, A. H. (2026). Closing the credit desert: a fairness-constrained geospatial AI
framework for predicting and marketing equitable mortgage access in underserved
American communities. Financial Economics Letters. [DOI: add after acceptance]
```

---

## License
MIT License. See LICENSE file.
