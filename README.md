# Exploring Pricing Strategies for PizzaHub 

Applied pricing analytics project for PizzaHub’s 4 regions (Jan–Apr 2023). Combines EDA, causal DiD, elasticity estimation and multi-armed bandits on daily order data to compare uniform vs region-specific discounts and recommend profit-maximising pricing.

---

## 1. Project Overview

This repository analyses how different pricing levers (pizza price and per-mile delivery fee) impact demand, revenue, and profit across four regions of a food-delivery platform.

In March 2023, PizzaHub introduced:
- **Region 3:** ~5% discount on food price  
- **Region 4:** ~5% discount on delivery fee  
- **Regions 1 & 2:** Control regions (no policy change)

Using this quasi-experiment, we:
- Quantify demand response to price and fee changes
- Estimate price and fee elasticities
- Measure the causal impact of discounts on profit using **Difference-in-Differences (DiD)**
- Simulate optimal pricing under different strategies
- Learn data-driven prices via **multi-armed bandits (MAB)**

---

## 2. Key Questions

1. How sensitive is demand to:
   - Pizza price?
   - Delivery fee?
2. Did the March discounts in Regions 3 & 4 actually increase profit?
3. Is **uniform pricing** across regions dominated by:
   - Region-specific pricing?
   - Two-part tariffs (food price + per-mile fee)?
4. Can bandit algorithms learn (near) optimal prices from data over time?

---

## 3. Methods

- **EDA & Feature Engineering**
  - Daily aggregates (orders, revenue, profit)
  - Pre/post intervention flags (pre-Mar 1 vs post-Mar 1)
  - Treatment indicators for Region 3 & Region 4
  - Effective total price, log transforms, distance buckets, etc.

- **Econometric Models**
  - Linear and log-linear demand models  
  - **Difference-in-Differences (DiD)** to isolate the March policy effect  
  - Elasticity calculations for both food price and delivery fee  

- **Pricing Simulations**
  - Baseline vs counterfactual pricing scenarios
  - Uniform pricing vs third-degree price discrimination vs two-part tariffs
  - Profit and consumer surplus comparisons

- **Multi-Armed Bandits (MAB)**
  - Arms = discrete price/fee levels via a composite `Price_day`
  - **Isotonic regression** to fit a monotone demand curve  
  - Algorithms: ε-greedy, UCB1, Thompson Sampling  
  - Comparison between static optimum and bandit-learned policies

---

## 4. Repository Structure

├─ notebooks/            # EDA, DiD, elasticity, bandit experiments
└─ README.md
