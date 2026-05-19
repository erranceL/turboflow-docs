---
description: >-
  TurboFlow’s perpetual trading experience, including trading models, pricing,
  funding, and core risk controls.
icon: chart-line-up
---

# Perpetual Trading

### Overview

Perpetual Trading is one of the core market experiences on TurboFlow.

It is designed to give users a more flexible way to participate in supported markets through high-leverage access, multiple trading models, and a risk framework built around transparency and platform-level controls.

Rather than offering a one-size-fits-all structure, TurboFlow’s perpetual trading experience combines pricing logic, funding mechanics, liquidation rules, and execution design to support more active and capital-efficient market participation.

### Trading Models

TurboFlow supports multiple trading models so users can choose the structure that best fits how they want to trade.

#### 1. Flat-Fee Model

This model operates similarly to most traditional exchanges. You pay a trading fee and slippage when opening and closing a trade

* **Trading fee**: Most assets fall within the **4–6 basis point (bp)** range, where 1 bp = 0.01%.&#x20;
* **Slippage**: calculated as position size/price slippage factor + base slippage.

This setup is designed to reflect the real cost of trading on an orderbook exchange and correctly price the execution risk involved. When estimating total cost, both the trading fee and price impact are shown.

\
When opening a trade, the platform charges double the combined cost (to account for both opening and closing). This amount appears in your transaction history.

\
When closing the trade, no additional fees are charged.

#### 2. Profit-Sharing Model

**No fees or slippage** when opening a trade.

If a trade closes with a profit, the platform charges a small percentage of that profit — the exact rate depends on how much the underlying asset moved in your favor.&#x20;

You can view this relationship in the Profit-Share Calculator.

If the trade ends in a loss, no fees or slippage are involved.

### Funding Fees

Funding fees are charged every **1–8 hours**, depending on the specific token. The rates are derived from **market-implied funding rates** on major exchanges.

* **Positive funding**: Long positions pay the fee to the vault.
* **Negative funding**: Short positions pay the fee to the vault.

If a trade is closed before the next funding window, **no funding fee applies**.

During the **profit-share model**, traders will receive **70% of the displayed funding amount**.

\
Under the **flat-fee model**, traders receive **the full amount** of the funding.

### Oracles

Prices are sourced from a weighted average of leading exchanges (Binance, OKX, Bybit, and others) to ensure accuracy and reliability.

### Liquidation

Positions are liquidated when the total collateral value falls below the required maintenance margin across all open positions.

$$
Collateral\ Value<Position\ Size\times Maintenance\ Margin\ Rate
$$

1. **For leverage ≤ 100x:**\
   Maintenance Margin Rate (MMR) = min(45% × Initial Margin Rate, leverage-specific maximum MMR)

* The leverage-specific maximum MMR depends on the position holdings of each trading pair and can be viewed in the reference table.
* Initial Margin Rate (IMR) = 1 / Leverage

2. **For leverage > 100x:**\
   Maintenance margin may vary with market conditions and token-specific parameters. It is capped at **70% × IMR** and floored at **45% × IMR**.

### **Auto Deleveraging**

When a trader’s **unrealized PnL** exceeds the **maximum profit cap** set for a given token, the position is **automatically deleveraged** at the level where the trader retains **profits equal to that cap**.

You can view the **maximum profit** **cap** for each trading pair and trade directly on the **Reference Page** for **full transparency**.
