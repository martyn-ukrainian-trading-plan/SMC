# SMC — Smart Money Concepts

Pine Script indicators for TradingView based on Smart Money Concepts (SMC) methodology.

## Strategies

| Indicator | File | Description |
|-----------|------|-------------|
| **Range STR** | [`strategies/swing-range.pine`](strategies/swing-range.pine) | Swing structure detection with 3-state machine: BOS, Callback, CHoCH. Identifies external structure breaks while ignoring internal moves. |

## Archive

Old/experimental indicators in [`tmp/`](tmp/) and [`strategies/tmp/`](strategies/tmp/):

- `time-of-weak.pine` — Time-of-week analysis
- `volatility-news-stats.pine` — Volatility around news events
- `volatility-news.pine` — News-based volatility overlay
- `v.v1.pine` / `v-stats.v1.pine` — Volatility indicators v1
- `swing-range2.pine` — Range STR backup (2-state version)
- `swing-abc.pine` — ABC swing logic
- `swing-bos.pine` — BOS zigzag
- `swing-detection.pine` — Basic pivot zigzag

## How Range STR works

```
Grace Period → initial range (confHigh / confLow)
     ↓
hasCallback → waiting for BOS or CHoCH
     ↓                          ↓
hasBOS (same dir)         hasCHoCH (dir flip)
     ↓                          ↓
track HH/LL              track HH/LL (new dir)
     ↓                          ↓
40% retrace → hasCallback ←────┘
```

**States:**
- **hasBOS** — structure broken, tracking new extreme (HH or LL)
- **hasCallback** — retracement confirmed, tracking HL/LH, waiting for next break
- **hasCHoCH** — change of character, trend reversed, tracking extreme in new direction

## Setup

1. Open TradingView
2. Pine Editor → paste code from `strategies/swing-range.pine`
3. Add to chart
4. Recommended: BTCUSDT Bybit, test on multiple timeframes

## Inputs

| Parameter | Default | Description |
|-----------|---------|-------------|
| Grace period | 20 bars | Initial range detection period |
| Retracement % | 40% | Callback confirmation threshold |
| Show range box | true | Display confirmed range |
| Show labels | false | Debug labels (BOS/CB/CHoCH) |
