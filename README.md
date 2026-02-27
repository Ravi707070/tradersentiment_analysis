# Trader Performance vs Market Sentiment Analysis

##  Overview

This project analyzes how trader performance and behavior vary across different market sentiment regimes (Fear vs Greed).  

The goal is to:
- Understand whether sentiment impacts profitability
- Identify behavioral shifts in traders
- Propose actionable strategy rules
- Explore predictive modeling and trader segmentation

---

##  Datasets

### 1️ fear_greed_index.csv
Contains daily market sentiment data:
- `timestamp`
- `value` (Fear & Greed index value)
- `classification` (Fear / Extreme Fear / Neutral / Greed / Extreme Greed)
- `date`

### 2️ historical_data.csv
Contains trader-level transaction data:
- `Account`
- `Execution Price`
- `Size USD`
- `Side` (Buy/Sell)
- `Closed PnL`
- `Timestamp`

---

##  Methodology

### 1. Data Preparation
- Removed duplicates
- Checked missing values
- Converted timestamps to daily format
- Merged trading data with sentiment data on date

### 2. Feature Engineering
Created:
- Daily PnL per trader
- Win rate (PnL > 0)
- Average trade size
- Trade frequency
- Long/Short ratio
- Sentiment encoding (Fear / Greed)

### 3. Analysis
- Compared performance metrics across Fear vs Greed days
- Measured behavioral shifts in trade frequency and position sizing
- Segmented traders by consistency and activity
- Evaluated drawdown proxy using PnL volatility

### 4. Bonus Work
- Built a Random Forest model to predict next-day profitability bucket
- Applied KMeans clustering to identify trader archetypes
- Built a lightweight Streamlit dashboard for interactive exploration

---

##  Key Insights

1. **Performance differs across sentiment regimes**
   - Win rates are generally higher during Greed periods.
   - PnL volatility increases during Fear periods.

2. **Behavior adapts to market sentiment**
   - Trade frequency increases during Greed days.
   - Position sizes tend to expand in positive sentiment environments.

3. **Trader segmentation is meaningful**
   - Consistent traders perform better during Greed regimes.
   - Inconsistent traders experience larger volatility during Fear.

---

##  Strategy Recommendations

### Strategy 1 — Risk Control During Fear
Reduce position sizes for low win-rate traders during Fear periods to limit downside exposure and volatility impact.

### Strategy 2 — Selective Aggression During Greed
Allow moderate position size expansion for consistent traders during Greed regimes to enhance upside capture while maintaining risk control.

---

##  Predictive Modeling (Bonus)

A Random Forest classifier was trained to predict next-day trader profitability bucket using:
- Daily PnL
- Win rate
- Average trade size
- Sentiment encoding

Results indicate trader behavior combined with sentiment contains predictive signal.

---

##  Trader Clustering (Bonus)

KMeans clustering identified distinct trader archetypes:
- Aggressive risk-takers
- Consistent performers
- Conservative traders

This segmentation can be used for personalized risk management strategies.

---

##  How to Run

###  Create Environment

```bash
conda create -n ds_env python=3.10
conda activate ds_env
pip install -r requirements.txt

## Requirements
pandas
numpy
scikit-learn
matplotlib
seaborn
streamlit
pyarrow

##Project Structure
primetrade-trader-sentiment-analysis/
│
├── data/
├── notebooks/
├── outputs/
├── requirements.txt
└── README.md
🎯 Conclusion

Market sentiment influences trader behavior and performance.
Incorporating sentiment-aware risk controls and trader segmentation can improve stability and enhance returns in sentiment-driven market conditions.