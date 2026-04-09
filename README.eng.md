# SMC — Smart Money Concepts

Pine Script indicators for TradingView based on Smart Money Concepts (SMC) methodology.

---

## Active Indicators

### Range STR — Swing Structure Detection
**File:** [`strategies/swing-range.pine`](strategies/swing-range.pine)

3-state machine for detecting swing structure: BOS (Break of Structure), Callback (retracement), and CHoCH (Change of Character). Identifies external structure breaks while filtering out internal (noise) moves.

**How it works:**
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

| State | Description |
|-------|-------------|
| **hasBOS** | Structure broken in trend direction, tracking new extreme (HH or LL) |
| **hasCallback** | Retracement confirmed, tracking HL/LH, waiting for next break |
| **hasCHoCH** | Change of character — trend reversed, tracking extreme in new direction |

**Inputs:**

| Parameter | Default | Description |
|-----------|---------|-------------|
| Grace period | 20 bars | Initial range detection period |
| Retracement % | 40% | Callback confirmation threshold |
| Show range box | true | Display confirmed range on chart |
| Show labels | false | Debug labels (BOS/CB/CHoCH) |

---

### Volatility News Stats
**File:** [`volatility-news-stats.pine`](volatility-news-stats.pine)

Volatility analysis indicator combining ATR, Bollinger Bands width, and Historical Volatility (HV). Shows how volatility behaves around news events — key insight: vol drops ~12h before major news, then spikes. Works across EUR, BTC, Gold.

---

### Time of Week
**File:** [`time-of-weak.pine`](time-of-weak.pine)

Visual day-of-week overlay. Marks each trading day (пн/вт/ср/чт/пт/сб/вс) with color labels on the chart. Helps identify weekly patterns — e.g. Monday opens (green) vs Friday closes (red).

---

## Archive (tmp/)

> Old versions and experimental indicators. **Not actively used.** Kept for reference.

### [`strategies/tmp/`](strategies/tmp/)
| File | Description |
|------|-------------|
| `swing-range2.pine` | Range STR backup — simpler 2-state version (hasBOS / not hasBOS) |
| `swing-abc.pine` | ABC swing logic — basic A→B→C point tracking |
| `swing-bos.pine` | BOS zigzag — break of structure detection without callback |
| `swing-detection.pine` | Basic pivot zigzag using `ta.pivothigh` / `ta.pivotlow` |

### [`tmp/`](tmp/)
| File | Description |
|------|-------------|
| `v.v1.pine` | Volatility indicator v1 |
| `v-stats.v1.pine` | Volatility stats v1 |
| `volatility-news.pine` | News-based volatility overlay (earlier version) |

---

## Setup

1. Open TradingView → Pine Editor
2. Paste code from any `.pine` file
3. Add to chart
4. Recommended: **BTCUSDT Bybit**, test on multiple timeframes (1h, 4h, 1D)
