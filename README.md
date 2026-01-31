# Baseball Analysis

A production-ready, reproducible data science workspace for exploring MLB game outcomes and building team-level run expectancy and win-probability signals from daily batting and pitching data.

This repository captures the full lifecycle of the project: **data ingestion** (MLB schedules and daily Baseball Reference stats), **feature engineering** (rolling team-level aggregates and advanced metrics), **modeling** (expected score regressions), **evaluation** (correlation + win-rate analysis), and **deployment artifacts** (model coefficients and scoring outputs).

## Project goals (2023–2019 seasons)
- Build a season-level dataset that links game outcomes to rolling offensive/defensive indicators.
- Measure which short-term stat windows are predictive of runs scored.
- Translate expected score signals into win-probability features and evaluate their historical performance.

## Repository layout (production-ready structure)
Each top-level directory is purpose-built for this project and has a clear responsibility in the pipeline.

| Directory | Purpose | Why it exists here |
| --- | --- | --- |
| `config/` | Project configuration (season ranges, lookback windows, paths). | Makes pipeline parameters explicit and versioned so runs are reproducible and auditable. |
| `data/` | Project datasets split by lifecycle stage. | Separates raw pulls from interim transforms and final modeling tables. |
| `docs/` | Living documentation (data dictionaries, methodology notes). | Keeps project knowledge with the code for collaboration. |
| `models/` | Serialized model artifacts (RDS/coefficients). | Allows deployment and scoring without re-training. |
| `reports/` | Figures and evaluation outputs. | Centralizes visuals/metrics used in write-ups and presentations. |
| `src/` | All pipeline code, organized by stage. | Enforces a clean separation of responsibilities. |
| `tests/` | Automated checks and validation scripts. | Protects data integrity and future refactors. |

### `data/` layout
- `data/raw/`: Direct downloads (MLB schedules, daily hitter/pitcher tables, starters).
- `data/interim/`: Intermediate rolling stats (team-level 15-day aggregates).
- `data/processed/`: Final modeling table used in training/evaluation (`years_baseball.csv`).
- `data/metrics/`: Correlation tables and other computed metrics (`baseball_correlations.csv`).

## Code organization
All pipeline code lives in `src/` and is structured by stage:
- `src/ingest/` — data collection and raw dataset creation.
- `src/features/` — feature engineering and joins.
- `src/modeling/` — expected score models and coefficient outputs.
- `src/evaluation/` — accuracy, correlation, and win-rate analysis.
- `src/deployment/` — scoring helpers and artifacts for downstream use.
- `src/legacy/` — the original end-to-end script, retained for provenance.

## Naming conventions (project-specific)
- **Files:** lowercase snake_case with descriptive nouns or verbs (e.g., `team_batting_rolling.csv`, `build_expected_score_model.R`).
- **R objects:** lowercase snake_case for data frames, verb-based for functions (e.g., `calculate_woba()`), and explicit prefixes for home/away (`home_`, `away_`).
- **Models/outputs:** include season range and version when applicable (e.g., `expected_score_model_2016_2019.rds`).

## Configuration management
Pipeline defaults live in `config/baseball.yml`:
- `season_start`, `season_end`: season boundaries used in ingestion.
- `lookback_days`: rolling window length for batter/pitcher aggregation.
- `min_plate_appearances`: data quality filter for team stats.
- `paths`: explicit project-relative directories for outputs.

Changing the config keeps parameter choices tracked in Git, which makes results reproducible and peer-reviewable.

## Getting started
1. **Install R dependencies** used in the legacy pipeline (baseballr, dplyr, sqldf, ggplot2, rsq, tseries).
2. **Review configuration:** update `config/baseball.yml` for the season range or lookback window you want to analyze.
3. **Run the legacy pipeline** (to regenerate data end-to-end):
   ```bash
   Rscript src/legacy/projectbaseball_full_pipeline.R
   ```
4. **Inspect outputs** in `data/processed/` and `data/metrics/`.

## Documentation expectations
See `docs/README.md` for the data dictionary outline, feature explanations (e.g., wOBA, FIP), and model assumptions to maintain consistency across collaborators.

## Collaboration notes
- Every new dataset should include a short README in its directory (source, filters, grain).
- Keep all parameters in `config/baseball.yml` and avoid hard-coded paths.
- Prefer scripts in `src/` over ad-hoc notebooks to ensure reproducibility.
