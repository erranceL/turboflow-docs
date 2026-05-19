---
description: Event Contracts are TurboFlow’s short-cycle, event-based market products.
icon: binary
---

# Event Contracts

### Overview

They are designed to let users take a directional view on the outcome of a defined market event within a clearly specified time window, with settlement taking place at a fixed expiration point. Structurally, Event Contracts share certain characteristics with short-dated, European-style binary payoff instruments: users select a direction before entry, the outcome is determined only at expiration, and the payout is based on whether the selected outcome condition is met under TurboFlow’s settlement rules.

Unlike long-duration leveraged positions, users do not need to manage funding rates, margin adjustments, liquidation thresholds, or complex order types. Instead, each contract focuses on a simple market question:

Will the selected market outcome be higher or lower at the end of the chosen time window?

With trading cycles starting from as short as **30 seconds** and entry amounts starting from **as little as $2,** Event Contracts are built to make market participation faster, more intuitive, and more accessible for everyday users.

Event Contracts can be viewed as a short-cycle, market-driven complement to prediction markets. While traditional prediction markets often focus on longer-duration real-world outcomes, TurboFlow’s Event Contracts focus on faster, more frequent outcome-based participation across supported markets.

At launch, Event Contracts are built around major crypto assets such as BTC and ETH. TurboFlow plans to gradually expand into broader global market assets such as oil and gold, as well as sports and event-based prediction markets. In June, TurboFlow is expected to introduce football-related prediction markets as part of its roadmap toward the 2026 FIFA World Cup cycle.

Unlike fixed low-return pure chance products, Event Contracts are based on observable market or event outcomes. The payout structure is designed to be more competitive, while the result depends on directional judgment, timing, market context, and strategy. Users may form views based on momentum, volatility, time-window selection, asset behavior, event probability, or other market signals before entering a contract.

In this sense, Event Contracts combine three elements:

* **option-like payoff logic,** where outcomes are settled at expiration;
* **prediction-market style participation,** where users express a view on a defined outcome;
* **short-cycle trading experience,** where settlement windows can be much shorter than traditional prediction markets or derivatives products.

### How It Works

With Event Contracts, users participate by selecting a market, choosing a settlement window, entering an amount, and taking a directional view on the next outcome.

A typical flow looks like this:

1. Choose a supported market
2. Select a contract duration
3. Enter an amount
4. Choose a direction: **Higher or Lower**
5. Wait for the contract to settle at the end of the selected time window

If the final outcome matches the selected direction under TurboFlow’s settlement rules, the order returns the displayed payout. If the selected direction is incorrect, the order settles according to the contract result. If the settlement result is unchanged under platform rules, the user’s principal is returned.

This creates a clear and time-bounded participation loop: users know the market, the direction, the duration, the return rate, and the settlement point before entering the order.

### Core Product Logic

Event Contracts are designed around a defined event, a fixed expiration point, and a conditional payoff.

The product logic can be understood through three core components:

#### 1. Defined Outcome

Each Event Contract is based on a defined outcome condition.

For market-based Event Contracts, this may be whether the Exit Price is higher or lower than the Enter Price at the end of the selected time window.

For future event-based prediction markets, this may be whether a defined event condition is met under the platform’s settlement rules.

#### 2. Fixed Expiration

Event Contracts are settled at a fixed expiration point.

This makes them similar in structure to European-style payoff instruments, where the outcome is determined at expiration rather than continuously during the contract period.

Users do not need to actively close, manage, or adjust the position before expiration. Once the order is entered, the contract runs until the selected settlement time.

#### 3. Conditional Payoff

The payout depends on whether the selected outcome condition is met.

If the user’s selected direction or outcome is correct, the order returns the displayed payout. If it is incorrect, the order settles accordingly based on the contract result. If the result is flat under platform rules, the principal is returned.

This structure makes Event Contracts easy to understand while still allowing users to apply market views, probability assessment, timing, and strategy.

Event Contracts are not designed as long-duration leveraged positions. They are also not simple random-chance products.

