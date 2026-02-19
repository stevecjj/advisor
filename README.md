# TSLA Covered Call Strategy Advisor

A live, web-based tool that auto-fetches TSLA market data and calculates the optimal covered call strike price using an IV-adaptive strategy.

## 🚀 Deploy to GitHub Pages (5 minutes)

### Step 1: Create a GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Name it: `tsla-advisor` (or anything you like)
3. Set to **Public** (required for free GitHub Pages)
4. Click **Create repository**

### Step 2: Upload the Files

**Option A — Upload via browser (easiest):**
1. On your new repo page, click **"uploading an existing file"**
2. Drag and drop the `index.html` file
3. Click **Commit changes**

**Option B — Git command line:**
```bash
cd tsla-advisor
git init
git add .
git commit -m "TSLA covered call advisor"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/tsla-advisor.git
git push -u origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages** (left sidebar)
2. Under "Source", select **Deploy from a branch**
3. Branch: **main** / Folder: **/ (root)**
4. Click **Save**
5. Wait 1-2 minutes

### Step 4: Access Your Site

Your advisor is now live at:
```
https://YOUR_USERNAME.github.io/tsla-advisor/
```

Bookmark this URL — it works on any device (phone, tablet, laptop).

---

## 🔑 First-Time Setup

When you first open the page:

1. **Enter your Anthropic API key** in the key field at the top
   - Get one at [console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys)
   - The key is stored only in your browser's localStorage — never sent anywhere except Anthropic's API
   - You need a plan that includes web search (most paid plans do)

2. That's it. Click **"Fetch Live Data & Calculate Strike"** and you're trading.

---

## 📖 How It Works

Every other Friday:

1. **Open the page** → Click the green "Fetch" button
2. The tool calls Claude with web search to find:
   - Current TSLA price
   - 30-day implied volatility
   - 50-day SMA
   - Price from 2 weeks ago
   - Upcoming earnings dates
3. **The strategy engine calculates your strike** based on:
   - IV Regime (LOW/MID/HIGH/EXTREME → different OTM distances)
   - Momentum adjustment (recent rally or decline)
   - Trend adjustment (price vs. 50D SMA)
   - Earnings adjustment (extra buffer near earnings)
4. **Execute in your broker** at the recommended strike
5. Trade is auto-logged in the history table

### Manual Mode

If the API fetch fails, switch to "Manual Input" mode and enter the 5 values yourself from:
- **Price**: Your broker or Yahoo Finance
- **IV**: barchart.com → TSLA → Volatility
- **SMA**: TradingView chart
- **2W ago price**: Yahoo Finance historical
- **Earnings**: TSLA earnings calendar

---

## 📊 Strategy Summary

| IV Regime | IV Range | Base OTM | Position Size |
|-----------|----------|----------|---------------|
| LOW       | < 35%    | 4%       | 100%          |
| MID       | 35-55%   | 6%       | 85%           |
| HIGH      | 55-75%   | 10%      | 60%           |
| EXTREME   | > 75%    | 15%      | 35% or SKIP   |

**Backtest results (Jan 2023 – Feb 2026):**
- 76 trades, 15.8% assignment rate
- $16,095 total premium on ~$19,700 capital
- 26.3% annualized premium yield

---

## ⚠️ Disclaimer

This is a strategy modeling tool, not investment advice. Options trading involves significant risk. Past simulated performance does not guarantee future results. Always do your own research.
