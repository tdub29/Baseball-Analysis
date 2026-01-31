# Source code layout

This directory is organized to mirror the production pipeline stages used in this project.

- `ingest/`: Scripts that pull raw game schedules, daily hitter/pitcher stats, and probable starters.
- `features/`: Scripts that build rolling team aggregates and merge raw sources into modeling tables.
- `modeling/`: Scripts that fit expected score regressions and save model artifacts.
- `evaluation/`: Scripts that quantify accuracy, correlations, and win-rate performance.
- `deployment/`: Scoring helpers and model outputs used downstream.
- `legacy/`: The original end-to-end pipeline preserved for reference and provenance.
