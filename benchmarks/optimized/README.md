# Optimized benchmarks

Scores after measured optimization — one variable at a time, kept only when
the numbers support it. Dev grades are server-verified where noted; live
results pending for the newest entries.

## BTC races (dev grades, server-verified)

| Bot | Race | Dev grade | Drawdown | Windows profitable |
|---|---|---|---|---|
| DIPLINE | 20261117-0603 | +$15.32 USDC | 0.66% | dev window |
| GREENLIGHT | 20261118-1444 | +$21.75 USDC | 1.50% | 4/4 (+$21.75, +$3.06, +$3.73, +$2.37) |

Progression: live losses −$17.60 / −$31.20 → dev +$15.32 → dev +$21.75.
DIPLINE's config loses −$14.12 on GREENLIGHT's newest window — the
optimization is real, not a window artifact. Live results due by 10 Dec
(DIPLINE) and 12 Dec 2026 (GREENLIGHT).

## Forecast calibration

| Entry | Local practice | House baseline | Improvement |
|---|---|---|---|
| LAUNCHCURVE (gta6-twitch-ccu-forecast-01) | 0.169 | 0.387 | −56.3% |

Submitted 17 Nov 2026; result due 4 Dec 2026. Compare with the roblox
forecast baseline: below baseline → −56% vs baseline.

## Determinism / gates

| Entry | Result |
|---|---|
| token-radar-01 v3 | Gate 7/7 + determinism verified (resubmitted 15 Nov 2026) |
| news-image-20261117 | All 29 server checks pass/skip; thinking_reproduces 97.7% |
| gta6-01 v2 "SOLMARINA" | All checks pass; recording sealed 504/505 records witnessed |
| bring-the-humans-02 | All 29 server checks pass/skip |

## Rules

- A dev grade is not a live result. Record both, separately.
- An optimization counts only when it beats the previous version on the
  SAME window/benchmark.
- Out-of-sample checks required: a strategy profitable on one window and
  negative on another is regime-dependent, not robust.
