# Market Regime Detection and Dynamic Portfolio Allocation

## Overview 

This project explores whether financial market environments can be grouped into distinct **market regimes** and whether those regimes can be used to improve **portfolio allocation decisions**.

It demonstrates how machine learning can be applied to financial markets not just for prediction, but for improving decision-making under changing market conditions.

The project uses a combination of:
- **Unsupervised learning** to detect market regimes
- **Supervised learning** to predict future regimes
- **Regime-based portfolio backtesting** to evaluate investment performance relative to static benchmarks

This project was developed as part of the **University of Michigan Master of Applied Data Science (MADS) Capstone (SIADS 699)**.



## Project Objective

Financial markets do not behave the same way over time. Periods of calm, transition, and stress can lead to very different return and risk patterns across asset classes.

The objective of this project is to:
1. Detect distinct market regimes using historical financial data  
2. Predict the next market regime using supervised machine learning  
3. Apply predicted regimes to a portfolio allocation strategy  
4. Compare the strategy against benchmark allocations such as **SPY buy-and-hold**


## Data Source

This project uses publicly available financial data from the following sources:

### Market Data
- **Yahoo Finance** (via 'yfinance')
- Examples: SPY, QQQ, TLT, GLD, sector ETFs, global indices, and VIX-related series

### Macroeconomic Data
- **FRED (Federal Reserve Economic Data)** (via 'fredapi')
- Examples: 10-Year Treasury Yield, 2-Year Treasury Yield

**All data used in this project is publicly accessible and does not require special permissions.**  
**Users must provide their own FRED API key to access macroeconomic data.**

No proprietary or restricted datasets are included in this repository.

## Data Access Statement

All data used in this project is publicly available from Yahoo Finance and FRED.  
Users must provide their own FRED API key to access macroeconomic data.

Due to licensing and size considerations, not all intermediate datasets are included in this repository. All data can be regenerated using the provided notebooks.


## Methodology



The project is organized into three main steps:

### 1. Unsupervised Learning: Market Regime Detection
We engineer volatility, return, and macroeconomic features from historical weekly market data and use clustering methods to identify distinct market regimes.

### 2. Supervised Learning: Regime Prediction
After labeling the historical data with regimes, we train supervised machine learning models to predict the **next period’s regime** using lagged financial and macroeconomic features.

### 3. Portfolio Backtesting
Predicted regimes are used to drive dynamic portfolio allocations across a selected set of assets. Strategy performance is then compared with benchmark portfolios using return, volatility, Sharpe ratio, and drawdown metrics.

## Model Development Notes

Multiple modeling approaches were explored, including:
- Direct multiclass regime prediction
- A two-layer model separating risk detection and regime classification

The final implementation consolidates the best-performing approach for clarity and reproducibility.

## Results

The regime-based allocation framework was evaluated against benchmark strategies such as SPY buy-and-hold and a traditional 80/20 stock-bond portfolio.

Key findings:
- Regime-aware allocation improved risk-adjusted returns in certain market conditions
- The model was effective at identifying high-volatility periods and reducing exposure to risk assets
- Performance gains were primarily driven by improved drawdown management rather than raw return maximization

While results vary across time periods, the framework consistently demonstrates improved risk management during periods of market stress.

## Repository Structure

```text

├── README.md
├── requirements.txt
├── LICENSE
├── 01 - Data Preparation - Fred YFinance.ipynb
├── 02 - Data Engineering.ipynb
├── 03 - Unsupervised.ipynb
├── 04 - Supervised Combined.ipynb
├── 05 - Regime Portfolio - Combined 2 Layer.ipynb
└── (data files used for modeling and backtesting)
```

## Getting Started

This project can be run either locally using Jupyter Notebook or through Deepnote.

> Note: You must provide your own FRED API key to run this project.

#### 1. Clone the repository

```bash
git clone https://github.com/Spencer-Cheung/regime-portfolio-allocation.git
cd regime-portfolio-allocation
```

#### 2. Install dependencies

```bash
pip install -r requirements.txt
```

#### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

## Execution Order

Run the notebooks in the following order:

1. 01 - Data Preparation - Fred YFinance  
2. 02 - Data Engineering  
3. 03 - Unsupervised  
4. 04 - Supervised Combined  
5. 05 - Regime Portfolio - Combined 2 Layer

## Author Contributions

Arun Palaniappan (Co-Owner): Led the development and refinement of the written report and project video. Developed the initial supervised models and contributed to GitHub repository development and visualizations.

Phuc Nguyen (Co-Owner): Contributed to data acquisition, data cleaning, and feature engineering. Played a key role in both unsupervised and supervised modeling, pioneering the 2 layer model, as well as the development of the allocation framework. Also contributed to data visualization and analysis.

Spencer Cheung (Co-Owner): Led overall project direction and coordination. Responsible for initial data acquisition, data cleaning, and feature engineering. Implemented the unsupervised learning framework and contributed to the portfolio allocation approach. Developed the initial draft of the report and contributed to GitHub repository management and visualizations.

