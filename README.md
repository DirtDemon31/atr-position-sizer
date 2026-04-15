# ATR Position Sizer — Upscale 5K

A real-time, browser-based ATR position sizing tool built for prop trading on the Upscale 5K challenge account.

## Features

- **ATR-based position sizer** — calculates lot size, stop-loss price, take-profit, and dollar risk from ATR(14) × multiplier
- **Live price fetching** — pulls real-time prices from CoinGecko for BTC, SOL, ETH, TON, XRP, XAU and more
- **Daily loss tracker** — tracks remaining daily cap in real time, color-coded progress bar
- **Trade journal** — full Upscale (14 trades) and Storm Trade (215 trades) history with sort/filter
- **Analytics** — equity curves, P&L by symbol, win rate by day of week, return % distribution
- **ATR guide** — how to use ATR stops, typical values per instrument, time-based exit rules
- **Pre-trade checklist** — R:R, daily cap, leverage, ATR, live price, session window

## Usage

Open `index.html` directly in any browser, or use via GitHub Pages.

## Account Defaults

| Setting | Value |
|---|---|
| Account | $5,000 |
| Max Leverage | 5× |
| Risk per Trade | 0.5–1% |
| Daily Loss Cap | 3% ($150) |
| Instruments | BTC, SOL, ETH, TON, XRP, XAU, UKOIL |

## Live on GitHub Pages

[Open the Position Sizer](https://stephanjrioux.github.io/atr-position-sizer/)

---
Built from real Upscale + Storm Trade journal data (Oct 2024 – Apr 2026).
