# Data Dictionary

## Dataset Metadata

- Dataset names: 1) oop_oecd_vs_who_long_2015_2022.xls  
                 2) oop_oecd_vs_who_wide_2015_2022.xls  
                 3) oecd_vs_wb_vs_who_oop_ppp_2015_2022_comparison.xls   
- Created on 2028-02-21  
- Created by: Thanh Huynh  
- Primary source(s):WHO Global Health Expenditure Database, Years 2015-2022  
                    OECD Health Statistics, Years 2015-2022  
- Geographic scope: CANADA, CHINA, GREAT BRITAIN, JAPAN, USA  
- Time coverage: YEARS 2015 - 2022  
- License / usage constraints:
OECD Data: key constraints include a maximum of 60 data downloads per hour; ban on accessing data via VPNs WHO Global Healther Expenditure Database: a user cannot use the name or emblem of the WHO without prior written approval, nor imply WHO endorsement of his/her work. Data must not be misrepresented, and a user is responsible for checking if datasets are credited to other sources.  

## File Name and Variable Descriptions  

**File name: oop_oecd_vs_who_wide_2015_2022.xls**  
- **Layout**: Cross-tabulated, "wide"; designed for row-by-row comparison with oop_oecd_vs_who_long_2015_2022.xls. Pivoted format where metrics are spread across columns. Note: Due to .csv conversion, headers for who_value and oecd_value repeat. Columns follow the country sequence CAN, CHN, GBR, JPN, USA  
- **Data Quality Status**: converted .csv   *warning*: headers may be ambiguous due to the conversion via web-scraping  
- **Number of rows**: 40  
- **Number of columns**: 8  
- **Column grouping**:
  * Country_code : 3-alpha character code representing country  
  * Year: integer, representing fiscal year  
  * abs_diff: float, absolute difference between OECD/WHO for each country  
  * oecd_value: float/decimal, raw value from OECD Health Statistics for each country in the same sequence  
  * who_value: float/decimal, amount spent on healthcare expressed as a percentage (%) of the country's Gross Domestic Product (GDP)  
  * pct_diff: float, percentage variance for each country in the same sequence  


**File name: oop_oecd_vs_who_long_2015_2022.xls**  
- **Layout**: Clean format where each row represents a single Country-Year observation. This data is used for data analysis and visualization. Columns follow the country sequence CAN, CHN, GBR, JPN, USA  
- **Data Quality Status**: converted .csv   *warning*: headers may be ambiguous due to the conversion via web-scraping  
- **Number of rows**: 40  
- **Number of columns**: 8  


**File name: oecd_vs_wb_vs_who_oop_ppp_2015_2022_comparison.xls**  
- **Layout**: Tabular comparison of 3 different global sources.  The country sequence is CAN, CHN, GBR, JPN, USA  
- **Data Quality Status**: converted .csv   *warning*: headers may be ambiguous due to the conversion via web-scraping  
- **Number of rows** 40  
- **Number of columns**: 8  
- **Column grouping**:  *Note re Wold Bank Open Data portal values listed below*:    
The values are derived from the WHO GHED but is included here to cross-reference data consistency across different international reporting platforms.  The multiple diff columns in this file are used for data triangulation. While the World Bank frequently mirrors WHO data, there are occasional discrepancies due to different update cycles or rounding methods. These columns identify where the 3 sources disagree on consumer healthcare costs for the Canada, China, Great Britain, Japan, and the US.  
  
                    year, integer:  fiscal year of the data, range 2015–2022  
                    country_code, string: 3-letter ISO 3166-1 alpha-3 country code  
                    country, string:	full name of the country  
                    oecd_value, float:	healthcare spending (% of GDP) from OECD Health Statistics  
                    wb_value, float:	healthcare spending (% of GDP) from the World Bank Open Data portal  
                    who_value, float:	 healthcare spending (% of GDP) from the WHO Global Health Expenditure Database  
                    abs_diff_oecd_wb, float:	absolute difference between the OECD and World Bank values  
                    pct_diff_oecd_wb, float:  percentage variance between OECD and World Bank values  
                    abs_diff_oecd_who, float:	 absolute difference between the OECD and WHO values  
                    pct_diff_oecd_who, float:	 percentage variance between OECD and WHO values  
                    abs_diff_wb_who, float:	 absolute difference between the World Bank and WHO values  
                    pct_diff_wb_who,	float:	percentage variance between World Bank and WHO values  

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

Minor discrepancies between OECD and WHO values due to:  
  - Revision timing  
  - Update cycles  
  - PPP (purchasing power parity) adjustments may vary slightly across reporting system  
  - COVID-19 may distort short-term comparability  
  - OOP (out-of-pocket), excludes insurance premiums  

## Provenance  

- Raw file/API endpoints: https://api.worldbank.org/v2/country/{}/indicator/{}?format=json&per_page=500; https://sdmx.oecd.org/public/rest/data  
- Extraction date: 2026-02-21  
- Transformation notebook/script: DSCI-511-GroupProject-DataGather (28Feb2026).ipynb  
- Output artifact(s): oop_oecd_vs_who_long_2015_2022.xls : 2015-2022 year trend analysis for OOP and PPP across the 5 selected countries  
                      oop_oecd_vs_who_wide_2015_2022.xls : 2015-2022 year country-spending comparison  
                      oecd_vs_wb_vs_who_oop_ppp_2015_2022_comparison.xls : for data validation - auditing of discrepancies between WHO GHED and OECD data  

## Change Log  
  
| Date | Version | Author | Change summary |
| :--- | :--- | :--- | :--- |
| 2026-02-20 | v0.0 | Sharon Robinson | Initial draft |
| 2026-03-01 | v1.0 | Sharon Robinson | 1st amendment |

