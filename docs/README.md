# Documentation

This folder contains project-specific documentation to keep the analysis reproducible and collaborator-friendly.

## What to keep here
- **Data dictionary:** field definitions for `data/processed/years_baseball.csv` (stat names, units, grain).
- **Feature notes:** explanations of derived metrics (wOBA, FIP, OPS, expected score formulas) and any regression coefficients.
- **Model assumptions:** sample windows, minimum PA filters, and any regression-to-mean adjustments.
- **Known data limitations:** scraping limits, missing-day handling, and season boundary exceptions.

## Suggested files
- `data_dictionary.md`
- `feature_engineering_notes.md`
- `modeling_assumptions.md`
- `evaluation_summary.md`
