# Data layout

This project keeps datasets staged by lifecycle to support reproducibility and version control.

- `raw/`: Direct pulls from MLB schedule endpoints and Baseball Reference (daily hitters/pitchers, starters).
- `interim/`: Rolling team aggregates (e.g., 15-day hitter/pitcher summaries).
- `processed/`: Final modeling tables (e.g., `years_baseball.csv`).
- `metrics/`: Correlation tables and summary outputs (e.g., `baseball_correlations.csv`).

When adding new files, include a short note in the directory README or a companion `*_README.md` describing source, grain, and filters applied.
