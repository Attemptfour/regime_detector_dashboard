# BHMM K=10 dashboard

Interactive visualization of a 10-state Variational Bayesian Hidden Markov Model trained on hourly BTC features (2019-09 → 2026-04, 54,448 hours).

**Live:** https://attemptfour.github.io/bhmm-dashboard/

## What this shows

The model identifies hidden behavioral regimes — psychological market states — from 20 hourly features (price dynamics, velocity, volatility, conviction, macro context). Same mathematics as Mercer's speech recognition, applied to market psychology rather than phonemes.

Three charts, synced on the time axis:

- **Price chart** — BTC log price with a colored regime strip beneath it
- **Posteriors** — smoothed regime ownership over time (1-week rolling average for readability)
- **Entropy** — model confidence over time, with the max-entropy reference line

## Method

Variational Bayesian inference via coordinate-ascent (CAVI) following Murphy (2023, §10.3.6). Auto-pruning via digamma sparsity collapses redundant regimes naturally.

Cross-validated with a methodologically distinct approach (Disentangled-Sticky HDP-HMM Gibbs sampling). Both methods converge on the same regime structure at >93% cosine similarity per regime.

## Causality

The test split (Sep 2025 onward, ~5,445 hours) was inferred via forward-filter only — what a live trader would see. The train split uses the forward-backward smoother, correct for parameter estimation, no leakage to test.

## Validated finding

Regime 9 (Consolidation) precedes volatility expansion within 72 hours. A naive straddle on the first Consolidation hour after 6+ hours of non-Consolidation produced 100% win rate on 32 trades on the test period (Sep 2025 → Apr 2026), with 4-7× clearance over break-even after theta and IV-crush haircuts.

## Tech

Single-page HTML, vanilla JavaScript, Plotly.js. No backend, no build step, no framework. Hosted on GitHub Pages.

## Files

- `index.html` — dashboard
- `dashboard_data.json` — timeseries (price, regimes, posteriors, entropy)
- `regime_metadata.json` — per-regime statistics

---

*Not investment advice. The model identifies volatility-cycle phases, not directional alpha.*