The outcome is based on market movement or defined event results over a specific time window. This means users may apply their own market views, timing preferences, probability assessment, volatility expectations, and short-term strategies when participating.

Compared with traditional fixed-odds entertainment products, where payout structures are usually highly unfavorable to users, TurboFlow’s Event Contracts are designed to offer a more competitive and market-driven payout experience. Current return rates may reach around 80% depending on market, direction, duration, liquidity conditions, and platform configuration.

This means that Event Contracts are easy to understand, but not purely random. Users can form strategies around:

* **short-term trend direction;**
* **volatility conditions;**
* **market momentum;**
* **time-window selection;**
* **asset selection;**
* **event probability;**
* **entry timing;**
* **risk control and position sizing.**

The product is simple at the interface level, but the underlying participation can still be strategic.

### Contract Durations

TurboFlow currently supports multiple short-cycle settlement windows for Event Contracts, including:

* **30 sec**
* **1 min**
* **3 min**
* **5 min**
* **15 min**
* **1 hour**

Available durations and supported markets may vary over time based on product design, liquidity conditions, risk management settings, and platform updates.

Shorter durations are designed for users who want faster participation and more immediate settlement. Longer durations may be more suitable for users who prefer a wider time window for market or event outcomes to develop.

### Supported Markets

Event Contracts are currently built around major crypto assets such as BTC and ETH.

As TurboFlow expands its liquidity and pricing infrastructure, the platform aims to gradually support more global market assets and event categories, including:

* crypto assets;
* commodities;
* oil;
* gold;
* sports-related prediction markets;
* other major global market instruments and event-based markets.

**TurboFlow also plans to introduce football-related prediction markets in June, as part of its broader roadmap toward the 2026 FIFA World Cup cycle.**

Supported markets may vary over time. Users should always refer to the live product interface for the latest available markets.

### Pricing and Settlement

Event Contracts display an Enter Price and Exit Price as part of the contract lifecycle.

The Enter Price is recorded when the user enters the order. The Exit Price is recorded at the settlement point of the selected time window.

Settlement pricing is determined through TurboFlow’s oracle-based pricing and settlement system, which is designed to support a consistent and trusted settlement process across short-cycle market activity.

The Enter Price / Exit Price may be generated based on trusted market data sources, internal oracle mechanisms, and platform settlement logic. These values are recorded by TurboFlow’s settlement system and used to determine the result of each Event Contract under the applicable rules.

**Users should always rely on the product interface and official platform rules for the latest displayed values and settlement behavior.**

### Return Rate and Dynamic Odds

Each Event Contract displays a Return Rate and corresponding estimated profit before entry.

The return rate is configured by TurboFlow based on supported markets, selected direction, contract duration, liquidity conditions, volatility, and platform risk management parameters. Users can see the return rate applicable to a specific order before placing it. Once the order is confirmed, that return rate will be used for the settlement of that order.

As TurboFlow expands its institutional liquidity network, including liquidity support from Susquehanna Crypto, Event Contracts are expected to move toward a more dynamic, market-driven pricing experience.

Dynamic odds help Event Contracts become more responsive to real market conditions, including:

* **liquidity depth;**
* **directional demand;**
* **market volatility;**
* **asset-specific risk;**
* **time-window risk;**
* **platform risk exposure.**

This is designed to support fairer pricing, more efficient cost structures, and a healthier long-term market environment for Event Contracts.

In practice, dynamic odds mean that the return rate shown to users may vary across different markets, durations, directions, and market conditions. Users should always check the live return rate shown on the interface before entering an order.

### Flat Result

If the Exit Price equals the Enter Price, the order is considered flat under platform rules.

In this case, the user’s principal is returned, and no profit or loss is generated.

Flat result rules may vary by product configuration or supported market. Users should always refer to the latest official platform rules and product interface.

### Public Market Activity

Event Contracts include visible activity layers designed to make participation more transparent and more interactive.

Users may be able to explore:

* **Public Trades;**
* **Positions;**
* **History;**
* **Leaderboard highlights;**
* **activity displayed in the top scrolling banner.**

These interface elements help users track market activity, monitor participation, and follow standout performance across the platform.

