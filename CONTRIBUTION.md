# Contribution 

Thanks for your interest in contributing to this project.  

## Scope  

This repository focuses on building a reproducible, cross-country dataset of consumer out-of-pocket healthcare costs for the following 5 countries:  

* United States  
* Canada  
* United Kingdom  
* Japan  
* China  

## How to Contribute  

1. Fork the repository and create a feature branch.  
2. Make focused changes (one logical update per pull request).  
3. Include a short summary of what changed and why.  
4. Open a pull request with evidence that your changes run correctly.  

## Contribution Checklist  

Before opening a pull request:  

- Confirm source URLs are public and stable  
- Document variables added/changed in the data dictionary  
- Describe all cleaning and standardization steps  
- Note assumptions (currency conversion, PPP handling, missing value logic)  
- Verify outputs are reproducible from notebook/script steps  

## Data Standards  

Use these standards for all new or changed data:  

- Retain one row per country-year for core tables  
- Use consistent country names, adhering to the ISO 3-alpha country code   
- Standardize column names  
- Preserve units in column definitions  
- Do not overwrite raw source files; develop transformed outputs separately  

## Pull Request Format  

Please include:  

- Problem statement  
- Data source(s) used  
- Processing steps performed  
- Output files produced  
- Limitations or caveats  

## Code and Notebook Expectations  

- Notebooks and scripts should be readable and modular  
- Avoid hard-coded local machine paths  
- Prefer deterministic transformations  
- Add brief markdown notes before complex processing blocks  

## Reporting of Issues  

When filing an issue, include:  

- Expected behavior  
- Actual behavior  
- Steps to reproduce  
- File names and sample rows (if relevant)  

## Team Roles & Attribution  
**Thanh Huynh:  Project Manager, Data Acquisition and Processing Lead**: Oversight of project lifecycle and milestones; executed data extractions via WHO/OECD APIs; developed Python notebooks and presentation materials  
**Sharon Robinson:  Documentation Lead & Data Acquisition Participant**: Authored project README.md, DATA DICTIONARY.md, and CONTRIBUTION.md documents; participation in research and selection of countries for 5-country comparative study; creation and management of GitHub repository and version synchronization  
**Khushi Patel:  Data Veracity, Visualization and Interpretation**: Participation in research and selection of countries for 5-country comparative study; data validation and presentatation preparation  
**Ari Voluck:  Data Veracity, Visualization and Interpretation**: Participation in initial research and selection of countries for 5-country comparative study; data validation and presentatation preparation  

## Team Contacts  

- Thanh Huynh — th3238@drexel.edu  
- Khushi Patel — kp3382@drexel.edu  
- Sharon Robinson — slr424@drexel.edu  
- Ari Voluck — av532@drexel.edu  
