README.md
# Comparing Consumer Out-of-Pocket Healthcare Expenditures  
### A Cross-National Dataset (2015–2022)

**Course:** DSCI 511 – Data Acquisition and Pre-Processing  
**Authors:** Ari Voluck, Khushi Patel, Sharon Robinson, Thanh Huynh  

---

## Project Overview

This project constructs a reproducible dataset comparing **consumer out-of-pocket (OOP) healthcare expenditures per capita** across five countries:

- United States
- Canada
- United Kingdom
- Japan
- China

The dataset covers the years **2015–2022** and focuses on the **financial burden experienced directly by households**, rather than total national healthcare spending.

Out-of-pocket healthcare expenditures include payments made directly by individuals for healthcare services such as physician visits, medications, and hospital services that are not covered by insurance or government programs.

The goal of this project is to:

- Build a **harmonized dataset** of OOP spending per capita (PPP-adjusted)
- Compare trends across five countries
- Evaluate consistency between **OECD** and **WHO** expenditure reporting systems
- Provide a **fully reproducible data pipeline**

---

## Data Sources

The dataset integrates information from two international health expenditure databases.

### 1. WHO Global Health Expenditure Database (GHED)

Accessed via the **World Bank World Development Indicators API**.

This database provides internationally comparable health expenditure indicators reported by national governments.

Indicator used:

> Out-of-pocket expenditure per capita (PPP-adjusted, current international dollars)

---

### 2. OECD Health Statistics

Accessed via the **OECD SDMX API**.

Indicator used:

> Household out-of-pocket expenditure (HF3) per capita, PPP-adjusted

Both datasets follow the **System of Health Accounts (SHA 2011)** framework, which standardizes how healthcare expenditures are reported internationally.

---

## Data Acquisition

Data were retrieved programmatically using Python.

The workflow uses:

- `requests` for API calls
- `pandas` for data processing
- Jupyter Notebook for the pipeline

The process includes:

1. Automated API requests to WHO/World Bank and OECD endpoints
2. Retrieval of JSON and CSV responses
3. Conversion to pandas DataFrames
4. Data validation and type checks

The entire pipeline is **fully scripted**, meaning the dataset can be regenerated without manual downloads.

---

## Data Preprocessing

A structured preprocessing pipeline was used to clean and integrate the datasets.

Steps include:

1. Parse JSON and CSV API responses into pandas DataFrames
2. Filter observations to the years **2015–2022**
3. Standardize column names
4. Convert country identifiers to **ISO alpha-3 codes**
5. Enforce numeric data types
6. Reshape data to tidy long format
7. Merge datasets on `(country_code, year)`
8. Calculate comparison metrics
9. Handle missing values

All preprocessing steps are implemented programmatically to ensure reproducibility.

---

## Dataset Structure

The final dataset is stored in **tidy long format**, where each row represents a **country-year observation**.

Dataset characteristics:

- Countries: 5
- Years: 2015–2022
- Observations: **40**
- Variables: **7**

Primary key:
(country_code, year)

Files included:
oop_oecd_vs_who_long_2015_2022.csv
oop_oecd_vs_who_wide_2015_2022.csv

---

## Key Variables

The dataset includes:

- Country name
- ISO country code
- Year
- OECD reported OOP expenditure
- WHO reported OOP expenditure
- Absolute difference between the two sources
- Percentage difference between the two sources

Full definitions are provided in the **Data Dictionary**.

---

## Reproducibility

The project includes a fully reproducible pipeline.

Key features:

- All API requests scripted in Python
- No manual file downloads required
- Entire workflow documented in a Jupyter Notebook
- Easily extendable to additional countries or years

---

## Data Access

All data used in this project are **publicly available**.

Sources:

- WHO Global Health Expenditure Database
- OECD Health Statistics

The dataset contains **aggregated national statistics only**.

No personal or restricted data are used.

---

## Limitations

Some limitations should be considered:

- Minor discrepancies between OECD and WHO values due to revision timing and update cycles
- PPP adjustments may vary slightly between reporting systems
- COVID-19 may distort short-term comparability (2020–2021)
- Out-of-pocket spending excludes insurance premiums

Despite these limitations, the dataset provides a reliable basis for cross-national comparison of consumer healthcare spending.

---

## Potential Applications

This dataset may be useful for:

- Health economics research
- Cross-national policy analysis
- Public health reporting
- Academic research projects
- Journalism and public policy analysis

---

## Repository Contents
README.md
DATA_DICTIONARY.md
DSCI-511-GroupProject-DataGather.ipynb
oop_oecd_vs_who_long_2015_2022.csv
oop_oecd_vs_who_wide_2015_2022.csv

---

## License

This dataset is derived from publicly available government statistics and is intended for **educational and research purposes**.
