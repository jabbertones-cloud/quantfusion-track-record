# QuantFusion paper-trading track record

> Cryptographically-timestamped forecasts from the QuantFusion 22-strategy
> paper-trading system. **Paper mode only** -- org policy blocks live trading
> until 3 consecutive profitable paper months.

[![Brier (overall)](https://img.shields.io/badge/brier-n/a-lightgrey)](metrics/overall.json)
[![Forecasts logged](https://img.shields.io/badge/forecasts-10-blue)](forecasts/)
[![Days running](https://img.shields.io/badge/days_running-1-blue)](metrics/overall.json)
[![Best DSR](https://img.shields.io/badge/best_DSR-0.000-yellow)](metrics/by_strategy.json)

## Provenance

Every forecast in this repo is committed to git **before** the market resolves.
This makes the forecast cryptographically anchored: GitHub signs every commit
with its timestamp, and the commit SHA is immutable.

- **GitHub commit chain:** see [Commits](../../commits/main).
- **IPFS pins** (if Pinata configured): hash recorded per batch in `metrics/overall.json`.
- **Schema:** `docs/SCHEMAS.md`.

## SOT thresholds (institutional grade)

| Metric | Institutional | Significant |
|---|---|---|
| Brier score | < 0.10 (Kalshi tier) | < 0.50 (beats 50/50) |
| Deflated Sharpe (Bailey/Lopez de Prado 2014) | > 0.95 | > 0.85 |
| PBO (Bailey/Borwein) | < 0.50 | -- |

## Summary by strategy

_No resolved forecasts yet. Awaiting first market resolutions._

## Overall

- **Total forecasts logged:** 10
- **Resolved:** 0
- **Unresolved (open):** 10
- **Brier (overall):** n/a
- **PnL (paper):** $0.00
- **Last updated (UTC):** 2026-07-23T21:44:07.800651+00:00

## How to verify

```bash
git clone https://github.com/jabbertones-cloud/quantfusion-track-record.git
cd quantfusion-track-record
# Each forecast was committed BEFORE its market resolved.
git log --format="%h %ad %s" --date=iso forecasts/ | head -20

# Replay the same strategies on the public Jon-Becker academic dataset:
git clone https://github.com/Jon-Becker/prediction-market-analysis
# then run quantfusion-rf/backtest/jon_becker_backtester.py
```

## Backtest report

See `docs/BACKTEST.md` for the latest CPCV-validated backtest on the
Jon-Becker dataset (DSR + PBO computed per institutional SOT).

## Disclaimer

Paper mode. Org policy blocks live trading. No fiduciary advice.
