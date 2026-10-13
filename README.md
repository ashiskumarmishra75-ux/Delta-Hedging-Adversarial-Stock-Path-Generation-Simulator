# Delta Hedging & Stock Path Generation Simulator

Welcome to the **Delta Hedging & Stock Path Generation Simulator**. In this project, we build a quantitative finance simulator designed to model how traders manage risk when dealing with financial derivatives. The core objective is to implement and analyze two foundational components: **Stock Path Generation** and **Delta Hedging Engines**. 

Additionally, we implement an advanced extension featuring an **Adversarial Stock Path Generator** inspired by recent research in data-driven mathematical finance ([Hirano et al., 2023](https://arxiv.org/pdf/2307.13217)).

---

## 🛠️ Complete Simulation Pipeline
Our architecture models a production-grade quantitative trading backtester:
```
Stock Path Generation ──> Option Payoff Calculation ──> Delta Hedging ──> Transaction Cost Modelling ──> P&L Analysis ──> Strategy Comparison
```

---

## 📋 Features & Methodology

### 1. Stock Path Generation
In real financial markets, stock prices fluctuate constantly due to supply, demand, order flow imbalances, macroeconomic news, and volatility shocks. To evaluate our strategies under multiple market regimes, we implement a flexible path generation engine:
*   **Standard Baselines:** Continuous price paths built using standard **Geometric Brownian Motion (GBM)** models.
*   **Realistic Enhancements:** Extended simulations that incorporate stochastic volatility adjustments, sudden jumps (Poisson jump-diffusion process), structural market crashes, and stressed macro scenarios.

### 2. Delta Hedging Engine
When an institution sells or holds an option contract, their portfolio value scales dynamically with the underlying asset price. 
*   Our engine minimizes this directional exposure by continuously rebalancing positions in the underlying stock at fixed discrete time steps.
*   **Market Frictions:** We implement proportional transaction costs ($c$) to simulate execution drag. This tracks realistic trading mechanics, demonstrating why hyper-frequent rebalancing is sub-optimal in practice.

### 3. Strategy Comparison
We evaluate performance by backtesting different risk-management strategies over simulated distributions and historical timelines (such as the S&P 500 and BVSP indices):
*   **Traditional Baseline:** Analytically derived Black–Scholes delta formulas.
*   **Learning-Based Framework:** Computational/data-driven Deep Hedging architectures.
*   **Metrics:** Comparisons are judged on Final Profit & Loss (P&L) distribution profiles, total hedging error variance, downside risk, and Conditional Value at Risk (CVaR).

### 4. Advanced Extension: Adversarial Deep Hedging
To ensure our hedging engine is robust under structural breaks, we implement an adversarial framework structured as a min-max game (akin to a Generative Adversarial Network):
*   **The Hedger (Agent):** Optimizes positions to maximize a specified utility function (e.g., Entropic Risk Measure or Expected Shortfall) under terminal wealth.
*   **The Generator (Adversary):** An RNN-based architecture that learns to output the most unfavorable price path perturbations designed to maximize the hedger's tracking error.
*   This removes explicit dependence on parametric price models and exposes vulnerabilities within standard risk rules.

---

## 💻 Tech Stack
*   **Core Systems:** Python, NumPy, SciPy
*   **Deep Learning & Adversarial Optimization:** PyTorch (for neural network models and GPU acceleration)
*   **Data Analysis & Plots:** Pandas, Matplotlib

---

## 🚀 Getting Started

### Prerequisites
Ensure you have the required packages installed:
```bash
pip install numpy pandas torch matplotlib scipy
```

## 📊 References & Academic Base
*   Hirano, M., Minami, K., & Imajo, K. (2023). *Adversarial Deep Hedging: Learning to Hedge without Price Process Modeling*. [arXiv:2307.13217](https://arxiv.org/pdf/2307.13217).
*   Buehler, H., Gonon, L., Teichmann, J., & Wood, B. (2019). *Deep Hedging*. Quantitative Finance, 19(8), 1271-1291.

---
*Disclaimer: This project is constructed for educational and quantitative research purposes. AI responses or model artifacts may include mistakes.*

