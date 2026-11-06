# ⚡ Quant Market Making Arena

[![Live Production](https://img.shields.io/badge/Live-Production%20Demo-00f59b?style=for-the-badge&logo=vercel)](https://quant-market-making-arena.vercel.app)
[![License: MIT](https://img.shields.io/badge/License-MIT-00d2ff?style=for-the-badge)](LICENSE)
[![Quantitative Finance](https://img.shields.io/badge/Microstructure-Avellaneda--Stoikov-ffd600?style=for-the-badge)](https://github.com/Sunzzx/quant-market-making-arena)

A high-frequency algorithmic market-making simulator and interactive browser arena. Master inventory risk aversion, control Avellaneda-Stoikov reservation prices, survive Poisson flash crashes, and harvest the bid-ask spread in real-time.

---

## 📐 Mathematical Foundations

The simulation engine models high-frequency order book microstructure according to the seminal **Avellaneda & Stoikov (2008)** framework:

### 1. Mid-Price Dynamics (Jump-Diffusion)
The reference asset price $S_t$ follows a Geometric Brownian Motion with compound Poisson jump shocks:
$$dS_t = \mu S_t dt + \sigma S_t dW_t + J_t dN_t$$
where $N_t$ is a Poisson counter with intensity $\lambda_{jump}$ and $J_t \sim \mathcal{N}(\mu_J, \sigma_J^2)$.

### 2. Reservation (Indifference) Price
A market maker holding inventory $q$ at time $t$ with risk-aversion parameter $\gamma$ and volatility $\sigma$ quotes around an optimal reservation price:
$$r(s, q, t) = s - q \gamma \sigma^2 (T - t)$$
*When inventory is positive ($q > 0$), the reservation price shifts downward to deter further buys and attract aggressive sells.*

### 3. Optimal Half-Spread & Quotes
The optimal bid and ask quotes $(r^a, r^b)$ solve:
$$\delta^a(s, q) + \delta^b(s, q) = \gamma \sigma^2 (T - t) + \frac{2}{\gamma} \ln\left(1 + \frac{\gamma}{\kappa}\right)$$
where $\kappa$ is the order flow liquidity parameter.

---

## 🎮 Features
- **Real-Time Limit Order Book (LOB) Canvas:** Live visual depth chart rendering bids and asks dynamically.
- **Dynamic Inventory Shading:** Adjust $\gamma$ (risk aversion) and half-spread $\delta$ on the fly to see quotes skew.
- **Regime Switching:** Test your market maker against Normal Flow, Institutional Sweeps, and Flash Crashes.
- **Real-Time PnL & Sharpe Tracking:** Continuous equity curve updating with tick-by-tick marked-to-market inventory.
- **Delta Auto-Hedging:** Automated market-order hedging when inventory exceeds threshold limits.
- **Built-in Freemium Monetization:** 3 free rounds/day with automated Stripe checkout hook for Pro Python Bot Exporter.

---

## 🚀 Quick Start
Run locally with any static web server:
```bash
# Python
python3 -m http.server 8080

# Or Node.js
npx serve .
```
Visit `http://localhost:8080`.

---

## 🛠️ Tech Stack & Zero-Cost Architecture
- **Frontend:** Pure HTML5, Tailwind CSS, Canvas API, Web Audio API (zero runtime build dependencies).
- **Hosting:** 100% Free Tier on Vercel (`*.vercel.app`) / GitHub Pages (`sunzzx.github.io`).
- **SSL & CDN:** Global Edge CDN via Vercel / GitHub Pages.

---

## 👤 Author
**Ayush Kandwal (@Sunzzx)**  
AI & Quant Researcher (Dual IIT Scholar)  
- Portfolio: [https://sunzzx.github.io/ayush-kandwal-portfolio/](https://sunzzx.github.io/ayush-kandwal-portfolio/)
- GitHub: [@Sunzzx](https://github.com/Sunzzx)
