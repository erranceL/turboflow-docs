---
description: >-
  Trading cost models for Classic Perps and Turbo Perps, including the core fee
  formulas.
icon: sack-dollar
---

# Fee Schedule

### Overview

TurboFlow uses two different fee models for perpetuals.

* **Classic Perps** use a flat trading fee plus funding.
* **Turbo Perps** use zero trading fees and a profit-share model on winning trades.
* The live trading interface remains the source of truth for pair-specific settings.

### Classic Perps

#### What you pay

Classic Perps use a standard **flat-fee** structure.

When trading, you may pay:

* a trading fee based on position notional
* slippage based on size and market conditions
* funding while the position stays open

TurboFlow charges the combined open and close trading fee upfront when the position opens. No additional trading fee is charged when the position closes.

#### Trading fee formula

Let:

* `N` = position notional
* `r_open` = open fee rate
* `r_close` = close fee rate

Then:

$$
Trading\ Fee = N \times (r_{open} + r_{close})
$$

If the same fee rate applies on both sides:

$$
Trading\ Fee = N \times 2r
$$

Typical Classic Perps trading fees range from `0.02%` to `0.08%` per side, depending on the pair.

#### Example

For a `$10,000` position at `0.05%` per side:

$$
Trading\ Fee = 10{,}000 \times (0.0005 + 0.0005) = 10
$$

You pay **$10** when the position opens.

#### Funding formula

Funding is calculated hourly.

$$
premium_t = \left(\frac{MarketMakerPerpPrice_t}{SpotIndex_t}\right) - 1
$$

$$
Average\ Premium = mean(premium_1, premium_2, ..., premium_{720})
$$

$$
Funding\ Rate = Average\ Premium + clamp(0.00125\% - Average\ Premium,\ -0.05\%,\ +0.05\%)
$$

$$
Final\ Funding\ Rate = clamp(Funding\ Rate,\ -4\%,\ +4\%)
$$

$$
Funding\ Payment = Position\ Size \times Spot\ Index \times Final\ Funding\ Rate
$$

At a high level:

* if the perp trades above spot, longs pay shorts
* if the perp trades below spot, shorts pay longs
* if the perp trades near spot, funding stays near zero

#### Total Classic Perps cost

Your total trading cost is:

$$
Total\ Cost = Trading\ Fee + Slippage + Net\ Funding\ Paid
$$

### Turbo Perps

#### What you pay

Turbo Perps use a different model.

You pay:

* **zero trading fees**
* **zero spread**
* **zero fee on losing trades**
* a **dynamic profit share** on winning trades only

Instead of charging a separate line-item fee, TurboFlow adjusts the effective close price on profitable trades.

#### Profit-share formula

**Close price**

$$
P_{close} = P_{entry} + Capture \times (P_{exit} - P_{entry})
$$

**Capture**

$$
Capture = \frac{1 - base\_rate}{1 + market\_impact + size\_impact}
$$

**Market impact**

$$
market\_impact = \frac{1}{(move \times rate\_multiplier)^{rate\_exponent}}
$$

**Size impact**

$$
size\_impact = \frac{bet\_amount \times leverage}{1{,}000{,}000 \times move \times position\_multiplier}
$$

**Move**

$$
move = \left| \frac{P_{exit}}{P_{entry}} - 1 \right|
$$

Where:

* `base_rate` is the minimum platform share
* `market_impact` makes small moves less favorable
* `size_impact` scales with effective position size
* `position_multiplier` reflects pair liquidity depth

#### Effective fee on a winning trade

For a profitable trade:

$$
Gross\ Profit = Notional \times \left| \frac{P_{exit} - P_{entry}}{P_{entry}} \right|
$$

$$
Realized\ Profit = Notional \times \left| \frac{P_{close} - P_{entry}}{P_{entry}} \right|
$$

$$
Platform\ Share = Gross\ Profit - Realized\ Profit
$$

If the trade loses, the platform share is:

$$
0
$$

#### Example

For a BTC long with `$1,000` margin at `10x` leverage:

* `P_entry = 100,000`
* `P_exit = 105,000`
* `bet_amount = 10,000`
* `base_rate = 0.10`
* `rate_multiplier = 15,000`
* `rate_exponent = 1`
* `position_multiplier = 1,384.6`

This gives:

* `P_close = 104,493.50`
* `Gross Profit = $500.00`
* `Realized Profit = $449.35`
* `Platform Share = $50.65`

The effective fee in this example is **10.1% of gross profit**.

### Quick comparison

| Product       | Main cost model                | When charged                            |
| ------------- | ------------------------------ | --------------------------------------- |
| Classic Perps | Flat trading fee + funding     | Trading fee upfront, funding while open |
| Turbo Perps   | Profit share on winning trades | Only when the trade closes in profit    |

### Related pages

* [Classic Perps](../products/classic-perps.md)
* [Turbo Perps](../products/turbo-perps.md)
* [Parameters & Risk Logic](../turboflow-core/parameters-and-risk-logic.md)
