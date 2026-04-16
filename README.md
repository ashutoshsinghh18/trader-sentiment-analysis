##  Trader Performance vs Market Sentiment

An end-to-end data analysis project exploring the relationship between 
Bitcoin market sentiment (Fear/Greed Index) and trader behavior on 
Hyperliquid — a decentralized perpetuals exchange.

Analyzed 211,000+ real trades across 2 years (2023–2025).

##  Key Findings
- Traders execute 37% more trades on Fear days with no improvement in win rate
- Greed days produce more consistent positive PnL (median $265 vs $123 on Fear days)
- Consistent winners (>50% win rate) outperform high-frequency traders across all sentiments
- Random Forest model predicts next-day profitability with 95% accuracy

## Tech Stack
- Python · Pandas · NumPy
- Matplotlib · Seaborn
- Scikit-learn (Random Forest)
- Jupyter Notebook

##  Repository Structure
trader-sentiment-analysis/
├── trader_sentiment_analysis.ipynb  # Main analysis notebook
├── README.md                        # Project documentation
├── charts/                          # All output charts
│   ├── chart1_pnl_distribution.png
│   ├── chart2_behavior_metrics.png
│   ├── chart3_timeseries.png
│   ├── chart4_segments.png
│   ├── chart5_longshort.png
│   └── chart6_feature_importance.png
└── data/                            # Place CSV files here
    ├── historical_data.csv
    └── fear_greed_index.csv

##  How to Run
# 1. Clone the repo
git clone https://github.com/ashutoshsinghh18/trader-sentiment-analysis

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

# 3. Launch notebook
jupyter notebook trader_sentiment_analysis.ipynb
