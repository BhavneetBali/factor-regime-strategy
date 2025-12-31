# Factor Investing with Regime-Aware Deployment (NIFTY 50)

## Overview

This project studies whether regime-aware deployment improves the risk-adjusted performance of cross-sectional factor strategies in Indian equities.
The strategy combines Momentum, Value, and Quality factors and compares:
- Always-on factor exposure
- Regime-switched exposure based on market trends
- Benchmark performance (NIFTY 50)
The focus is on portfolio construction, execution discipline, and drawdown control, rather than pure signal mining.

## Strategy Design

### Universe
- NIFTY 50 constituents
- Split into Banks and Non-Banks to account for valuation metric differences

### Rebalancing
- Portfolio rebalanced quarterly
- Performance evaluated using monthly returns

### Factor Definitions
| Factor   | Definition                  |
| -------- | --------------------------- |
| Momentum | 6–1 and 12–1 price momentum |
| Value    | PE, PB (bank-adjusted)      |
| Quality  | ROE                         |

Factor scores are computed using rank-based composites with fixed weights.

### Regime Definition

Market regime is defined independently of factor signals:
- **Risk-on:** NIFTY 50 trailing 12-month return > 0
- **Risk-off**: otherwise

When risk-off, the factor strategy is deployed.
When risk-on, exposure shifts to the benchmark.

This ensures **no signal overlap** between regime detection and factor construction.

# Key Results (3-Year Sample)
| Strategy             | CAGR | Volatility | Sharpe | Max Drawdown |
| -------------------- | ---- | ---------- | ------ | ------------ |
| Always-On 6–1        | ~20% | ~13%       | >1.0   | ~(-11%)        |
| Always-On 12–1       | ~19% | ~15%       | ~0.9   | ~(-10%)        |
| Regime-Switched 6–1  | ~13% | ~13%       | ~0.53  | ~(-8%)         |
| Regime-Switched 12–1 | ~12% | ~13%       | ~0.51  | ~(-8%)         |
| Benchmark            | ~11% | ~13%       | ~0.44  | ~(-8%)         |

# Key Insights
- Always-on factor strategies maximize returns but suffer from higher tail risk
- Regime-aware deployment materially reduces drawdowns
- Over longer samples, slower momentum (12–1) becomes more robust
- Once regime logic is applied, differences between momentum speeds narrow

# Assumptions & Limitations

- Fundamentals are treated as a static snapshot to avoid look-ahead bias
- No transaction costs or slippage included
- Index composition assumed constant
- Results are indicative and not investment advice

# Future Work

- Point-in-time fundamentals with reporting lags
- Point-in-time fundamentals with reporting lags
- Volatility-based regime definitions
- Out-of-sample validation

# Disclaimer

This project is for **educational and research purposes only**.










