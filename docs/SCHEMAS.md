# Forecast schema

Every file under `forecasts/` follows this institutional shape:

```json
{
  "forecast_id": "fc_<sha256(market_id+ts)[:12]>",
  "market_venue": "polymarket|kalshi",
  "market_id": "<venue native id>",
  "market_question": "Will X happen?",
  "market_end_date": "ISO 8601",
  "signal_emitted_at": "ISO 8601",
  "strategy_key": "weather_arb_v1",
  "agent_id": "quantfusion_weather_arb_paper",
  "predicted_probability_yes": 0.62,
  "market_implied_probability_yes": 0.54,
  "edge_pct": 0.08,
  "signal_side": "LONG|SHORT|NONE",
  "stake_usd_paper": 100.0,
  "rationale_hash": "sha256_of_market_snapshot",
  "resolved": false,
  "resolution": null,
  "resolved_at": null,
  "pnl_usd": null,
  "brier_contribution": null
}
```

After resolution, the same file is updated in-place with `resolved=true`,
`resolution` (0|1), `resolved_at`, `pnl_usd`, and `brier_contribution`. The
diff is visible in git history -- proof that we did not edit the prediction.

## Metrics files

- `metrics/overall.json` -- aggregate Brier, PnL, calibration bins
- `metrics/by_strategy.json` -- per-strategy rolling Brier (7d/30d/all), DSR

## SOT references

- Brier institutional: < 0.10 (Kalshi tier)
- Brier "beats 50/50": < 0.50
- Deflated Sharpe Ratio: Bailey & Lopez de Prado, 2014
- PBO via CSCV: Bailey, Borwein, Lopez de Prado, Zhu, 2014
