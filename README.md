# Pine Strategy Indicators v7

## Overview

A collection of five technical indicators for TradingView, implemented in Pine Script (v5/v6). These indicators provide analysis tools for measuring market momentum, trend direction, and price strength across multiple timeframes.

## Included Indicators

### Balance of Power

**Purpose:** Measures the strength of buying versus selling pressure in the market.

**Core Logic:** Calculates the ratio of price change (close - open) to the trading range (high - low) for each period. Values oscillate around zero, with positive values indicating buyer dominance and negative values indicating seller dominance.

**Key Parameters:**
- None (uses default OHLC values)

![Balance of Power](images/Balance-of-Power.png)

**Typical Use Case:** Identifying market strength and potential reversals by observing divergences between price and BOP values. Effective when combined with trend-following indicators.

---

### McGinley Dynamic

**Purpose:** Adaptive moving average that adjusts smoothing based on market speed.

**Core Logic:** Uses a self-adjusting mechanism that modifies the smoothing factor based on the ratio of price to the previous indicator value. The formula incorporates a fourth-power adjustment: `mg[1] + (source - mg[1]) / (length * (source/mg[1])^4)`.

**Key Parameters:**
- **Length:** Period for calculation (default: 14, min: 1)

![McGinley Dynamic](images/McGinley-Dynamic.png)

**Typical Use Case:** Trend identification with reduced lag compared to traditional moving averages. Price crossing above/below the line signals potential trend changes. Overlay on price chart for dynamic support/resistance levels.

---

### Relative Vigor Index

**Purpose:** Measures the conviction of a price trend by comparing close-open range to high-low range.

**Core Logic:** Applies symmetrically weighted moving average (SWMA) to the difference between close-open and high-low values, then sums over the specified period. Generates a main line and signal line (SWMA of the main line).

**Key Parameters:**
- **Length:** Period for RVI calculation (default: 10, min: 1)
- **Offset:** Display offset in bars (default: 0, range: -500 to 500)

![Relative Vigor Index](images/Relative-Vigor-Index.png)

**Typical Use Case:** Confirming trend direction and spotting potential reversals. Crossovers between the RVI line and signal line generate trading signals. Most effective in trending markets.

---

### Vortex Indicator

**Purpose:** Identifies trend initiation and measures trend strength using positive and negative vortex movements.

**Core Logic:** Calculates two directional movements: VI+ (upward vortex from high to prior low) and VI- (downward vortex from low to prior high). Each is normalized by the sum of true ranges over the period.

**Key Parameters:**
- **Length:** Look-back period for calculation (default: 14, min: 2)

![Vortex Indicator](images/Vortex-Indicator.png)

**Typical Use Case:** Detecting trend changes when VI+ crosses above VI- (bullish signal) or below (bearish signal). Strength of divergence between the lines indicates trend momentum.

---

### Woodies CCI

**Purpose:** Enhanced Commodity Channel Index implementation with dual timeframes and histogram visualization.

**Core Logic:** Plots two CCI calculations simultaneously—a fast "turbo" CCI and a standard 14-period CCI. Histogram colors change based on whether the last five CCI 14 values are all positive (teal) or all negative (red).

**Key Parameters:**
- **CCI Turbo Length:** Fast CCI period (default: 6, range: 3-14)
- **CCI 14 Length:** Standard CCI period (default: 14, range: 7-20)

![Woodies CCI](images/Woodies-CCI.png)

**Typical Use Case:** Identifying overbought/oversold conditions and trend direction. Values above +100 suggest bullish momentum, below -100 suggest bearish momentum. Zero-line crosses indicate potential trend changes.

---

## How to Use

1. Open TradingView and navigate to the Pine Editor
2. Copy the desired indicator code from the `indicators/` folder
3. Paste into a new Pine Editor tab
4. Click "Add to Chart" to apply the indicator
5. Adjust parameters through the indicator settings menu as needed

## Disclaimer

These indicators are provided for educational purposes only. They are not financial advice. Past performance does not guarantee future results. Always conduct thorough analysis and risk management before making trading decisions.
