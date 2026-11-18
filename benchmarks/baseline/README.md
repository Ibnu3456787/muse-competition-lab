# Baseline benchmarks

Scores before optimization — the starting points every improvement is
measured against. All figures verified from competition results or local
grader runs; see `postmortems/competition-results.md` for sources.

## BTC races (live results)

| Bot | Race | Net PnL | Trades | Max drawdown |
|---|---|---|---|---|
| BTC-1 (extreme-dip z-score) | 20261111-0801 | −$17.60 (−1.76%) | 1 | — |
| BTC-2 (two-phase dip-swing) | 20261112-1439 | −$31.20 (−3.12%) | 8 | 3.32% |

Winner benchmarks in the same races: +$7.57 (5 trades) and +$9.19 (5 trades).

## Forecast calibration

| Entry | Our score | Baseline | Verdict |
|---|---|---|---|
| roblox-up-and-coming-forecast-01 | log_score −42.4 | house baseline (better) | **Below baseline — prize-ineligible** |

## Vision / geolocation

| Entry | Our score | Winner |
|---|---|---|
| photo-geolocator-01 | 281,000; median error 9,432 km | 492,000; median error 89 km |

Note: our photo-geolocator graded with no provider key (300× 401) — the
baseline reflects an infrastructure failure, not the model's capability.

## Judged competitions (baseline match records)

Every judged entry: exactly 6 matches (ai-joke 8), win rate below 50%
except coolest-art-01 (3W/2D/1L). Winners: 27–107 matches. See
`competitions/makefun/judged-losses.md`.
