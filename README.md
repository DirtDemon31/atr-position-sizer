# ATR Position Sizer

> Free, open-source position sizing calculator for traders — works with any asset, runs entirely in your browser.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=flat-square&logo=github)](https://dirtdemon31.github.io/atr-position-sizer/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)
[![No Tracking](https://img.shields.io/badge/No%20Data%20Collected-Privacy%20First-brightgreen?style=flat-square)](https://dirtdemon31.github.io/atr-position-sizer/)

---

![ATR Position Sizer Demo](demo.gif)

---

## What It Does

Instead of guessing lot sizes or using arbitrary percentage stops, this tool calculates your exact position size from **ATR (Average True Range)** — so your stop-loss is always proportional to current market volatility, not a fixed number you made up.

Enter your account balance, risk %, the asset's ATR from your chart, and a multiplier — the sizer outputs your exact:

- **Stop-loss price** anchored to real volatility
- **Take-profit price** at your chosen R:R ratio  
- **Lot size** (units) so one stop-out = exactly your risk amount  
- **Dollar risk** and **leverage used** vs your max limit
- **Daily cap remaining** so you know when to stop

---

## Live Demo

👉 **[dirtdemon31.github.io/atr-position-sizer](https://dirtdemon31.github.io/atr-position-sizer/)**

No installation. No sign-up. Open and use.

---

## Features

| Tab | What's Inside |
|---|---|
| **Position Sizer** | Core calculator — lot size, stop price, TP price, leverage check, pre-trade checklist |
| **Daily Tracker** | Log each trade, track running P&L, live daily-cap progress bar |
| **ATR Guide** | Multiplier selection guide, step-by-step workflow, common mistakes |

### Highlights

- Works with **any asset** — crypto, stocks, forex, commodities, indices — type any ticker
- **Live price fetch** for 50+ crypto tickers via CoinGecko (no API key needed)
- **Pre-trade checklist** auto-validates R:R, leverage limit, daily cap, and inputs
- **Zero dependencies** — one HTML file, no build step, no server
- **No data collected** — everything stays in your browser session

---

## Quick Start

### Use Online
Open the [live demo](https://dirtdemon31.github.io/atr-position-sizer/) in any browser.

### Run Locally
```bash
git clone https://github.com/DirtDemon31/atr-position-sizer.git
cd atr-position-sizer
```

Then open `index.html` in your browser:

| OS | Command |
|---|---|
| Linux | `xdg-open index.html` |
| macOS | `open index.html` |
| Windows | `start index.html` |

Or simply drag `index.html` into an open browser window. The address bar should show `file:///...` — that confirms it's running locally.

---

## Input Reference

| Field | What to Enter | Example |
|---|---|---|
| **Balance ($)** | Your total account equity | `5000` |
| **Max Leverage** | Maximum leverage your broker allows | `5×` |
| **Risk per Trade** | % of account you're willing to lose on one trade | `1%` = $50 on a $5K account |
| **Daily Loss Cap** | Maximum % you'll lose in one session before stopping | `3%` = $150 on $5K |
| **Asset / Ticker** | Any symbol — type freely | `BTC`, `AAPL`, `EUR/USD`, `XAU` |
| **Current Price** | Asset price in USD — enter manually or click ⟳ Live | `84500` |
| **ATR (14)** | ATR(14) value from your daily chart | `2800` for BTC |
| **ATR Multiplier** | How many ATRs your stop sits from entry | `1.5×` standard |
| **Direction** | Long (buy) or Short (sell) | `Long` |
| **Target R:R** | Take-profit distance as a multiple of stop distance | `1.5` = TP is 1.5× the stop |
| **Today's P&L** | Running loss so far today (negative if losing) | `-75.00` |

### Where to Find ATR(14)

Open your daily chart in **TradingView**, **Binance**, or any charting platform and add the **ATR indicator** with period 14. The value shown is in price units — paste it directly into the sizer.

> Example: BTC daily chart shows ATR = **$2,840** → enter `2840`

---

## ATR Multiplier Guide

The multiplier controls how far your stop sits from the entry relative to recent volatility. Wider multiplier = fewer false stop-outs, but larger loss per trade (offset by smaller position size).

| Multiplier | Market Condition | When to Use |
|---|---|---|
| **1.0×** | Very low volatility | Tight ranges, no momentum |
| **1.5×** | Normal trending market | Default for most setups ✓ |
| **2.0×** | Elevated volatility | Post-news, wide daily candles |
| **2.5×** | High volatility | Macro events, strong trends |
| **3.0×** | Extreme volatility | FOMC, CPI, earnings, black swan |

**Rule of thumb:** When in doubt, use 1.5×. If you're getting stopped out frequently on valid setups, increase to 2×. Never widen the multiplier just because you don't want to take a loss — that defeats the purpose.

---

## The Formula

```
Stop Distance  = ATR(14) × Multiplier
Stop Price     = Entry − Stop Distance        ← Long
Stop Price     = Entry + Stop Distance        ← Short

TP Price       = Entry + (Stop Distance × R:R)  ← Long
TP Price       = Entry − (Stop Distance × R:R)  ← Short

Quantity       = Dollar Risk ÷ Stop Distance
Position Size  = Quantity × Entry Price
Leverage Used  = Position Size ÷ Account Balance
Dollar Risk    = Account Balance × Risk %
```

**Example — BTC Long:**
```
Balance:        $5,000
Risk:           1% = $50
Entry:          $84,500
ATR(14):        $2,800
Multiplier:     1.5×
Stop Distance:  $2,800 × 1.5 = $4,200
Stop Price:     $84,500 − $4,200 = $80,300
Quantity:       $50 ÷ $4,200 = 0.0119 BTC
Position Size:  0.0119 × $84,500 = $1,005.55
Leverage Used:  $1,005.55 ÷ $5,000 = 0.20×   (well within 5× limit)
TP (at 1.5R):  $84,500 + $6,300 = $90,800
Max Win:        $50 × 1.5 = $75
```

---

## Why ATR Stops Beat Fixed % Stops

| Fixed % Stop | ATR Stop |
|---|---|
| Same stop every trade regardless of conditions | Stop scales with current volatility |
| Too tight in high-vol → random stop-outs | Fits the market's natural noise range |
| Too wide in low-vol → oversized losses | Position size adjusts to keep risk constant |
| Arbitrary — not anchored to price structure | Can be anchored to swing high/low |

The core insight: **risk stays constant in dollars — only position size changes**. High ATR day = smaller position. Low ATR day = larger position. Your dollar loss per stop-out is always exactly your risk %.

---

## Live Price Support (Crypto)

Click the **⟳ Live** button to fetch the current price from [CoinGecko](https://www.coingecko.com) — no API key required.

<details>
<summary>Supported crypto tickers (click to expand)</summary>

`BTC` `ETH` `SOL` `XRP` `BNB` `ADA` `DOGE` `DOT` `MATIC` `LINK` `LTC` `AVAX` `UNI` `ATOM` `XLM` `ALGO` `TON` `NEAR` `OP` `ARB` `INJ` `SUI` `APT` `SEI` `TIA` `TRUMP` `PEPE` `WIF` `BONK` `SHIB` `FLOKI` `ZEC` `DASH` `XMR` `FIL` `SAND` `MANA` `AAVE` `MKR` `CRV` `LDO` `TAO` `FET` `RENDER` `IMX` `GALA` `FARTCOIN` and more.

</details>

For **stocks, forex, and commodities** (AAPL, EUR/USD, XAU, UKOIL, etc.) — enter the price manually from your broker or TradingView.

---

## Daily Tracker

Use the **Daily Tracker** tab to log trades throughout your session:

1. Enter the asset, P&L, direction, and optional notes
2. Click **Add Trade** — it updates running P&L and daily cap progress bar instantly
3. The cap bar turns **yellow at 80%** and **red when the limit is hit**
4. When the cap is hit, stop trading — the tracker tells you clearly

The daily tracker also syncs with the sizer so your "today's P&L" is always up to date.

---

## Privacy

This tool collects **zero data**. There is no server, no analytics, no cookies, no tracking. The entire app is a single HTML file that runs in your browser. Closing the tab wipes all session data.

---

## Contributing

Pull requests welcome. To run locally for development, just open `index.html` — there's no build step or package manager. Everything is vanilla HTML/CSS/JS.

Areas where contributions would be useful:
- Additional CoinGecko ticker mappings
- TradingView-style chart integration
- Dark/light theme toggle
- Export session log as CSV

---

## License

[MIT](LICENSE) — free to use, modify, fork, and distribute.

---

*Built with vanilla HTML/CSS/JS. Prices via [CoinGecko API](https://www.coingecko.com/en/api). No affiliation with any broker or trading platform.*
