# 🧠 Reinforcement Learning for Multi-Asset Portfolio Optimization

## 📈 Project Overview

This project investigates the application of **Reinforcement Learning (RL)** to financial portfolio management involving multiple assets. The objective is to train an RL agent to dynamically allocate capital among three stocks — **Apple (AAPL)**, **Motorola (MSI)**, and **Starbucks (SBUX)** — using historical daily price data.

A **linear Q-learning algorithm** with momentum is implemented to make discrete trading decisions. Its performance is compared to benchmark strategies including Buy-and-Hold, Random Trading, and Mean-Variance Optimization (Markowitz portfolio).

---

## 🎯 Goals

- Model portfolio management as a sequential decision-making problem.
- Train an RL agent to learn a policy for buying, holding, or selling assets.
- Benchmark RL performance against classical trading strategies.
- Analyze agent behavior and portfolio evolution over time.

---

## 🧮 Methodology

### RL Environment

- **State (`s_t ∈ ℝ⁷`)**:
  - Number of shares owned per asset (3)
  - Current prices (3)
  - Available cash (1)

- **Actions**:
  - Each action is a triplet of discrete decisions: {Sell All, Hold, Buy Max} for each stock.
  - Total of 27 discrete actions (3³ combinations).

- **Reward**:
  - Defined as the **change in total portfolio value** between time steps:
    \begin{equation*}
    r_{t+1} = π_{t+1} - π_t
    \end{equation*}

- **Execution Rules**:
  - Always sell before attempting buys.
  - Buy in a round-robin fashion until cash runs out.

### Q-Learning Agent

- **Q-function** approximated using a **linear model**:
  \begin{equation*}
  Q(s_t, a) = W_a ⋅ s_t + b_a
  \end{equation*}
  - `W`: weight matrix (27 × 7)
  - `b`: bias vector (27 × 1)

- **Training**:
  - Momentum-based updates to improve convergence.
  - Epsilon-greedy exploration with scheduled decay.

---

## 🧪 Results

- The RL agent demonstrates **adaptive behavior** to changing market conditions.
- Achieves **comparable or superior performance** to Buy-and-Hold and Random Trading strategies.
- The Markowitz portfolio shows stronger performance in hindsight but lacks adaptability.
- RL policy evolves over time, learning to rebalance the portfolio in response to price dynamics.

---

## 📂 Project Structure

```bash
├── 40006_Axel_Saint_Romain.ipynb  # Main notebook with full implementation
├── data/                          # Contains price data for AAPL, MSI, SBUX
├── README.md                      # Project documentation
