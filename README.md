# Trading Strategy for QuantiInsti 3Hr Hackathon

This repository contains a Python-based trading strategy. The strategy is fundamentally **momentum-based**—it leverages technical indicators to capture trends and changes in market momentum. While the current implementation is sufficient for the hackathon's timeframe, there is room for further improvements and refinements.

## Strategy Overview

The core idea of this momentum-based strategy is to capture market moves by:
- **Entry Signals:**  
  - **Long Position:**  
    - The 50-day EMA is above the 200-day EMA, indicating an overall bullish trend.
    - The current close is above the 50-day EMA.
    - The RSI is above 55, showing strong momentum.
    - Volume exceeds the 20-day average volume, indicating increased market participation.
  - **Short Position:**  
    - The 50-day EMA is below the 200-day EMA, indicating an overall bearish trend.
    - The current close is below the 50-day EMA.
    - The RSI is below 45, suggesting weak momentum.
    - Volume exceeds the 20-day average volume, confirming the strength of the move.

- **Exit & Flip Logic:**  
  - For a **long position**, the strategy exits when the RSI drops below 50, signaling a potential loss of upward momentum, and then immediately flips into a short position.
  - For a **short position**, it exits when the RSI rises above 50, signaling a potential reversal or loss of downward momentum, and then flips into a long position.
  
This immediate flip approach ensures continuous exposure to momentum changes in the market, allowing the strategy to capture both upward and downward moves when conditions shift.

## Backtesting and Implementation

- **Data & Indicators:**  
  The strategy uses historical stock data and computes the following technical indicators:
  - EMA (50-day and 200-day)
  - RSI (14-day period)
  - Rolling 5-day high/low for breakout validation (shifted by one period)
  - Rolling 20-day average volume (shifted by one period)
  
- **Trade Execution:**  
  The backtest simulates the entry and exit of trades based on the defined signals and incorporates an auto-flip mechanism to switch positions instantly when exit conditions are met.

- **Performance Metrics:**  
  The backtest outputs the final balance, total returns, and the number of trades executed, which can be used to evaluate the strategy's performance.

## Competition Context and Future Improvements

Given the 3-hour timeframe of the competition, this momentum-based strategy provides a functional baseline. However, several improvements can be explored:
- **Risk Management:**  
  Incorporating stop-loss and take-profit levels could help manage risk more effectively.
- **Signal Confirmation:**  
  Additional confirmation indicators (like MACD or volume oscillators) might reduce false signals.
- **Optimization:**  
  Parameter optimization (e.g., EMA periods, RSI thresholds) using historical data can fine-tune performance.
- **Alternative Exit Strategies:**  
  Testing different exit conditions or dynamic position sizing may further enhance returns.

This repository serves as a starting point for further development and refinement. Your feedback or contributions are welcome.
