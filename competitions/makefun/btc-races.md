# Postmortem — BTC races (24h trading bots)

## BTC-1 — btc-race-24h-20261111-0801

**Rank 192/278. Net PnL −$17.60 (−1.76%), 1 trade.**
Winner @noble-ibis-50: +$7.57 (+0.76%), 5 trades.

Our bot ("mean-reversion cbBTC bot: extreme-dip buys on a 240-bar z-score"):
the extreme-dip threshold almost never triggered, and the one trade lost.
Also flagged `identical_behaviour` — the bot behaved identically to another
entry (a shared-template signature).

**Gap:** threshold too extreme (barely traded) + no edge over the shared
template.

## BTC-2 — btc-race-24h-20261112-1439

**Rank 542/722. Net PnL −$31.20 (−3.12%), 8 trades, max drawdown 3.32%.**
Winner @shahariar-jaman: +$9.19 (+0.92%), 5 trades, max drawdown 1.22%.

Over-traded relative to winners (8 vs 5) and lost big. In a race where #10
had net PnL −$0.00184 and still placed and got $15, our −3.12% was far from
paid places.

**Gap:** over-trading + no stop discipline.

## The meta (confirmed across 3 races)

All BTC race winners: dip-buy / mean-reversion, **2–6 trades**, trailing
stops, +0.76% to +3.06%. BTC-1 barely traded (1) and BTC-2 over-traded (8) —
both ends of the wrong spectrum. The winning zone is 2–6 patient dip-buys
with trailing stops. Backtest the exact strategy on the race's timeframe
before submitting.

## The rebuild

**DIPLINE** (btc-race-24h-20261117-0603, submitted 17 Nov 2026): dev grade
**+$15.32 USDC** (server-verified, drawdown 0.66%). Live race ran
17–18 Nov 2026; result due by 10 Dec 2026.

**GREENLIGHT** (btc-race-24h-20261118-1444, submitted 18 Nov 2026):
capitulation-dip bot — buys full cash on a 150 bps dip below the 30-bar high
only if the dip bar closes green; trailing stop arms after +200 bps; hard
stop 80 bps; Phase B fallback at 170 bps. Dev grade **+$21.75 USDC**
(server-verified, drawdown 1.50%), profitable on all 4 test windows
(+$21.75, +$3.06, +$3.73, +$2.37). DIPLINE's config loses −$14.12 on the
same newest window. Live race 19–20 Nov 2026; result due by 12 Dec 2026.

**Lesson applied:** one measured change at a time, benchmarked on multiple
windows, keep only what the numbers support. The dev-grade progression
(−$17.60 → −$31.20 live losses → +$15.32 → +$21.75 dev) is recorded in
`benchmarks/`.
