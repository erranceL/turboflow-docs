---
description: >-
  A new type of perpetual trading built around zero trading fees, zero spread
  execution, and a dynamic profit-share model.
icon: pump-impeller
---

# Turbo Perps

### A New Type of Perpetual Trading

Turbo Perps are leveraged perpetual contracts that track live crypto prices with **no trading fees and no spread**. Instead of a fixed fee on every trade, the platform takes a dynamic share of your profit on winning trades only.&#x20;

**Losing trades pay nothing.**&#x20;

This product offers high leverage and asymmetric payouts.

Key properties at a glance:

* **Zero trading fees** — no maker/taker charges
* **Zero spread** — you open and close at the reference price
* **Profit Share only** — the platform earns only when you earn
* **Isolated margin** — each position has its own dedicated collateral
* **Up to 1000x leverage** on BTC, ETH, and other major pairs

#### How Turbo Perps compare to Classic Perps

| Feature            | Classic Perps         | Turbo Perps                  |
| ------------------ | --------------------- | ---------------------------- |
| Trading fee        | 0.02–0.08% per side   | Zero                         |
| Spread             | Embedded in execution | Zero                         |
| Fee when losing    | Charged regardless    | Zero                         |
| Fee when winning   | Charged regardless    | Dynamic profit share only    |
| Platform incentive | Earns on every trade  | Earns only when trader earns |

### The Profit Share Formula (P\_close)

When you close a winning position you don't receive the raw market price P(T). You receive a slightly adjusted closing price P\_close that reflects the platform's profit share cut. The key property: the larger the price move, the smaller the cut — so big directional trades are more profitable on a percentage basis.

### Full Formula

**Close Price**

$$
P_{close} = P_{entry} + Capture \times (P_{exit} - P_{entry})
$$

**Capture**

$$
Capture = \frac{1 - base\_rate}{1 + market\_impact + size\_impact}
$$

**Market Impact**

$$
market\_impact = \frac{1}{(move \times rate\_multiplier)^{rate\_exponent}}
$$

**Size Impact**

$$
size\_impact = \frac{bet\_amount \times leverage}{1{,}000{,}000 \times move \times position\_multiplier}
$$

**Move**

$$
move = \left| \frac{P_{exit}}{P_{entry}} - 1 \right|
$$

Where:

* `move` is the absolute percentage price change.

#### What each term does

<table data-header-hidden><thead><tr><th valign="top">Term</th><th valign="top">What it controls</th><th valign="top">BTC value</th></tr></thead><tbody><tr><td valign="top">base_rate</td><td valign="top">Floor cut — minimum platform share even on infinite moves</td><td valign="top">10%  (0.10)</td></tr><tr><td valign="top">rate_multiplier</td><td valign="top">How fast the cut shrinks as the move grows — higher = faster decay</td><td valign="top">15,000</td></tr><tr><td valign="top">rate_exponent</td><td valign="top">Curve shape of the decay — 1 = linear</td><td valign="top">1</td></tr><tr><td valign="top">position_multiplier</td><td valign="top">Scales the size_impact term per-pair (reflects liquidity depth)</td><td valign="top">1,384.6</td></tr><tr><td valign="top">bust_buffer</td><td valign="top">Extra offset for stop/liquidation trigger price (not in P_close)</td><td valign="top">0.036%</td></tr><tr><td valign="top">leverage</td><td valign="top">Your chosen leverage multiplier</td><td valign="top">up to 1000x</td></tr><tr><td valign="top">bet_amount</td><td valign="top">Your position size in USD (collateral x leverage)</td><td valign="top">user input</td></tr></tbody></table>

#### Step-by-step worked example

Scenario: BTC long, $1,000 margin at 10x leverage.

_Entry price  P\_entry  = $100,000_

_Exit price   P\_exit   = $105,000   (+5% move)_

_bet\_amount             = $10,000   (margin x leverage)_

_base\_rate              = 0.10_

_rate\_multiplier        = 15,000_

_rate\_exponent          = 1_

_position\_multiplier    = 1,384.6_

{% stepper %}
{% step %}
Move size  move = |105,000 / 100,000 - 1| = 0.05  (5%)
{% endstep %}

{% step %}
Market impact  = 1 / (0.05 x 15,000)^1  =  1 / 750  =  0.001333
{% endstep %}

{% step %}
Size impact  = 10,000 / (1,000,000 x 0.05 x 1,384.6)  =  0.0001446
{% endstep %}

{% step %}
Capture ratio  = (1 - 0.10) / (1 + 0.001333 + 0.0001446)  =  0.90 / 1.001478  =  0.8987
{% endstep %}

{% step %}
P\_close  = 100,000 + 0.8987 x 5,000  =  $104,493.50
{% endstep %}
{% endstepper %}

Raw profit on $10,000 position  =  $500.00

Your actual profit               =  $449.35

Platform's share                 =  $ 50.65   (10.1% of raw profit)

#### How the profit share changes with move size (BTC, $1,000 position, 10x)

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

_On large moves (above \~1%) the effective fee converges to base\_rate (10%). Only on very small moves (<0.5%) does the cut noticeably exceed 10%. This asymmetry rewards traders who catch big directional moves._

#### Trigger price for stop-loss and liquidation

The price at which a stop or liquidation actually fires is adjusted by a small per-pair buffer to prevent triggering on micro-wicks:

P\_trigger = P\_close  x  (1  +  trade\_sign  x  bust\_buffer)

trade\_sign:   +1 for Long,   -1 for Short

bust\_buffer:  BTC = 0.036%,  ETH = 0.038%,  DOGE = 0.040%

### Margin System

Turbo Perps use **Isolated Margin** only. Each position has its own collateral ring-fenced from other positions — a loss on one position cannot affect another.

