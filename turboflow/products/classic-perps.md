---
description: >-
  TurboFlow’s standard perpetual trading experience, including leverage, margin,
  funding, and tier-based risk controls.
icon: chart-line-up
---

# Classic Perps

### Overview

Classic Perps let traders take leveraged **long or short exposure without a fixed expiry**.

On TurboFlow, Classic Perps are built to feel familiar to users of major exchanges: open a position, choose your leverage, manage margin, and close when you want.

The product uses a transparent **tier-based risk framework**, with the highest leverage available on the deepest markets and more conservative limits applied to lower-liquidity pairs. Tier assignments are reviewed regularly to keep risk settings aligned with market conditions.

### What Traders Should Understand First

There are four core parts to TurboFlow Classic Perps:

* **leverage**, which determines how much exposure you can take relative to your collateral
* **margin**, which determines how much collateral you need to open and maintain a position
* **funding**, which reflects the cost of holding a position across funding windows
* **liquidation rules**, which define when a position can no longer be supported by available collateral

TurboFlow is designed to make those rules visible rather than hiding them behind a generic leverage label.

### Trading Costs

TurboFlow Classic Perps use a standard **flat-fee** model, similar to the structure traders are used to on major exchanges.

When trading, users pay:

* a trading fee
* slippage based on position size and market conditions

When opening a trade, the platform charges the combined cost for both the open and close upfront. That amount is shown in transaction history. No additional trading fee is charged when the position is closed.

For the full list of trading pairs and applicable fees, refer to the [Parameters & Risk Logic](../turboflow-core/parameters-and-risk-logic.md) Page here.&#x20;

### Margin and Leverage Framework

TurboFlow uses a 4-tier risk framework for Classic Perps.

Instead of assigning the same leverage to every asset, TurboFlow groups markets by liquidity and spread quality, then applies leverage caps and position limits that match the underlying risk of that market.

### How Position Brackets Work

Within each tier, margin requirements are not static.

As position size increases:

* maximum effective leverage decreases
* initial margin requirements increase
* maintenance requirements increase

This bracketed structure allows smaller positions in liquid markets to access higher leverage, while larger positions face tighter risk limits.

In plain English: **the bigger the position, the more collateral the system requires.**

That helps reduce liquidation cascades, improves platform stability, and keeps leverage aligned with real market depth.

[parameters-and-risk-logic.md](../turboflow-core/parameters-and-risk-logic.md "mention")

### Initial Margin and Maintenance Margin

TurboFlow calculates margin requirements using a rules-based framework rather than a single flat number.

At a high level:

* Initial Margin determines how much collateral is needed to open a position
* Maintenance Margin determines how much collateral must remain to keep that position open

The core formulas are:

* Initial Margin Rate (IMR) = 1 / Max Leverage
* Initial Margin = Position Value x IMR
* Maintenance Margin Rate (MMR) = 1 / (2 x Max Leverage) for the relevant bracket
* Maintenance Margin = (Position Value x MMR) - Maintenance Deduction

As a position moves into larger size brackets, maintenance requirements step up accordingly.

TurboFlow also uses a maintenance deduction mechanism so transitions between brackets are smoother and do not create abrupt jumps in required maintenance at each threshold.

For traders, the key point is simple: larger positions and riskier markets require more conservative margin treatment.

**For the full tier-by-tier and bracket-by-bracket margin table, including leverage, initial margin, maintenance margin, and maintenance deduction values for each asset, refer to the Classic Perps Margin PDF below.**

{% file src="../../.gitbook/assets/TurboFlow Perpetuals_Margin and Leverage Framework.pdf" %}

### Funding

Funding exists to keep the perpetual contract price anchored to the underlying spot market.

On TurboFlow, funding is calculated every hour. The platform samples the gap between the perp index price and the spot reference price every 5 seconds, averages those samples across the hour, and then uses that average premium to determine who pays whom.

The core formulas are:

* premium\_t = (Market Maker Perp Price\_t / Spot Index\_t) - 1
* Average Premium = mean of all 720 five-second samples collected over 1 hour
* Funding Rate = Average Premium + clamp(0.00125% - Average Premium, -0.05%, +0.05%)
* Final Funding Rate = clamp(Funding Rate, -4%, +4%)
* Funding Payment = Position Size x Spot Index x Final Funding Rate

