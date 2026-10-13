> **Superseded and archived.** This project has been folded into
> [tdub29/baseball-analytics](https://github.com/tdub29/baseball-analytics). The 604-line R pipeline here was rebuilt there as
> `research/r/mlb/{ingest,features,model,evaluate,run_season}.R` with 59 passing testthat
> assertions, and the original is preserved at `research/r/legacy/`. Read-only from here.

# Baseball Analysis

An R pipeline that predicts MLB runs scored from rolling team batting and pitching stats. It pulls game schedules and daily Baseball Reference tables, builds 15-day team aggregates, fits a regression for expected runs, and checks how often a predicted edge turns into a win.

This was the first version. The maintained version, with Statcast data and a dbt warehouse, is in [baseball-analytics](https://github.com/tdub29/baseball-analytics).

## What is in the repo

- **Pipeline:** `src/legacy/projectbaseball_full_pipeline.R` (604 lines) does ingestion, feature joins, the expected-score regression, correlation analysis and win-rate analysis in one script. It uses `baseballr` for data and `lm` for the model.
- **Modeling table:** `data/processed/years_baseball.csv` holds 5,111 games and 302 columns, with `season` values 2015, 2016 and 2017. Each row joins a game result to rolling batting, starting-pitcher and bullpen stats for both teams.
- **Correlations:** `data/metrics/baseball_correlations.csv` is a 92-column correlation matrix that includes runs scored. The strongest single-stat correlations with runs are about 0.09 (`rpR`, `spSO_perc.1`, `rpER`), so no one rolling stat predicts a game well, which is why the script builds a combined expected-score formula.
- **Config:** `config/baseball.yml` sets the season range (2016 to 2019), the 15-day lookback, the 100 plate-appearance filter and the data paths. Note the script itself still hardcodes its start year, so the config is documentation of intent more than a live switch.

## Run it

Install the R packages the script loads: `baseballr`, `dplyr`, `sqldf`, `ggplot2`, `rsq`, `tseries`. From the repo root:

```bash
Rscript src/legacy/projectbaseball_full_pipeline.R
```

It writes raw pulls to `data/raw/`, rolling aggregates to `data/interim/`, the modeling table to `data/processed/` and the correlation table to `data/metrics/`. It calls live `baseballr` endpoints, so a rerun depends on those sources still serving the same data.

## Layout

| Path | Contents |
| --- | --- |
| `config/` | `baseball.yml` |
| `data/` | `raw/`, `interim/` (empty here), `processed/`, `metrics/` |
| `src/legacy/` | The pipeline script |
| `src/{ingest,features,modeling,evaluation,deployment}/` | Empty placeholders for a planned split of the script; that split happened in `baseball-analytics` |
| `docs/`, `tests/` | Outlines only, no content or tests |

## Status

Archived. No tests, no data dictionary, and no license file. For current work and results, use [baseball-analytics](https://github.com/tdub29/baseball-analytics).
