# LQ45 Portfolio Analysis & Optimization

> **Optimizing equity portfolio allocation using Monte Carlo simulation, Modern Portfolio Theory, and risk-return analytics on LQ45 stocks.**

---

## Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Business Questions](#business-questions)
- [Analysis Workflow](#analysis-workflow)
- [Dashboard Preview](#dashboard-preview)
- [Key Findings](#key-findings)
- [Insights](#insights)
- [Business Recommendations](#business-recommendations)
- [Project Structure](#project-structure)
- [How to Run](#how-to-run)
- [Tools](#tools)
- [Author](#author)

---

## Overview

This project performs a comprehensive risk-return analysis on 10 actively traded Indonesian stocks from the **LQ45 index**, covering the period **January 2020 – December 2025**. Using Modern Portfolio Theory (MPT) and Monte Carlo simulation, the analysis identifies the optimal portfolio allocation that maximizes the Sharpe Ratio — offering the best risk-adjusted return for investors.

The project demonstrates end-to-end data analysis skills: from data ingestion and cleaning, through statistical modeling, to interactive dashboard storytelling.

---

## Dataset

| Property | Detail |
|---|---|
| **Source** | Yahoo Finance via `yfinance` Python library |
| **Stocks** | BBCA, BBRI, TLKM, ASII, BMRI, UNVR, ICBP, KLBF, EXCL, INDF |
| **Index** | LQ45 (Indonesia Stock Exchange) |
| **Period** | January 2020 – December 2025 (6 years) |
| **Frequency** | Daily closing prices |
| **Records** | ~1,200 trading days × 10 stocks |

---

## Business Questions

Individual investors in Indonesia often build portfolios based on intuition rather than data. Key questions this project answers:

- Which LQ45 stocks offer the best risk-adjusted returns?
- How correlated are these stocks — and which combinations reduce overall portfolio risk?
- What is the **optimal allocation** across these stocks to maximize the Sharpe Ratio?
- How does portfolio performance vary across 5,000 simulated allocation scenarios?

---

## Analysis Workflow

### 1. Business Understanding
- Defined the investment problem: selecting an efficient stock allocation based on risk and return.
- Formulated business questions related to stock performance, diversification, and optimal portfolio allocation.
- Set the analysis objective to identify a portfolio with the best risk-adjusted return.

### 2. Data Collection & Cleaning
- Retrieved adjusted closing prices using `yfinance`
- Handled missing values with forward-fill (carry last known price)
- Validated data completeness across all tickers

### 3. Exploratory Data Analysis (EDA)
- Computed **daily returns** for all 10 stocks
- Calculated **rolling 30-day volatility** to observe risk over time
- Built a **correlation heatmap** to identify diversification opportunities
- Normalized price chart (base = 100) to compare relative performance

### 4. Risk-Return Analysis
- **Annualized Return**: Mean daily return × 252 trading days
- **Annualized Volatility**: Standard deviation of daily returns × √252
- **Sharpe Ratio**: `(Annual Return − Risk-Free Rate) / Volatility`
  - Risk-free rate assumption: **6%** (Bank Indonesia benchmark rate reference)

### 5. Monte Carlo Portfolio Simulation
- Generated **5,000 random portfolio weight combinations**
- Each combination satisfies: all weights ≥ 0, sum of weights = 100%
- Computed portfolio return, volatility, and Sharpe Ratio for each
- Plotted the **Efficient Frontier** to visualize the risk-return trade-off
- Identified the **maximum Sharpe Ratio portfolio** as the optimal allocation

### 6. Dashboard & Storytelling
- Exported all results to CSV files for Tableau visualization
- Built a 4-page interactive dashboard covering:
  - Stock performance overview
  - Individual risk-return comparison
  - Efficient frontier scatter plot
  - Optimal portfolio allocation recommendation

---

## Dashboard Preview

![Dashboard Preview](output/dashboard.png)

🔗 [View on Tableau Public](https://public.tableau.com/app/profile/fatwa.nurhidayat/viz/LQ45PortfolioOptimizationDashboard/Dashboard) 

---

## Key Findings

> *Note: The results are based on historical stock price data from the selected period. Past performance does not guarantee future results.*

- **Best Sharpe Ratio stock**: BMRI.JK — delivered the strongest risk-adjusted return among all selected LQ45 stocks, with a Sharpe Ratio of 0.301
- **Highest volatility**: EXCL.JK — recorded the highest price fluctuation (40.76%), indicating a relatively aggressive risk profile
- **Lowest correlation pair**: EXCL.JK & ICBP.JK — showed the weakest correlation (0.19), suggesting strong diversification potential when combined in a portfolio
- **Optimal portfolio** (max Sharpe Ratio ≈ 0.234):
    - ASII.JK: ~29%
    - BMRI.JK: ~24%
    - BBRI.JK: ~13%
    - BBCA.JK: ~9%
    - TLKM.JK: ~9%
    - Others: distributed across the remaining assets
- **Efficient Frontier** reveals:
    - higher expected returns generally require higher portfolio risk,
    - while diversification across multiple LQ45 sectors helps reduce overall portfolio volatility and improve portfolio efficiency
 
---

## Insights
### 1. BMRI.JK offers the strongest individual risk-adjusted performance

BMRI.JK recorded the highest Sharpe Ratio among the selected LQ45 stocks. This indicates that BMRI.JK provided the most efficient balance between return and risk compared to the other individual stocks in the analysis.

However, a high individual Sharpe Ratio does not automatically mean that the stock should dominate the entire portfolio. Portfolio construction still needs to consider correlation, volatility, and diversification effects across assets.

### 2. High return stocks do not always produce the most efficient portfolio

Some stocks showed relatively high annualized returns but also carried higher volatility. This indicates that return alone is not sufficient for investment decision-making. A stock with strong return potential may still reduce portfolio efficiency if its risk contribution is too high.

The analysis highlights the importance of evaluating both return and risk simultaneously rather than selecting stocks only based on historical price growth.

### 3. Diversification improves portfolio efficiency

The optimal portfolio achieved lower volatility than several individual stocks while maintaining a competitive expected return. This shows that combining multiple stocks can reduce overall portfolio risk, especially when the selected assets do not move perfectly together.

The low correlation between EXCL.JK and ICBP.JK also indicates that sector diversification can help reduce exposure to stock-specific risk.

### 4. EXCL.JK has an aggressive risk profile

EXCL.JK showed the highest volatility among the selected stocks. This means the stock experienced larger price fluctuations and may not be suitable for conservative investors if held in a large proportion.

However, its low correlation with some other stocks may still provide diversification benefits when allocated carefully within a broader portfolio.

### 5. The optimal portfolio is not equally weighted

The Monte Carlo simulation showed that the maximum Sharpe Ratio portfolio allocated different weights to each stock. This suggests that an equal-weighted portfolio may not be the most efficient approach when stocks have different risk, return, and correlation characteristics.

A data-driven allocation strategy can produce a more efficient portfolio by assigning higher weights to assets with better risk-adjusted contribution.

### 6. Efficient frontier helps investors understand risk-return trade-offs

The efficient frontier simulation shows that different portfolio allocations produce different levels of expected return and volatility. Portfolios with higher expected returns generally require investors to accept higher risk.

This visualization helps investors compare possible allocation scenarios and choose a portfolio that matches their risk tolerance.

---

## Business Recommendations
### 1. Prioritize risk-adjusted return, not only historical return

Investors should avoid selecting stocks based only on the highest historical return. Instead, they should evaluate the Sharpe Ratio, volatility, and correlation between assets to identify stocks that provide better return per unit of risk.

BMRI.JK can be considered as one of the core candidates in the portfolio because it showed the strongest individual risk-adjusted performance among the selected stocks.

### 2. Use diversification to reduce portfolio risk

Investors should combine stocks from different sectors and correlation profiles to reduce portfolio volatility. Stocks with low correlation, such as EXCL.JK and ICBP.JK, may help improve diversification when included with appropriate weight.

This approach can help reduce the impact of stock-specific price fluctuations on the overall portfolio.

### 3. Limit exposure to highly volatile stocks

Stocks with high volatility, such as EXCL.JK, should be allocated carefully. While they may offer return opportunities, excessive allocation to highly volatile stocks can increase portfolio risk.

For conservative investors, exposure to high-volatility stocks should be limited or balanced with more stable assets.

### 4. Use the optimal portfolio allocation as a reference, not a fixed rule

The maximum Sharpe Ratio portfolio can be used as a quantitative reference for allocation decisions. However, investors should still adjust the final allocation based on their investment horizon, risk tolerance, liquidity needs, and market outlook.

The optimal allocation from historical data should be reviewed periodically because stock performance and market conditions can change over time.

### 5. Rebalance the portfolio regularly

Investors should rebalance the portfolio periodically to maintain the intended allocation and risk level. Without rebalancing, price movements may cause certain stocks to become overweight or underweight, changing the portfolio’s risk-return profile.

A quarterly or semi-annual rebalancing strategy can help keep the portfolio aligned with the original investment objective.

### 6. Combine quantitative analysis with fundamental analysis

This project focuses on historical price data, return, volatility, correlation, and portfolio simulation. For real investment decisions, investors should also consider company fundamentals, macroeconomic conditions, sector outlook, valuation, and recent market news.

Combining quantitative portfolio analysis with fundamental research can lead to more informed investment decisions.

### 7. Use the dashboard as a portfolio monitoring tool

The Tableau dashboard can be used to monitor stock performance, compare risk-return profiles, evaluate diversification opportunities, and communicate portfolio allocation decisions more clearly.

This makes the dashboard useful not only for analysis, but also for investment reporting and decision support.

---

## Project Structure

```
LQ45-Portfolio-Optimization/
│
├── data/
│   ├── stock_price.csv             # Raw daily closing prices
│   ├── daily_returns.csv           # Computed daily returns
│   ├── stock_summary.csv           # Annualized return, volatility, Sharpe per stock
│   └── monte_carlo.csv             # 5,000 simulated portfolio metrics
│
├── notebooks/
│   └── ind_stock_analysis.ipynb    # Main analysis notebook (fully documented)
│
├── output/
│   ├── correlation_heatmap.png     # Correlation heatmap
│   ├── normalized_price.png        # Normalized price chart
│   └── efficient_frontier.png      # Monte Carlo efficient frontier plot
│
└── README.md
```

---

## How to Run

### Prerequisites
- Python 3.9+
- Jupyter Notebook or JupyterLab

### Installation

```bash
# Clone the repository
git clone https://github.com/fatwanurhdyt/LQ45-Portfolio-Optimization.git
cd LQ45-Portfolio-Optimization

# Install dependencies
pip install yfinance pandas numpy matplotlib seaborn scipy jupyter
```

### Run the Notebook

```bash
jupyter notebook notebooks/ind_stock_analysis.ipynb
```

The notebook will automatically fetch the latest stock data from Yahoo Finance. To replicate the exact results in this README, set the date range to `2020-01-01` to `2025-12-31`.

---

## Tools

| Category | Tools |
|---|---|
| **Language** | Python 3.11 |
| **Data Retrieval** | `yfinance` |
| **Data Manipulation** | `pandas`, `numpy` |
| **Visualization (Python)** | `matplotlib`, `seaborn` |
| **Dashboard** | Tableau Public |
| **Environment** | Jupyter Notebook |

---

## Author

**Fatwa Nurhidayat**
- GitHub: [@fatwanurhdyt](https://github.com/fatwanurhdyt)
- LinkedIn: [linkedin.com/in/fatwanurhdyt](https://linkedin.com/in/fatwanurhdyt)
- Email: [fatwa.nrhdyt@gmail.com](mailto:fatwa.nrhdyt@gmail.com)
