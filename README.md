# Quant Research Prep: Strategies, Market Microstructure & Algorithms

A working collection of notebooks built while preparing for quantitative research internships: trading strategy prototypes, market-making/microstructure models, and coding/algorithms practice.

---

## Repo Structure

| Notebook | Area | What it covers |
|---|---|---|
| `Avellaneda-Stoikov.ipynb` | Market making | Optimal market-making model (Avellaneda & Stoikov) — reservation price and optimal bid/ask spread as a function of inventory risk and time horizon |
| `LOB.ipynb` | Market microstructure | Limit order book mechanics — book construction, price-time priority, and order flow simulation |
| `IntraDayVWAP.ipynb` | Execution | Intraday VWAP tracking/benchmarking for execution algorithms |
| `vwap_mean_reversion(2).ipynb` | Strategy | Mean-reversion signal built around deviations from VWAP |
| `PairsKalman.ipynb` | Statistical arbitrage | Pairs trading with a Kalman filter for dynamic hedge-ratio estimation  |
| `GridPaths.ipynb` | Algorithms / strategy | Path Counting exercise with DP |
| `Kelly.ipynb` | Position sizing / risk | Kelly criterion for optimal bet/position sizing given edge and odds |
| `Majority.ipynb` | Algorithms (DSA) | Majority element problem  |
| `SubArraySum.ipynb` | Algorithms (DSA) | Subarray sum problems (e.g., Sliding Window) |


---

## Repo Sections

### 1. Trading Strategies & Execution
- `Avellaneda-Stoikov.ipynb` — market-making quote generation
- `IntraDayVWAP.ipynb`, `vwap_mean_reversion(2).ipynb`: execution benchmarking and mean-reversion signal generation around VWAP
- `PairsKalman.ipynb` — statistical arbitrage via adaptive pairs trading

### 2. Market Microstructure
- `LOB.ipynb`: limit order book simulation and order-flow mechanics

### 3. Risk & Position Sizing
- `Kelly.ipynb`: Kelly criterion sizing

### 4. Algorithms / Coding Practice (DSA)
- `Majority.ipynb`, `SubArraySum.ipynb`, `GridPaths.ipynb`, standard interview-style algorithm problems, kept alongside the finance notebooks as coding-interview prep

### 5. Portfolio Construction Pipeline *(new module)*
A three-stage systematic allocation pipeline, added as its own subfolder:

```
portfolio_pipeline/
├── stage1_cdar_entropy.py        # Minimum-entropy CDaR optimization
├── stage2_black_litterman.py     # Black-Litterman using Stage 1 as the implied-view prior
├── stage3_vol_target.py          # Volatility targeting with leverage and financing cost
└── pipeline_README.md            # Full math + exercises for this module
```

- **Stage 1:** minimizes Conditional Drawdown-at-Risk with an entropy penalty to avoid concentrated allocations
- **Stage 2:** feeds Stage 1's weights into Black-Litterman as the implied equilibrium return prior, then blends with explicit views
- **Stage 3:** scales the resulting weights by an EWMA-vol-targeting leverage factor, net of financing cost

---

## Setup

```bash
git clone <this-repo-url>
cd <repo-name>
pip install -r requirements.txt   # numpy, pandas, cvxpy, scipy, matplotlib, jupyter
jupyter notebook
```

---

## Roadmap

Planned additions, roughly in order:

- [ ] Factor model backtest (Fama-French style long-short on residual alpha)
- [ ] Regime detection (HMM or volatility-regime classifier) feeding into Stage 3's `sigma_target`
- [ ] Simple market-making strategy backtest against `LOB.ipynb`'s simulated order flow
- [ ] Walk-forward feature research pipeline with information-coefficient (IC) evaluation and explicit lookahead/multiple-testing guards
- [ ] Ablation table comparing raw Stage 1 weights vs. +BL vs. +vol-target vs. full pipeline

---
