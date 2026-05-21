---
description: >-
  How TurboFlow uses market parameters to manage leverage, margin, and
  platform-level risk.
icon: shield
---

# Parameters & Risk Logic

### Overview

TurboFlow applies a tiered margin and leverage framework across its perpetual markets.

Different markets have different liquidity depth, volatility, spread conditions, and execution risks. For this reason, TurboFlow does not apply the same leverage, position cap, or margin requirement to every trading pair.

Instead, supported markets are grouped into different risk tiers. More liquid markets may support higher leverage and larger position sizes, while less liquid or longer-tail markets require lower leverage, smaller position limits, and stricter margin requirements. The detailed framework classifies markets into multiple tiers and applies bracket-based leverage, margin, and position cap rules.

_In simple terms:_

**Deeper markets can support more leverage.**

**Less liquid markets require stricter risk limits.**

### Market Tiering

TurboFlow classifies supported markets into risk tiers based on market quality and platform risk exposure.

Key factors may include:

* liquidity depth;
* spread conditions;
* volatility;
* execution risk;
* market maturity;
* asset category;
* trading activity;
* liquidity provider requirements.

Core assets with deeper liquidity may be assigned to higher tiers, allowing higher maximum leverage and larger position capacity. Long-tail assets or markets with thinner liquidity may be assigned to lower tiers, where leverage and position limits are more conservative.

This approach helps ensure that leverage levels are aligned with actual market conditions rather than applying a one-size-fits-all model.

### Position Size and Leverage

TurboFlow uses a bracket-based system for position size.

As a user’s position size increases, the maximum available leverage may decrease. This means a smaller position may be eligible for higher leverage, while a larger position in the same market may require more margin and lower leverage.

The logic is straightforward:

Larger positions create greater liquidation and market impact risk. Therefore, larger positions require stricter margin requirements.

This helps reduce excessive risk from oversized high-leverage positions and supports a more stable trading environment.

### Initial Margin

Initial Margin is the minimum margin required to open a position.

Higher leverage reduces the initial margin required to enter a position, but it also makes the position more sensitive to price movement.

Users should understand that using higher leverage may increase the probability of rapid liquidation during volatile market conditions.

### Maintenance Margin

Maintenance Margin is the minimum margin required to keep a position open.

If the margin available for a position falls below the required maintenance level, the position may be subject to liquidation under platform rules.

Maintenance margin is designed to help protect users, liquidity providers, and the platform from excessive downside risk during adverse market movement.

### Maintenance Deduction

TurboFlow’s bracket-based margin framework may use a maintenance deduction mechanism to smooth margin requirements across different position brackets.

The purpose of this mechanism is to avoid sudden jumps in maintenance margin when a position crosses from one bracket into another.

This helps make margin requirements more continuous and predictable across different position sizes.

### Why This Matters

TurboFlow’s risk framework is built around several core principles.

1. **Liquidity-Based Risk Control**

More liquid markets can generally support higher leverage. Less liquid markets require more conservative parameters.

2. **Size-Based Margin Scaling**

Larger positions require stricter margin requirements. This helps reduce liquidation pressure and platform-level exposure.

3. **Dynamic Risk Boundaries**

Risk parameters may vary by market, asset, position size, volatility, liquidity, and platform conditions.

4. **Platform Stability**

Margin and leverage limits are designed to help maintain a more stable trading environment, especially during periods of market volatility.

5. **User Protection**

By applying stricter limits to larger positions and less liquid markets, TurboFlow aims to reduce the probability of disorderly liquidation, extreme losses, and unnecessary platform risk.

### User Impact

For users, this means:

* different markets may have different maximum leverage;
* the same market may have different leverage limits depending on position size;
* larger positions may require more margin;
* lower-liquidity assets may have stricter position limits;
* liquidation risk increases when using higher leverage;
* live platform parameters may change based on market conditions.

Users should always check the live trading interface before opening a position. The interface will display the applicable leverage, margin requirement, and risk parameters for the selected market and position size.

### Parameter Updates

TurboFlow may update market tiers, leverage limits, position caps, margin requirements, maintenance margin settings, and other risk parameters from time to time.

Updates may be based on:

* market volatility;
* liquidity changes;
* spread conditions;
* trading activity;
* risk exposure;
* liquidity provider requirements;
* product or platform updates.

The latest parameters shown in the live trading interface and official platform rules should be treated as the source of truth.

### Risk Warning

Perpetual contracts and leveraged trading involve substantial risk.

High leverage can amplify both profits and losses. Users may lose part or all of their margin. Market volatility, liquidity conditions, price gaps, funding costs, and liquidation mechanisms may all affect trading outcomes.

Before trading, users should fully understand:

* how leverage works;
* how margin is calculated;
* how liquidation may occur;
* how position size affects risk;
* how market liquidity affects execution;
* whether perpetual products are suitable for their risk tolerance.

TurboFlow does not guarantee profits, execution outcomes, or protection from losses. Users should trade responsibly and should not trade with funds they cannot afford to lose.

**For detailed tier definitions, bracket caps, leverage levels, and margin formulas, please refer to the TurboFlow Perpetuals: Margin and Leverage Framework PDF below.**

{% file src="../../.gitbook/assets/TurboFlow Perpetuals_Margin and Leverage Framework.pdf" %}

### Important Notice

This page provides a general explanation of TurboFlow’s margin and risk logic. Specific parameters may vary by market, asset, position size, liquidity conditions, and platform configuration.

Users should always refer to the live trading interface and official platform rules for the latest applicable parameters.
