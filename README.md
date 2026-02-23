---
marp: true
theme: default
paginate: true
---

# DSCI 511 Term Project (Phase 1)
## Comparing Out-of-Pocket Healthcare Costs Across Countries

- Countries: United States, Canada, United Kingdom, Japan, China
- Focus: Consumer out-of-pocket costs (vs total government spending)

---

## Why this project is useful

- Compares household financial burden across healthcare system models
- Standardizes indicators across international and national data sources
- Supports reproducible analysis for coursework and policy exploration
- Provides a foundation for downstream visualization and modeling

---

## Planned dataset contents (2015-2022)

- Out-of-pocket healthcare spending per person
- Household healthcare spending as a share of total expenses
- Insurance premiums (where available)
- Copayments and deductibles (where available)
- Prescription drug spending
- Context variables (population, income per capita)

---

## Data sources

Primary sources include:

- WHO Global Health Expenditure Database
- OECD Health Statistics

---

## Getting started: prerequisites

- Python 3.10+
- Jupyter Notebook (recommended)

Install dependencies:

```bash
pip install requests pandas matplotlib jupyter
```

---

## Quick sample pull (World Bank API)

```python
import requests
import pandas as pd

countries = {
    "United States": "USA",
    "Canada": "CAN",
    "United Kingdom": "GBR",
    "Japan": "JPN",
    "China": "CHN",
}

indicator = "SH.XPD.OOPC.PP.CD"
base_url = "https://api.worldbank.org/v2/country/{}/indicator/{}?format=json&per_page=5000"

rows = []
for country, code in countries.items():
    response = requests.get(base_url.format(code, indicator), timeout=30)
    if response.status_code != 200:
        continue
    payload = response.json()
    if len(payload) < 2 or payload[1] is None:
        continue
    for entry in payload[1]:
        rows.append(
            {
                "country": country,
                "year": int(entry["date"]),
                "out_of_pocket_ppp": entry["value"],
            }
        )

df = pd.DataFrame(rows).sort_values(["country", "year"])
df_2020_2024 = df[(df["year"] >= 2020) & (df["year"] <= 2024)].dropna()
print(df_2020_2024.head())
```

---

## Expected output

- Cleaned tabular extract for selected years and countries
- Optional CSV export:
  - `out_of_pocket_health_expenditure_ppp_2020_2024.csv`

---

## Reproducibility notes

- Normalize country names and indicator definitions across sources
- Track currency/PPP assumptions and year alignment
- Document missing values and source-specific caveats in a data dictionary

---

## Project documentation

- Contribution guide: [CONTRIBUTING.md](CONTRIBUTING.md)
- Data dictionary starter: [DATA_DICTIONARY_TEMPLATE.md](DATA_DICTIONARY_TEMPLATE.md)

---

## Limitations

- Country definitions of out-of-pocket spending are not perfectly identical
- Some indicators may have incomplete year coverage
- Data quality and transparency vary by source and country

---

## Where to get help

For questions about scope, preprocessing choices, or source interpretation:

- Ari Voluck — av532@drexel.edu
- Khushi Patel — kp3382@drexel.edu
- Sharon Robinson — slr424@drexel.edu
- Thanh Huynh — th3238@drexel.edu

If moved into a Git repository, use Issues for bug reports and data-quality notes.

---

## Maintainers and contributors

- Ari Voluck
- Khushi Patel
- Sharon Robinson
- Thanh Huynh

Contributions are welcome through pull requests with clear notes on:

- Source files used
- Cleaning and standardization logic
- Any assumptions introduced during preprocessing
