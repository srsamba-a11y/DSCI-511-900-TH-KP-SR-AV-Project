# Data Dictionary Template

Use this template to document each dataset/table produced in the project.

## Dataset Metadata

- Dataset names: https://sdmx.oecd.org/public/rest/data; https://api.worldbank.org/v2/country/{}/indicator/{}?format=json&per_page=5000
- Created on (2028-02-21):
- Created by: Thanh Huynh
- Primary source(s):WHO Global Health Expenditure Database, Years 2015-2022; OECD Health Statistics, Years 2015-2022
- Geographic scope: USA, CANADA, UK, CHINA, JAPAN
- Time coverage: YEARS 2015 - 2022
- License / usage constraints:  OECD Data: key constraints include a maximum of 60 data downloads per hour; ban on accessing data via VPNs
                                WHO Global Healther Expenditure Database: a user cannot use the name or emblem of the WHO without prior written
                                approval, nor imply WHO endorsement of his/her work. Data must not be misrepresented, and a user is responsible
                                for checking if datasets are credited to other sources.

## Table-Level Description

- Table/file name: oop_table
- Grain (row definition):
- Key columns: REF_AREA": {"REF_AREA":"country", "TIME_PERIOD": "year", "OBS_VALUE": "value"}
- Join keys (if applicable):
- Number of rows: 224
- Number of columns: 7
- Missingness summary: lack of data transparency for Japan and China

- Table/file name: oop_table
- Grain (row definition):
- Key columns: REF_AREA": {"REF_AREA":"country", "TIME_PERIOD": "year", "OBS_VALUE": "value"}
- Join keys (if applicable):
- Number of rows: 224
- Number of columns:
- Missingness summary:

## Variable Definitions

| Column name | Type | Description | Unit | Allowed values / format | Missing value handling | Source field | Transformation notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| country | string | Country name | N/A | United States, Canada, United Kingdom, Japan, China | Not allowed in final output | Country label from source | Standardized to canonical names |
| iso3 | string | ISO 3166-1 alpha-3 code | N/A | USA, CAN, GBR, JPN, CHN | Not allowed in final output | Source country code or lookup table | Validated against controlled list |
| year | integer | Observation year | year | 4-digit year | Remove rows with invalid year | Date/year field | Cast to int |
| out_of_pocket_ppp | float | Out-of-pocket health expenditure per capita (PPP) | International $ | Non-negative numeric | Keep as null when missing | Indicator SH.XPD.OOPC.PP.CD | Parsed from source API response |

Add one row per variable in your dataset.

## Standardization Rules

- Country names normalized to a single canonical format
- Monetary values documented with exact unit and conversion basis
- Time variables standardized to calendar year
- Duplicate country-year rows resolved with documented tie-break logic

## Data Quality Checks

- Uniqueness check on country-year key
- Type validation for numeric and date fields
- Range checks for expenditure values (non-negative)
- Missingness threshold checks by country and year
- Cross-source consistency checks when merged variables are used

## Assumptions and Limitations

- Definition differences across countries for out-of-pocket spending
- Potential gaps in time coverage by source
- Currency/PPP assumptions and reference years
- Reporting lag and revisions in official sources

## Provenance

- Raw file/API endpoint:
- Extraction date:
- Transformation notebook/script:
- Output artifact(s):

## Change Log

| Date | Version | Author | Change summary |
| --- | --- | --- | --- |
| 2026-03-01 | v0.1 | Sharon Robinson, Khushi Patel, Thanh Huynh, Ari Voluck | Initial draft |
