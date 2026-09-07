---
description: Event Contracts are TurboFlow’s short-term, event-based market products.
icon: binary
---

# Event Contracts

### **Product Guide**

TurboFlow Event Contracts are short-term Higher / Lower trades on a market over a fixed time window. A trader chooses a supported market, selects a duration, enters a stake, and chooses Higher or Lower. When the timer ends, the contract settles automatically.

Each contract reduces a trading view to one clear question:

> <mark style="color:$primary;">**Will the market be higher or lower at expiry?**</mark>

The product is designed for traders seeking fast, simple directional exposure without the moving parts of a traditional leveraged position. During the life of an Event Contract, there is no margin management, no funding, and no liquidation management. The staked amount defines the maximum possible loss for that contract.

Markets, durations, limits, return rates, and other product parameters may change with product rollout, liquidity, and platform risk settings. The live TurboFlow interface is the authoritative source for current availability and the terms shown before an order is confirmed.

### **How Do TurboFlow Event Contracts Work?**

The trading flow is designed to make the contract terms visible before entry:

1. Choose a supported market.
2. Select a contract duration.
3. Enter a stake and review the Enter Price, Return Rate, and estimated profit.
4. Choose Higher or Lower and confirm the order.
5. Wait for the contract to settle automatically at expiry.

A Higher position is a view that the Exit Price will be above the Enter Price at expiry. A Lower position is a view that the Exit Price will be below the Enter Price at expiry.

### **What Determines the Outcome?**

Two prices determine the result of an Event Contract:

* Enter Price — the market price when the order is accepted.
* Exit Price — the market price at the contract’s settlement time.

TurboFlow compares the Exit Price with the Enter Price under the platform’s official settlement rules:

* Correct direction — the contract settles at the amount shown before confirmation.
* Incorrect direction — the trader loses the staked amount.
* Flat result — if the settlement result is unchanged under platform rules, the principal is returned.

The size of the market move does not change whether the selected direction is correct. The outcome depends on the relationship between the Enter Price and Exit Price at the fixed settlement time.

### **What Durations and Markets Are Available?**

TurboFlow supports short-cycle Event Contract durations including:

* 30 seconds
* 1 minute
* 3 minutes
* 5 minutes
* 15 minutes
* 1 hour

Shorter durations are suited to faster market moves and more active trading. Longer durations give a market view more time to develop. Available durations may change according to liquidity and risk management settings.

TurboFlow Event Contracts are currently available on:

* Bitcoin (BTC)
* Ether (ETH)
* Gold (XAU)
* Silver(XAG)

Users may hold Event Contracts across multiple durations at the same time. The current limit is 200 USDT per duration. The live product interface should always be checked for the latest supported markets, durations, and limits.

USDT is the default quote currency on TurboFlow. Users can deposit USDT or USDC through supported external networks.

### **How Do Return Rate, Pricing, and Settlement Work?**

Before an Event Contract is confirmed, the TurboFlow interface displays:

* the selected market
* the Enter Price
* the selected duration
* the Return Rate
* the estimated profit

The Return Rate reflects the current market, selected direction, contract duration, volatility, liquidity conditions, and platform risk settings. Once the order is confirmed, that Return Rate is locked for the specific contract. Later changes in quoted rates do not change an already confirmed contract.

Enter Price and Exit Price are determined through TurboFlow’s oracle-based pricing system under the platform’s official settlement rules. Settlement occurs automatically at expiry, so no separate closing action is required.

All TurboFlow trades require onchain confirmation. Under normal conditions, order confirmation involves a delay of roughly 300–500 milliseconds. Users should rely on the live interface and official platform rules for current settlement behavior, pricing references, and contract terms.

### **How Do Event Contracts Compare With Other Products?**

Event Contracts provide a different trading structure from perpetual contracts and longer-duration prediction-style products:

