# DSCI 511 Term Project (Proposal)  
## Comparing Out-of-Pocket Healthcare Costs Across Countries  

- Countries: Canada, China, Great Britain, Japan, US  
- Focus: Consumer out-of-pocket healthcare expenditures (vs total government spending)  

## Why this project is useful  

- Compares household financial burden across healthcare models for 5 select countries  
- Standardizes indicators across international and domestic data sources  
- Supports reproducible analysis for coursework and policy exploration  
- Provides a foundation for downstream visualization and modeling  

## Planned dataset contents (2015-2022)  

- Dataset contains aggregated national statistics only  
- Out-of-pocket expenditure per capita (Purchasing Power Parity (PPP)-adjusted, current international dollars)  
- Household healthcare spending as a share of total expenses  
- Insurance premiums (where available)  
- Copayments and deductibles (where available)  
- Prescription drug spending (where available)  
- Context variables (population, income per capita)  

## Data sources  

Primary sources include:  

- WHO Global Health Expenditure Database, Years 2015-2022  
- OECD Health Statistics, Years 2015-2022  

## Getting started: prerequisites  

- Python 3.13+  
- Jupyter Notebook (recommended)  

Install dependencies:  

```bash
pip install requests pandas matplotlib jupyter
```

## Quick sample pull (WHO APIs)

```python
import requests  
import pandas as pd  
import matplotlib.pyplot as plt  

countries = {  
    "United States": "USA",  
    "Canada": "CAN",  
    "United Kingdom": "GBR",  
    "Japan": "JPN",  
    "China": "CHN"  
}  

indicator = "SH.XPD.OOPC.PP.CD"  

base_url = "https://api.worldbank.org/v2/country/{}/indicator/{}?format=json&per_page=5000"   

all_data = []  

for country_name, country_code in countries.items():  
    url = base_url.format(country_code, indicator)  
    response = requests.get(url)  

    if response.status_code != 200:  
        print(f"Error fetching data for {country_name}")  
        continue  

    json_data = response.json()  

    if len(json_data) < 2 or json_data[1] is None:  
        print(f"No data available for {country_name}")  
        continue  

    for entry in json_data[1]:  
        if entry["value"] is not None:  
            all_data.append({  
                "country": country_name,  
                "year": entry["date"],  
                "value": entry["value"]  
            })  
```

## Expected output  

- Cleaned tabular extract for selected years and countries  

## Reproducibility notes  

- Normalize country name and country code indicator definitions across sources  
- Track currency/PPP assumptions and year alignment  
- Document missing values and source-specific limitations in a data dictionary  

## Project documentation  

- README guide: [README.md](README.md)  
- Data Dictionary starter: [DATA_DICTIONARY.md](DATA_DICTIONARY.md)  
- Data Processing methods: [METHODS.md](METHODS.md)  

## Limitations  

- Country definitions of out-of-pocket consumer spending are not perfectly identical  
- Some indicators may have incomplete year coverage  
- Data quality and transparency vary by source and country  
- Minor discrepancies between OECD and WHO values due to revision timing and update cycles  
- PPP adjustments may vary slightly between reporting systems  
- COVID-19 may distort short-term comparability (2020–2021)  
- Out-of-pocket spending excludes insurance premiums  

## Where to get help  

For questions about scope, preprocessing choices, or source interpretation:  

- Thanh Huynh — th3238@drexel.edu  
- Khushi Patel — kp3382@drexel.edu  
- Sharon Robinson — slr424@drexel.edu  
- Ari Voluck — av532@drexel.edu  

In GitHub repository, use Issues for bug reports and data-quality notes  

## Maintainers and contributors  

- Thanh Huynh  
- Khushi Patel  
- Sharon Robinson  
- Ari Voluck  

Contributions are welcome through pull requests with clear notes on:  
- Source files used  
- Cleaning and standardization logic  
- Any assumptions introduced during preprocessing  
