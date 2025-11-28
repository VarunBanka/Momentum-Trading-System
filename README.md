# **Momentum Trading System**

A machine-learning-driven momentum strategy built using Python, Auquan Toolbox, and custom backtesting logic.
The project downloads historical Level-2 market data, generates features, trains predictive models, and evaluates trade performance using a structured backtesting pipeline.

---

## 📘 **Overview**

This project aims to forecast short-term changes in the **basis** (difference between stock and future prices) and trade based on expected movement.
It combines **feature engineering**, **ensemble ML models**, and a **custom portfolio simulator** to evaluate strategy performance.

---

## 🧰 **Features**

### **✔ Data Pipeline**

* Auto-download of historical data using **Auquan Historical Data API**
* Cleans & processes stock and futures order-book information
* Computes mid-price, bid/ask volumes, target variable, etc.

### **✔ Feature Engineering**

Includes multiple predictive indicators:

* Momentum: `mom10`
* EMA signals: `emabasis2`, `emabasis5`, `emabasis10`
* Volume imbalances: `totalaskvolratio`, `totalbidvolratio`
* RSI movement features
* Shifted/normalized basis transformations

### **✔ Machine Learning**

* **Extra Trees Regressor** (sklearn)
* Achieves high variance score (~0.95 on sample run)
* Smooth predictive output suitable for trading signals

### **✔ Backtesting System**

Tracks:

* Instrument-level & portfolio-level PnL
* Score (normalized performance metric)
* Capital usage
* trades: wins/losses
* Maximum Drawdown
* Variance & volatility of returns
* Portfolio value progression

---

## 📊 **Sample Strategy Output**

Sample JSON summary:

```json
{
  "instrument_names": ["MQK"],
  "instrument_stats": [{
      "pnl": { "MQK": 0.11692330000000006 },
      "score": { "MQK": 0.5270070414825269 }
  }],
  "pnl": 0.11692330000000006,
  "trading_days": 3,
  "score": 0.5270070414825269,
  "maxDrawdown": 483.66499999999905,
  "maxPortfolioValue": 11230.483,
  "total_loss": 4699.115000000002,
  "variance": 790.2561871673435,
  "count_profit": 228,
  "capital": 9936.30299999999,
  "capitalUsage": 1324.7970000000041,
  "portfolio_value": 11169.233,
  "total_profit": 5868.347999999998,
  "count_loss": 222
}
```

### **Interpretation Highlights**

* ~50% win-rate (228 wins / 450 trades)
* Moderate net PnL (after aggregation)
* High drawdown → high-risk strategy
* High variance → volatile performance
* Model signal works but risk controls need improvement

---

## 🚀 **Getting Started**

### **Clone the repository**

```bash
git clone https://github.com/VarunBanka/Momentum-Trading-System
cd Momentum-Trading-System
```

### **Install Dependencies**

```bash
pip install scikit-learn tensorboardX beautifulsoup4 auquan_toolbox --no-deps
```

### **Run the Notebook**

Open:

```
Momentum_Trading_System.ipynb
```

Run all sections sequentially:

1. Data download
2. Cleaning & preprocessing
3. Feature engineering
4. Model training
5. Validation
6. Backtesting & output analysis

---

## 📈 **Future Enhancements**

* Add Stop-Loss/Take-Profit logic
* Add slippage & transaction costs
* Integrate more ML models (XGBoost, LightGBM, LSTM)
* Walk-forward or rolling-window training
* Add visualizations for equity curve + drawdown
* Multi-instrument diversification


---

## ⚠️ **Disclaimer**

This project is **for educational and research purposes only**.

* Nothing here is financial advice.
* Trading carries significant risk, including total capital loss.
* The author & contributors are **not responsible** for any financial losses.
* Models trained on historical data **do not guarantee** future performance.
* Use at your own risk.

---

## 🤝 **Contributing**

PRs and suggestions are welcome!
If you want to add features, please open an issue first.

---

## ⭐ **Support**

If you find this project useful, consider giving it a ⭐ on GitHub!

---
