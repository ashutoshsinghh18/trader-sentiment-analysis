# Trader Performance vs Market Sentiment
## Primetrade.ai · Data Science Intern Round-0 Assignment

---

## Setup & How to Run

### Requirements
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Data Files (place in same directory as notebook)
- `historical_data.csv` — Hyperliquid trader data
- `fear_greed_index.csv` — Bitcoin Fear/Greed index

### Run
```bash
jupyter notebook trader_sentiment_analysis.ipynb
```

---

## Methodology

**Data Prep:**  
- Parsed `Timestamp IST` (dd-mm-yyyy HH:MM) → date; aligned on daily date key with Fear/Greed index (2023–2025 overlap).  
- Simplified 5-class sentiment (Extreme Fear / Fear / Neutral / Greed / Extreme Greed) → 3 classes for cleaner analysis.  
- Built daily per-account metrics: PnL, win rate, trade count, avg size, long/short ratio.  
- No missing values in either dataset; no duplicates in fear/greed; trade data had no NaNs.

**Analysis:**  
- Compared PnL, win rate, trade frequency, and position size across sentiment classes.  
- Segmented traders by frequency (infrequent / moderate / frequent), position size, and win consistency.  
- Built a Random Forest classifier to predict daily profitability using behavioral + sentiment features.

---

## Key Insights

| # | Insight |
|---|---------|
| 1 | **Fear days → higher average PnL but lower median PnL.** Extreme outlier winners skew the mean. The median trader does _worse_ on Fear days ($123) than Greed days ($265). |
| 2 | **Traders trade ~37% more on Fear days** (avg 105 trades vs 77 on Greed) with _no improvement_ in win rate (~36% across all sentiments). Overtrading on volatility is a losing pattern. |
| 3 | **Consistent winners (>50% win rate) significantly outperform.** Trade frequency alone does not predict profitability — discipline and selectivity matter more than volume. |

---

## Strategy Recommendations

**Strategy 1 — "Fear = Quality over Quantity"**  
> On Fear days, *reduce trade count* by 20–30% and focus on high-conviction setups only.  
> For large-position traders: reduce size. Win rate doesn't increase with more trades on Fear days.

**Strategy 2 — "Greed = Ride the trend"**  
> On Greed days, median PnL is more reliably positive. Avoid shorting against momentum.  
> For Consistent-winner segment: Greed days are the optimal time to modestly scale up positions.

---

## Bonus

- **Predictive model:** Random Forest (95% accuracy) predicting daily profitability from `win_rate`, `n_trades`, `avg_size`, `fg_value`. Win rate and trade frequency are the top two features.
- **Trader archetypes:** Segmented into Consistent Winners, Inconsistent Traders, High-Frequency, Infrequent, Small/Large Position traders.

