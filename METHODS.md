oop_oecd_vs_who_wide_2015_2022.csv

# METHODS

## Overview

This project builds a reproducible, cross-national dataset of consumer out-of-pocket (OOP) healthcare expenditures per capita (PPP-adjusted) for the United States, Canada, United Kingdom, Japan, and China, covering 2015–2022. The aim is to harmonize data from major international sources, compare trends, and provide a transparent, fully scripted data pipeline.

---

## Data Sources

- **WHO Global Health Expenditure Database (GHED):** Accessed via the World Bank API. Provides internationally comparable OOP health expenditure indicators.
- **OECD Health Statistics:** Accessed via the OECD SDMX API. Reports household OOP expenditure (HF3) per capita, PPP-adjusted.
- Both sources follow the System of Health Accounts (SHA 2011) framework.

---

## Data Acquisition & Processing

All data are retrieved and processed programmatically in Python using:
- `requests` for API calls
- `pandas` for data wrangling
- Jupyter Notebook for workflow documentation

**Pipeline steps:**
1. Automated API requests to WHO/World Bank and OECD endpoints
2. Parse JSON/CSV responses into DataFrames
3. Filter for years 2015–2022
4. Standardize column names and country codes (ISO alpha-3)
5. Enforce numeric types and tidy long format
6. Merge datasets on (country_code, year)
7. Calculate absolute and percentage differences
8. Handle missing values and document all steps

All code is fully scripted for end-to-end reproducibility.

---

## Dataset Structure

- **Format:** Tidy long format (one row per country-year)
- **Countries:** 5
- **Years:** 2015–2022
- **Observations:** 40
- **Variables:** 7 (see Data Dictionary)
- **Primary key:** (country_code, year)
- **Files:** 
	- `oop_oecd_vs_who_long_2015_2022.csv`
	- `oop_oecd_vs_who_wide_2015_2022.csv`

---

## Key Variables

- Country name
- ISO country code
- Year
- OECD OOP expenditure
- WHO OOP expenditure
- Absolute difference
- Percentage difference

See DATA_DICTIONARY.md for full definitions.

---

## Reproducibility

- All steps are scripted; no manual downloads required
- Jupyter Notebook documents the entire workflow
- Pipeline is easily extendable to new countries or years

---

## Data Access & Ethics

- All data are from public, government sources (WHO, OECD)
- No personal or restricted data are used
- Dataset is for educational and research purposes only

---

## Limitations

- Minor discrepancies between OECD and WHO due to update cycles
- PPP adjustments may differ slightly by source
- COVID-19 may affect comparability (2020–2021)
- OOP spending excludes insurance premiums

---

## Applications

- Health economics and policy research
- Cross-national comparisons
- Public health reporting
- Academic and journalistic analysis

---

## Repository Contents

- README.md
- METHODS.md
- DATA_DICTIONARY.md
- DSCI-511-GroupProject-DataGather.ipynb
- oop_oecd_vs_who_long_2015_2022.csv
- oop_oecd_vs_who_wide_2015_2022.csv

---

## License

This dataset is derived from public government statistics and is intended for educational and research use.
