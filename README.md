# Bitcoin Market Sentiment × Trader Performance

> Exploring the relationship between the Bitcoin Fear & Greed Index and Hyperliquid trader behavior to uncover hidden patterns and drive smarter trading strategies.

---

<img src="https://github.com/nikhilyadav45/Data-Analysis-Assignment/blob/main/Dashboard.png"></img>

## Overview

This project analyzes **211,224 trades** from 32 Hyperliquid accounts alongside the daily Bitcoin Fear & Greed Index to answer a core question: *does market sentiment predict how profitably traders behave?*

The answer is yes — and the patterns are both consistent and actionable.

---

## Datasets

| File | Description | Records | Date Range |
|---|---|---|---|
| `historical_data.csv` | Hyperliquid trader execution data | 211,224 trades | Jan 2024 – May 2025 |
| `fear_greed_index.csv` | Bitcoin Fear & Greed Index (daily) | 2,644 rows | Feb 2018 – May 2025 |

### Columns — historical_data.csv

| Column | Description |
|---|---|
| `Account` | Trader wallet address |
| `Coin` | Asset traded (BTC, ETH, HYPE, SOL, etc.) |
| `Execution Price` | Fill price |
| `Size Tokens` | Position size in tokens |
| `Size USD` | Position size in USD |
| `Side` | BUY / SELL |
| `Timestamp IST` | Trade timestamp (IST, DD-MM-YYYY HH:MM) |
| `Start Position` | Position size before this trade |
| `Direction` | Open Long / Close Long / Open Short / Close Short / etc. |
| `Closed PnL` | Realized profit or loss (0 for non-closing trades) |
| `Transaction Hash` | On-chain transaction ID |
| `Order ID` | Hyperliquid order identifier |
| `Crossed` | Whether the order crossed the spread |
| `Fee` | Trading fee paid |
| `Trade ID` | Unique trade identifier |
| `Timestamp` | Unix timestamp |

### Columns — fear_greed_index.csv

| Column | Description |
|---|---|
| `timestamp` | Unix timestamp |
| `value` | Sentiment score (0–100) |
| `classification` | Extreme Fear / Fear / Neutral / Greed / Extreme Greed |
| `date` | Date (YYYY-MM-DD) |

---

## Methodology

1. Parse `Timestamp IST` (DD-MM-YYYY format) into a normalized `date` field
2. Merge trader data with the Fear & Greed Index on `date`
3. Filter to closed trades (`Closed PnL != 0`) for performance analysis — 104,408 trades
4. Aggregate PnL, win rate, trade count, and sizing by sentiment classification
5. Analyze long/short positioning, monthly trends, and per-account performance

---

## Key Results

### Overall Performance

| Metric | Value |
|---|---|
| Total Closed PnL | $10,296,959 |
| Overall Win Rate | 83.2% |
| Avg PnL per Trade | $98.62 |
| Unique Traders | 32 |
| Best Month | Dec 2024 (+$3,005,071) |
| Worst Month | Aug 2024 (-$106,817) |

### Performance by Sentiment

| Sentiment | Total PnL | Avg PnL/Trade | Win Rate | Avg Trade Size |
|---|---|---|---|---|
| Extreme Fear | $739,110 | $71.03 | 76.2% | $5,350 |
| Fear | $3,357,155 | $112.63 | 87.3% | $7,816 |
| Neutral | $1,292,921 | $71.20 | 82.4% | $4,783 |
| Greed | $2,150,129 | $85.40 | 76.9% | $5,737 |
| Extreme Greed | $2,715,171 | $130.21 | 89.2% | $3,112 |

### Long/Short Bias by Sentiment

| Sentiment | Long % | Short % |
|---|---|---|
| Extreme Fear | 68.8% | 31.2% |
| Fear | 62.1% | 37.9% |
| Neutral | 61.7% | 38.3% |
| Greed | 42.3% | 57.7% |
| Extreme Greed | 45.1% | 54.9% |

---

## Key Insights

**Fear is the most active and lucrative regime** — Fear periods generated $3.36M in PnL with an 87.3% win rate and the largest average position sizes ($7,816). Traders buy the dip with conviction, and it consistently pays off.

**Extreme Greed delivers the best per-trade alpha** — The highest avg PnL per trade ($130.21) and win rate (89.2%) occur during peak euphoria. Traders flip net short and capture mean-reversion with precision.

**Contrarian positioning is the core strategy** — Long bias of 69% in Extreme Fear flips to 55% short in Extreme Greed. This sentiment-inverse positioning is the primary driver of profitability.

**Dec 2024 was the defining event** — A single month produced $3M (29% of all-time PnL), driven by Extreme Greed conditions, the HYPE token surge, and the BTC post-election rally.

**Returns are highly concentrated** — The top 2 accounts earned 36% of all profits ($3.74M). The top 5 earned 62%. Elite execution, not broad luck, explains the skew.

---

## Files

```
├── README.md                              ← this file
├── historical_data.csv                    ← Hyperliquid raw trade data
├── fear_greed_index.csv                   ← Bitcoin Fear & Greed Index
└── bitcoin_sentiment_trader_analysis.md  ← full written analysis & findings
```