At a high level:

* if the perp trades above spot, longs pay shorts
* if the perp trades below spot, shorts pay longs
* if the perp trades close to spot, funding stays near zero

TurboFlow adds a small fixed interest component of 0.00125% per hour, with a clamp of +/-0.05%, so the interest leg does not overpower the premium signal. The final funding rate is also capped at +/-4% per hour.

This structure is designed to keep funding responsive to real dislocations while protecting traders from runaway funding during extreme moves.

### Perp Price, Spot Index, and Oracles

TurboFlow separates three different pricing components:

* Market Maker Perp Price: the live perpetual contract price provided by the market maker
* Spot Index: TurboFlow's own spot reference price for the underlying asset
* Funding Rate: the hourly payment mechanism that keeps the perp price anchored to spot

For standard assets, TurboFlow builds its spot index from major spot venues including Binance, OKX, Bybit, and Bitget.

The core spot-index formulas are:

* mid\_i = (best bid\_i + best ask\_i) / 2
* Spot Index = weighted median of surviving exchange mids

The spot index is designed to be robust rather than simply averaging everything together:

* top-of-book mid prices are read every 3 seconds
* stale feeds older than 5 seconds are dropped
* any venue more than 0.5% away from the live median is rejected as an outlier
* the final spot reference is taken using a weighted median, not a weighted average

This matters because a weighted median is harder to manipulate than a weighted average. A single bad venue cannot pull the spot index unless it controls more than half of the total weight.

If the market maker perp price becomes abnormal, TurboFlow can fall back to Binance perp pricing for the perp-side input while keeping the TurboFlow spot index unchanged.

### Spot-Limited Assets

Most Classic Perps will use a normal spot-based reference price. But for assets with no reliable spot feed, TurboFlow can fall back to a secondary mode.

In that case:

* the reference price becomes an 8-hour EMA of the market maker perp price
* funding is reduced to 1% of the normal rate
* the mark price used for liquidation is capped at 3x the synthetic spot reference

This is a fallback design for hard-to-reference assets, not the standard case. Its purpose is to soften volatility and reduce liquidation risk when no reliable external spot anchor exists.

### Liquidation

Positions are liquidated when available collateral falls below the required maintenance level for open positions.

The exact maintenance requirement depends on:

* the trading pair
* the leverage used
* the size bracket of the position
* the platform's current risk settings

This means liquidation risk is not only about headline leverage. It is also shaped by market tier and position size.

### Why This Structure Exists

TurboFlow's Classic Perps framework is built to balance three goals:

* high leverage where liquidity can support it
* tighter controls where markets are thinner or more volatile
* transparent rules that traders can understand before entering a position

The result is a perp product that aims to be flexible for active traders without pretending every market carries the same risk.

### Important Risk Notice

Classic Perps are leveraged products and are not suitable for all users.

High leverage can magnify both gains and losses. Liquidation can happen quickly, especially in volatile markets or larger size brackets.

Leverage limits, margin requirements, funding treatment, and position caps may change over time. Always rely on the live product interface and official platform rules for the latest settings before trading.

### Risk Tiers

<table><thead><tr><th width="91.8203125">Tier</th><th width="279.08984375">Market Profile</th><th>Max Leverage</th><th>Max Position Cap</th></tr></thead><tbody><tr><td>Tier 1</td><td>Deep, highly liquid majors</td><td>200x</td><td>$10,000,000</td></tr><tr><td>Tier 2</td><td>Liquid large-cap and tighter-spread markets</td><td>100x</td><td>$2,000,000</td></tr><tr><td>Tier 3</td><td>Mid-liquidity / wider-spread markets</td><td>50x</td><td>$500,000</td></tr><tr><td>Tier 4</td><td>Long-tail / lower-liquidity markets</td><td>20x</td><td>$200,000</td></tr></tbody></table>

Examples of Tier 1 markets include BTC, ETH, SOL, XRP, and BNB.

The exact tier assigned to a pair depends on TurboFlow's market classification rules and may change over time.
