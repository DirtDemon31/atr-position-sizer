# ATR Position Sizer

A free, open-source, browser-based position sizing tool for traders. Works with **any asset** — crypto, stocks, forex, commodities, indices.

**No data is collected. No sign-up. Runs entirely in your browser.**

---

## Live Demo

👉 [dirtdemon31.github.io/atr-position-sizer](https://dirtdemon31.github.io/atr-position-sizer/)

---

## Features

| Feature | Details |
|---|---|
| **ATR-based stop-loss** | Calculates stop price from ATR(14) × multiplier anchored to structure |
| **Position sizing** | Exact lot size and position size in $ from your dollar risk amount |
| **Take-profit calculator** | Target price at your chosen R:R ratio |
| **Daily loss tracker** | Logs trades, tracks running P&L, and shows remaining daily cap |
| **Live price fetch** | Pulls real-time crypto prices from CoinGecko (no API key required) |
| **Any asset** | Works for crypto, stocks, forex, commodities — type any ticker |
| **Pre-trade checklist** | Auto-validates R:R, leverage, daily cap, and price/ATR inputs |
| **ATR guide** | Built-in reference for multiplier selection and stop-loss workflow |

---

## How to Use

### Online
Open the live demo link above — no installation needed.

### Locally
```bash
git clone https://github.com/DirtDemon31/atr-position-sizer.git
cd atr-position-sizer
# Then open index.html in your browser:
xdg-open index.html      # Linux
open index.html           # macOS
start index.html          # Windows
```

Or drag `index.html` directly into your browser window.

---

## Sizer Workflow

1. **Set your account balance and risk %** (e.g. 1% of $5,000 = $50 risk per trade)
2. **Enter your asset** (e.g. BTC, SOL, AAPL, EUR/USD)
3. **Fetch or enter the current price**
4. **Enter ATR(14)** from your daily chart (TradingView, Binance, etc.)
5. **Choose ATR multiplier** (1.5× standard, 2× high-vol, 3× extreme)
6. **Set your target R:R** (minimum 1.5 recommended)
7. **Hit Calculate** — get exact stop price, take-profit price, lot size, and dollar risk

### ATR Multiplier Guide

| Multiplier | When to Use |
|---|---|
| 1.0–1.5× | Low volatility, ranging/choppy market |
| 1.5–2.0× | Normal trending market (default) |
| 2.0–2.5× | High volatility, post-news, wide-range days |
| 2.5–3.0× | Extreme events (FOMC, CPI, earnings) |

---

## Live Price Support

The **⟳ Live** button fetches real-time prices from [CoinGecko](https://www.coingecko.com) for 50+ crypto tickers with no API key. For stocks, forex, and commodities, enter the price manually from your broker or TradingView.

Supported tickers include: BTC, ETH, SOL, XRP, BNB, ADA, DOGE, DOT, MATIC, LINK, LTC, AVAX, UNI, ATOM, TON, NEAR, OP, ARB, SUI, APT, PEPE, WIF, SHIB, FLOKI, ZEC, DASH, XMR, and many more.

---

## Formula

```
Stop Distance  = ATR(14) × Multiplier
Stop Price     = Entry ± Stop Distance  (− for long, + for short)
TP Price       = Entry ± (Stop Distance × R:R)
Position Size  = Dollar Risk ÷ Stop Distance  (in units)
Position Value = Position Size × Entry Price
Leverage Used  = Position Value ÷ Account Balance
```

---

## No Data Collected

This tool runs 100% in your browser. No analytics, no tracking, no server. Your trade data exists only in your browser session and is cleared when you close the tab.

---

## License

MIT — free to use, modify, and distribute.
