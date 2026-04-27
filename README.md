# Hourly Regime detector for BTC

A regime detection model trained on custom-engineered data taken from the market.

**Live:** https://attemptfour.github.io/regime_detector_dashboard/

Trained on data ranging from 2019-09-20 to 2025-09-01 (49,003 hours). Tested on data from 2025-09-01 to 2026-04-16 (5,445 hours).

## What this shows

Three charts, synced on the time axis:

- **Price chart** — BTC log price, with each hour rendered as a regime-colored dot
- **Posteriors** — smoothed regime ownership over time
- **Entropy** — model confidence over time

Right sidebar lists 10 regimes with population %, return statistics, and self-transition probabilities. Click any regime for detail.

## Tech

Single-page HTML, vanilla JavaScript, Plotly.js. No backend, no build step. Hosted on GitHub Pages.

---

*Not investment advice.*