#### Initial Margin Rate (IMR)

The minimum collateral needed to open a position:

IMR = 1 / leverage

_Example  —  10x leverage:  IMR = 10%.  You post $1,000 to open a $10,000 position._

#### Maintenance Margin Rate (MMR)

The minimum ongoing collateral ratio. Falling below this triggers liquidation. Turbo Perps (Profit Share mode) use the following formula:

&#x20;_MMR = min(min(max(0.5 x IMR,  br + br x ln(1000/leverage)),  maxbr),  pair.maxMMR)_

&#x20; _br          =  base maintenance rate for your notional tier_

&#x20; _maxbr       =  7000 / leverage / 10000   (hard ceiling)_

&#x20; _pair.maxMMR =  exchange-set maximum for this pair_

{% hint style="info" %}
At low leverage (e.g. 10x) the floor of 0.5 x IMR = 5% dominates. At very high leverage (100x+) the formula term takes over. Profit Share mode has no deduction offset (MD = 0) unlike Flat-Fee V3.
{% endhint %}

#### Maintenance Margin (MM) in USD

MM  =  Position Size (USD)  x  MMR

_Example  —  $10,000 position at MMR 5%:  MM = $500.  Your buffer before liquidation is $500._

#### Leverage vs margin buffer — quick reference

| 5x   | 20.0% | 10.0% | \~10% adverse move  |
| ---- | ----- | ----- | ------------------- |
| 10x  | 10.0% |  5.0% | \~5% adverse move   |
| 20x  |  5.0% |  2.5% | \~2.5% adverse move |
| 50x  |  2.0% |  1.0% | \~1% adverse move   |
| 100x |  1.0% |  0.5% | \~0.5% adverse move |

### Liquidation

#### Liquidation & bankruptcy price formulas

| Direction    | Liquidation price                        | Bankruptcy price                  |
| ------------ | ---------------------------------------- | --------------------------------- |
| Long  (Buy)  | Entry  -  (Margin - MM) / Size  x  Entry | Entry  -  Margin / Size  x  Entry |
| Short (Sell) | Entry  +  (Margin - MM) / Size  x  Entry | Entry  +  Margin / Size  x  Entry |

{% hint style="info" %}
If either result is negative it is floored at $0.
{% endhint %}

#### Worked example  —  BTC Long 10x

Entry price  =  $100,000

Position     =  $10,000  (0.1 BTC equivalent)

Margin       =  $1,000   (10x leverage, IMR 10%)

MMR          =  5%   =>   MM = $500

Liquidation price  =  100,000 - (1,000 - 500) / 10,000 x 100,000

&#x20;                             \=  100,000 - 5,000

&#x20;                             \=  $95,000

Bankruptcy price   =  100,000 - 1,000 / 10,000 x 100,000

&#x20;                               \=  100,000 - 10,000

&#x20;                               \=  $90,000

The engine tries to fill at $95,000. If no fill is available, the ultimate floor is the $90,000 bankruptcy price.

#### Trigger condition

| Direction | Liquidation fires when…           |
| --------- | --------------------------------- |
| Long      | Mark Price  <=  Liquidation Price |
| Short     | Mark Price  >=  Liquidation Price |

#### Profit Share adjustment in liquidation (important)

For a winning Profit Share position, the system uses P-Close adjusted PnL at all times

Classic Perps:    Effective equity  =  Collateral  +  Full unrealised PnL

Turbo Perps:      Effective equity  =  Collateral  +  P-Close adjusted PnL (lower than full PnL when trade is winning)

{% hint style="info" %}
On a winning position your margin ratio improves more slowly than a standard perp because the profit share is pre-discounted in the equity calculation. This is expected — always rely on the platform's displayed liquidation price.
{% endhint %}

### Funding Fee

An interest charge accrues on open positions on various cycles ( depending on pair) to reflect the cost of leveraged exposure.

### Dynamic Risk Engine

A real-time risk engine monitors market conditions and may tighten parameters during periods of extreme volatility or low liquidity. Existing open positions are not immediately affected — changes apply to new positions only.

| Maximum leverage      | Reduced   | New positions capped at lower leverage  |
| --------------------- | --------- | --------------------------------------- |
| MMR                   | Increased | New positions need more margin buffer   |
| Liquidation threshold | Tightened | Liquidation price moves closer to entry |
| Max position size     | Reduced   | Large opens restricted                  |

### Pair Parameters Reference

These are the live configuration values used in P\_close calculations, funding, and liquidation triggers.

| BTC  | 10% | 15,000 | 1 | 1,384.6 | 0.036% | 1000x |
| ---- | --- | ------ | - | ------- | ------ | ----- |
| ETH  | 10% | 15,000 | 1 | 923.1   | 0.038% | 1000x |
| DOGE | 10% | 15,000 | 1 | 401.4   | 0.040% | 1000x |

{% hint style="info" %}
BTC, ETH, and DOGE share the same base\_rate and rate\_multiplier. The position\_multiplier reflects each pair's liquidity depth — higher = a given position size has less fee impact.
{% endhint %}

### Risk Disclosure

Turbo Perps are high-risk leveraged products. Prices can move rapidly and leveraged positions may be liquidated within seconds.

* Leverage magnifies both gains and losses — 10x means 100% margin loss on a 10% adverse move.
* Liquidation can happen very quickly during volatile market conditions.
* The profit share cut is higher on small moves — scalping strategies face a larger effective fee.
* P-Close adjustment means winning positions have less equity cushion than raw PnL suggests.
* Risk parameters can change dynamically; monitor your open positions and margin ratio regularly.
* Past performance of any strategy does not guarantee future results.

_Only trade with capital you can afford to lose entirely. Keep leverage conservative and use the platform risk tools available to you._
