# BTC ALGO TRADER — 3YR Backtest Simulation

A fully functional, single-file Bitcoin Trading Simulator with an embedded Python-powered simulation engine running entirely in the browser via **Pyodide** (WebAssembly).

## 🚀 Overview

This tool allows users to backtest a technical trading strategy against real-world Bitcoin (BTC/USDT) historical data. Unlike simple simulators, this engine models realistic trading conditions including exchange fees, stop-losses, and execution delays.

**Live Simulation:** Everything runs client-side. No backend, no database, and no installation required.

## ✨ Key Features

- **Python Simulation Engine**: High-performance backtesting logic powered by Python 3.11+ in the browser.
- **Real Market Data**: Automatically fetches the last ~1000 days (~2.7 years) of BTC/USDT price action from the Binance API.
- **Configurable Strategy**:
  - **Golden/Death Cross**: SMA-based trend following.
  - **RSI Filter**: Momentum-based entry/exit guards.
  - **Bollinger Bands**: Volatility visualization.
  - **Stop-Loss**: Built-in risk management to protect capital.
- **Realistic Modeling**:
  - **Next-Day Execution**: Signals detected at day's close are executed at the next day's open price (prevents look-ahead bias).
  - **Trading Fees**: Deducts a standard 0.1% fee per transaction.
- **Terminal Aesthetic UI**:
  - **Dual Charts**: Interactive price/indicator charts and portfolio performance tracking.
  - **Stats Dashboard**: Professional metrics including Alpha, Sharpe Ratio, Max Drawdown, and Win Rate.
  - **Exportable Ledger**: View daily trade logs in a paginated table or export the full history to CSV.

## 🛠️ Technology Stack

- **[Pyodide](https://pyodide.org/)**: Python 3.11 scientific stack compiled to WebAssembly.
- **[Chart.js](https://www.chartjs.org/)**: High-performance canvas charting.
- **[Binance API](https://binance-docs.github.io/apidocs/spot/en/)**: Real-time and historical cryptocurrency data.
- **Tailwind CSS**: Modern utility-first styling for the "Dark Terminal" look.
- **Lucide Icons**: Clean, consistent UI iconography.

## 🚦 Getting Started

1.  **Download** the `index.html` file.
2.  **Open** the file in any modern web browser (Chrome, Firefox, Safari, or Edge).
3.  **Click "RUN SIMULATION"**: The app will fetch the latest data and execute the backtest.

*Note: The first run may take a few seconds as the browser downloads the Pyodide runtime (~10MB).*

## 🧠 The Strategy Logic

The default "Golden Cross" strategy works as follows:

1.  **Entry (BUY)**: Triggered when the **Fast SMA** (e.g., 7-day) crosses *above* the **Slow SMA** (e.g., 30-day), provided the **RSI** is not in "Overbought" territory.
2.  **Exit (SELL)**: Triggered when the **Fast SMA** crosses *below* the **Slow SMA**.
3.  **Safety Net**: If the portfolio value drops by the **Stop-Loss %** from the entry price, the position is liquidated immediately to prevent further drawdown.

## 📊 Metrics Explained

- **Alpha**: The outperformance of the bot compared to simply holding Bitcoin over the same period.
- **Sharpe Ratio**: A measure of risk-adjusted return (calculated using daily returns and a 365-day annualization factor).
- **Max Drawdown**: The largest peak-to-trough decline in portfolio value, indicating the maximum historical risk.

## 📝 License

This project is provided for educational and simulation purposes only. **Not financial advice.**
