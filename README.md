# gpstocks-data

Scoring artefacts produced by [`mgb9/gpstocks`](https://github.com/mgb9/gpstocks).
**Do not edit by hand.** This branch is force-pushable; commits are made
automatically by the Pi cron after each scoring run.

## Layout

- `stocks.json`, `stocks_prev.json`, `stocks_metadata.json` — Buy-Now cohort and supporting data
- `macro.json`, `insiders.json`, `benchmarks.json`, `regime_log.json` — auxiliary panels
- `prices/<TICKER>.json` — per-ticker price history
- `snapshots/stocks_YYYY-MM-DD.json` — daily snapshot archive
- `quarterly_fundamentals/<TICKER>.json` — point-in-time vintage data
- `paper_portfolio.json`, `factor_etfs.json`, `score_stability.json`,
  `backtest_observations.json`, `factor_decomposition.json`, `rules_config.json`,
  `universe_history.json`

## Served via

`https://cdn.jsdelivr.net/gh/mgb9/gpstocks-data@main/<path>`

## Push cadence

- Daily 10:00 / 16:30 UK time (full data refresh, includes scoring)
- Every 2 hours during US market hours (price-only refresh; commits include `[skip ci]`)

## Discipline

The site treats this repo as untrusted source-of-truth: every artefact's
freshness is reported via the in-file `last_scored_at` / `last_pushed_at`
timestamps in `stocks_metadata.json`, not via HTTP headers or commit times.
