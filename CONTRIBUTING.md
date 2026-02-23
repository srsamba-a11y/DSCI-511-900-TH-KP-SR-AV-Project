# Contributing

Thanks for your interest in contributing to this project.

## Scope

This repository focuses on building a reproducible, cross-country dataset of out-of-pocket healthcare costs for:

- United States
- Canada
- United Kingdom
- Japan
- China

## How to contribute

1. Fork the repository and create a feature branch.
2. Make focused changes (one logical update per pull request).
3. Include a short summary of what changed and why.
4. Open a pull request with evidence that your changes run correctly.

## Contribution checklist

Before opening a pull request:

- Confirm source URLs are public and stable
- Document variables added/changed in the data dictionary
- Describe all cleaning and standardization steps
- Note assumptions (currency conversion, PPP handling, missing value logic)
- Verify outputs are reproducible from notebook/script steps

## Data standards

Use these standards for all new or changed data:

- Keep one row per country-year for core tables
- Use consistent country names and ISO3 codes
- Keep column names snake_case
- Preserve units in column definitions
- Never overwrite raw source files; write transformed outputs separately

## Pull request format

Please include:

- Problem statement
- Data source(s) used
- Processing steps performed
- Output files produced
- Limitations or caveats

## Code and notebook expectations

- Keep notebooks and scripts readable and modular
- Avoid hard-coded local machine paths
- Prefer deterministic transformations
- Add brief markdown notes before complex processing blocks

## Reporting issues

When filing an issue, include:

- Expected behavior
- Actual behavior
- Steps to reproduce
- File names and sample rows (if relevant)

## Team contacts

- Ari Voluck — av532@drexel.edu
- Khushi Patel — kp3382@drexel.edu
- Sharon Robinson — slr424@drexel.edu
- Thanh Huynh — th3238@drexel.edu