* Event Contracts — short-cycle Higher / Lower trades with a fixed expiry, a return rate locked at confirmation, and a maximum loss equal to the stake.
* Perpetual contracts — open-ended positions that require ongoing margin management and involve funding and liquidation considerations.
* Prediction-style markets — outcome-based positions that commonly resolve over longer time horizons.

TurboFlow Event Contracts sit between traditional derivatives and prediction-style products: they use an outcome-based format while keeping the timing and maximum risk of each contract clearly defined.

### **Why Do Traders Use Event Contracts?**

TurboFlow Event Contracts are built for traders who want:

* Clear risk per trade — the maximum loss is the stake and is known before entry.
* Fixed settlement timing — every contract has a defined expiry.
* Fast execution — contract cycles can be as short as 30 seconds.
* Short-term directional opportunities — traders can express views on momentum, trend, volatility, or a market reaction over a defined window.
* Simpler position mechanics — there is no margin, funding, or liquidation management during the contract.

The interface is simple, but the trading decisions can still be strategic. Duration selection, entry timing, position sizing across concurrent contracts, and the displayed Return Rate all remain important considerations.

### **Key Terms**

* **Event Contract** — a contract whose result depends on whether a defined condition is met at a defined time.
* **Higher / Lower** — the two directional choices for a TurboFlow Event Contract.
* **Enter Price** — the market price when an order is accepted.
* **Exit Price** — the market price at the contract’s settlement time.
* **Duration** — the fixed length of the contract.
* **Return Rate** — the rate shown before entry and locked when the order is confirmed.
* **Stake** — the amount committed to the contract and the maximum possible loss.
* **Settlement** — the automatic resolution of the contract at expiry using TurboFlow’s pricing system.
* **Flat** — an unchanged settlement result for which the principal is returned.

### **Frequently Asked Questions**

<details>

<summary>What happens if an Event Contract settles flat?</summary>

If the settlement result is unchanged under platform rules, the principal is returned.

</details>

<details>

<summary>Is there liquidation risk during the contract?</summary>

There is no margin management, funding, or liquidation during the life of a TurboFlow Event Contract. The maximum possible loss is the staked amount.

</details>

<details>

<summary>Can users hold Event Contracts across different durations?</summary>

Yes. Users may hold contracts across multiple durations at the same time. The current limit is 200 USDT per duration.

</details>

<details>

<summary>Which assets can users deposit?</summary>

USDT is TurboFlow’s default quote currency. Users can deposit USDT or USDC through supported external networks.

</details>

<details>

<summary>Where do Enter Price and Exit Price come from?</summary>

Both are determined through TurboFlow’s oracle-based pricing system under the platform’s official settlement rules.

</details>

<details>

<summary>Why can order confirmation take 300–500 milliseconds?</summary>

All trades require onchain confirmation. Under normal conditions, the confirmation process involves a delay of roughly 300–500 milliseconds.

</details>

### **Important Risk Notice**

TurboFlow Event Contracts are high-risk, short-term trading products and are not suitable for all users.

Fast settlement can lead to rapid gains or losses. An incorrect direction results in the loss of the full staked amount. Users should never trade with funds they cannot afford to lose.

Supported markets, durations, return rates, settlement behavior, and platform rules may change over time. Users should review the live product interface and official platform rules before trading.

Past outcomes and displayed return rates do not guarantee future results. Users should understand the product, manage position size carefully, and participate responsibly. This document is product information and does not constitute financial advice.

### **Official Sources**

[TurboFlow Homepage](https://tf.xyz/)  ·  [TurboFlow Event Contracts Documentation](https://turboflow.gitbook.io/whitepaper/turboflow/products/event-contracts)  ·  [TurboFlow FAQ](https://turboflow.gitbook.io/whitepaper/turboflow/resources/faq)  ·  [TurboFlow Deposits and Withdrawals](https://turboflow.gitbook.io/whitepaper/turboflow/resources/deposits-and-withdrawals)
