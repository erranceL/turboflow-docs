# Trading

## Trading Models

Traders can select between two fee models:

#### 1. Fixed Fee Model

This model operates similarly to most traditional exchanges. You pay a trading fee and slippage when opening and closing a trade.



* Trading fee: Most assets fall within the 4–6 bp range. The full list can be verified [**here**](https://turboflow.gitbook.io/whitepaper/turboflow/parameters).
* Slippage: calculated as position size/price slippage factor + base slippage.\
  The current price slippage factor can be viewed here.<br>

This setup is designed to reflect the real cost of trading on an orderbook exchange and correctly price the execution risk involved. When estimating total cost, both the trading fee and price impact are shown.\
At the time of opening a trade, the platform charges double the combined cost (to account for both opening and closing). This amount appears in your transaction history.\
When closing the trade, no additional fees are charged.

#### 2. Profit-Sharing Model

**No fees or slippage** when opening a trade.

If a trade closes with a profit, the platform charges a small percentage of that profit — the exact rate depends on how much the underlying asset moved in your favor. You can view this relationship in the Profit-Share Calculator.

If the trade ends in a loss, no fees or slippage are involved.



## Funding Fees

Funding fees are charged every **1–8 hours**, depending on the specific token. The rates are derived from **market-implied funding rates** on major exchanges.

* **Positive funding**: Long positions pay the fee to the vault.
* **Negative funding**: Short positions pay the fee to the vault.

If a trade is closed before the next funding window, **no funding fee applies**.

During the **profit-share model**, traders will receive **70% of the displayed funding amount**.\
Under the **flat-fee model**, traders receive **the full amount** of the funding.



## Oracles

Prices are sourced from a weighted average of leading exchanges (Binance, OKX, Bybit, and others) to ensure accuracy and reliability.



## Liquidation

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



## **Auto Deleveraging**

When a trader’s **unrealized PnL** exceeds the **maximum winning cap** set for a given token, the position is **automatically deleveraged** at the level where the trader retains **profits equal to that cap**.

You can view the **maximum winning cap** for each trading pair and trade directly on the **Reference Page** for **full transparency**.
