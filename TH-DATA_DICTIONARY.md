DATA_DICTIONARY.md
# Data Dictionary
### Out-of-Pocket Healthcare Expenditures Dataset (2015–2022)

This document describes the variables included in the dataset.

Dataset file:
oop_oecd_vs_who_long_2015_2022.csv

---

## Dataset Description

The dataset contains **out-of-pocket healthcare expenditures per capita** for five countries between 2015 and 2022.

Data are compiled from:

- OECD Health Statistics
- WHO Global Health Expenditure Database (via World Bank)

All values are **PPP-adjusted current international dollars per capita**.

Each row represents a **country-year observation**.

Primary key:
country_code + year

Dataset size:
40 rows × 7 columns

---

## Variable Definitions

| Variable | Type | Description |
|--------|------|-------------|
| `country` | string | Country name |
| `country_code` | string | ISO alpha-3 country code |
| `year` | integer | Calendar year (2015–2022) |
| `oecd_value` | float | OECD reported out-of-pocket healthcare expenditure per capita (PPP-adjusted current international dollars) |
| `who_value` | float | WHO / World Bank reported out-of-pocket healthcare expenditure per capita (PPP-adjusted current international dollars) |
| `abs_diff` | float | Absolute difference between OECD and WHO values |
| `pct_diff` | float | Percentage difference between OECD and WHO values |

---

## Derived Variables

### Absolute Difference
abs_diff = oecd_value − who_value

This measures the absolute difference between the two reporting systems.

---

### Percentage Difference
pct_diff = (abs_diff / who_value) × 100

This measures the relative difference between OECD and WHO values.

---

## Units

All expenditure values are expressed as:
PPP-adjusted current international dollars per capita

Purchasing Power Parity (PPP) allows comparison of spending levels across countries by adjusting for cost-of-living differences.

---

## Countries Included

- United States (USA)
- Canada (CAN)
- United Kingdom (GBR)
- Japan (JPN)
- China (CHN)

---

## Time Coverage
2015–2022

Each country has observations for all years in the dataset, forming a **balanced panel dataset**.

---

## File Formats

Two dataset formats are provided:

### Long Format
oop_oecd_vs_who_long_2015_2022.csv

Used for statistical analysis and panel data modeling.

### Wide Format
oop_oecd_vs_who_wide_2015_2022.csv

Reshaped format useful for visualization and reporting.

---

## Notes

- Minor discrepancies between OECD and WHO values may occur due to revision cycles and reporting updates.
- Out-of-pocket expenditures do **not include insurance premiums**.