This public activity layer is an important part of the Event Contracts experience. It makes short-cycle market participation more visible, social, and engaging.

### Interface & Experience

TurboFlow’s Event Contracts interface is designed to support fast decision-making and a more visual trading experience.

Depending on product settings and availability, users may be able to access interface features such as:

* **chart display controls;**
* **public feed visibility;**
* **entry line visibility;**
* **settlement reveal effects;**
* **position and history tracking;**
* **leaderboard and public activity displays.**

These features are intended to make short-cycle participation easier to follow, more engaging to use, and more responsive for active users.

TurboFlow aims to combine simple user-facing interaction with more sophisticated market infrastructure behind the scenes.

The user experience is designed to be:

* fast;
* visual;
* time-bounded;
* outcome-focused;
* easy to understand;
* suitable for both casual participation and strategy-driven users.

### How Event Contracts Complement Prediction Markets

Prediction markets allow users to express views on the outcome of future events.

TurboFlow’s Event Contracts bring a similar outcome-based participation model into short-cycle financial and event-based markets. Instead of waiting days, weeks, or months for an event to resolve, users can participate in market-based outcomes over much shorter time windows.

This makes Event Contracts a natural complement to prediction markets:

| Prediction Markets                | Event Contracts                                  |
| --------------------------------- | ------------------------------------------------ |
| Often based on real-world events  | Based on short-cycle market or event outcomes    |
| Usually longer settlement periods | Settlement windows as short as 30 seconds        |
| Event-driven participation        | Market-direction and event-outcome participation |
| Outcome-focused                   | Outcome-focused                                  |
| Often social and community-driven | Designed to be fast, visual, and interactive     |

As TurboFlow expands, Event Contracts, Prediction Markets, TG Mini App experiences, and Perpetual Contracts are expected to form a broader all-in-one onchain trading ecosystem.

Event Contracts can serve as the high-frequency, short-cycle layer within this ecosystem, while prediction markets can support longer-duration event outcomes and more social participation formats.

### Strategic Role in TurboFlow’s Ecosystem

Event Contracts are an important part of TurboFlow’s broader product ecosystem.

They create a bridge between:

* short-cycle trading;
* prediction-style participation;
* event-based outcomes;
* retail-friendly user experience;
* institutional liquidity and pricing infrastructure.

With support from Susquehanna Crypto and future institutional liquidity providers, TurboFlow aims to build a more diversified liquidity network and a more market-driven pricing foundation across its products.

This foundation can support multiple trading verticals, including:

* Event Contracts;
* Prediction Markets;
* TG Mini App experiences;
* 1000x Perpetual Contracts;
* future market-based and event-based products.

Event Contracts are designed to be one of TurboFlow’s key entry points for users who want a fast, simple, and interactive way to participate in market outcomes.

### Why It Matters

Event Contracts add a different kind of market participation layer to TurboFlow.

They are designed to offer:

* shorter trading cycles;
* low entry amounts;
* clear settlement timing;
* intuitive directional participation;
* visible public activity;
* dynamic, market-driven return rates;
* a more interactive experience for retail users;
* a strategic alternative to purely passive prediction-style participation.

Rather than requiring users to manage longer-duration exposure, Event Contracts focus on defined windows, clear directional choices, and a more immediate participation loop.

This makes them especially suitable for users who want a faster, simpler, and more interactive way to participate in market outcomes.

Event Contracts also help TurboFlow bring a broader set of users into onchain markets. Users who may find traditional derivatives too complex, or traditional prediction markets too slow, can participate through a more time-bounded and intuitive product format.

### Important Notice

Event Contracts involve high-risk trading activity and are not suitable for all users.

Supported markets, durations, return rates, settlement behavior, pricing sources, and interface settings may vary over time. Users should always refer to the latest product interface and official platform rules before participating.

Past outcomes, displayed return rates, public activity, or leaderboard performance do not guarantee future results. Users should understand the rules, assess their own risk tolerance, and participate responsibly.

Event Contracts may involve rapid settlement cycles and high-frequency participation. Users should not participate with funds they cannot afford to lose.
