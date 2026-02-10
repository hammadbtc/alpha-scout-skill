---
name: x-alpha-scout
description: X/Twitter alpha scanner for crypto and NFTs. Use when: (1) user wants daily alpha reports, (2) analyzing a specific token/NFT/project from X sentiment. GitHub: github.com/hammad-btc/x-alpha-scout
---

# X Alpha Scout

Your agent's X/Twitter alpha scanner. Two things: daily reports and on-demand analysis.

## Prerequisites

**Environment variables:**
```bash
export X_AUTH_TOKEN="your_twitter_auth_token"
export X_CT0="your_twitter_ct0_cookie"
```

**Verify:**
```bash
bird whoami --auth-token "$X_AUTH_TOKEN" --ct0 "$X_CT0"
```

---

## Feature 1: Daily Alpha Report (Auto at 00:00 UTC)

**User says:** "Run my daily alpha" or "Get today's report"

**What you do:**

```bash
# Scan for overnight alpha
bird search "(buying OR bought OR aping OR loading up) (ticker OR token OR \$)" --since 24h -n 25
bird search "(minting OR mint OR free mint) NFT" --since 24h -n 20
bird search "(just launched OR stealth launch) token" --since 12h -n 15
bird search "(gem OR undervalued OR 100x) crypto" --min-likes 10 --since 24h -n 15
```

**Generate report:**

```markdown
# 🦅 Alpha Scout Report — 2026-02-10

## 🔥 Top Calls (Last 24h)
| Asset | Type | Key Callers | Conviction |
|-------|------|-------------|------------|
| $PEPEAI | token | @DegenKing, @AlphaKing | HIGH |
| FomoBears | NFT | @NFTWhale | MEDIUM |

## 🆕 New Launches
- $MOONSHOT — stealth launch, 50K MC
- PixelPunks — free mint, 5K supply

## 📊 CT Sentiment Snapshot
- Bullish tickers: $PEPEAI, $SOLANA, $BONK
- Bearish warnings: $RUGCOIN (multiple red flags)

---
*Next report: 00:00 UTC*
```

**Deliver:** Send to user via their preferred channel (Discord, Telegram, etc.)

---

## Feature 2: On-Demand Analysis

**User says:** "What do you think of $PEPEAI?" or "Analyze FomoBears NFT"

**What you do:**

```bash
# Deep scan this specific asset
bird search "$PEPEAI" --since 48h -n 30
bird search "$PEPEAI (gem OR scam OR rug OR buy)" --since 48h -n 20
```

**Analyze gathered tweets:**

1. **Count sentiment:** Bullish vs Bearish vs Neutral
2. **Identify high-conviction posts:** Position sizes, wallet proofs, detailed threads
3. **Check high-rep accounts:** Are known good callers in or out?
4. **Look for red flags:** Contract issues, copycat names, anon team

**Deliver analysis in this exact format:**

```
📊 CT Sentiments:
[4-5 line summary based on top 20-30 recent tweets about the asset. What are people saying? Any patterns? Hype or concern? Specific details about the project/token/NFT]

📈 Overall: [Bullish/Bearish/Neutral]

🐋 Takes of High-Rep Accounts:
[@Influencer1: "quote or summary of their take" — Bullish]
[@Influencer2: "quote or summary of their take" — Bearish]
[Or: No noticeable activity detected from high-rep accounts — Neutral]

⚠️ Red Flags:
[Any contract issues, anon team, copycat name, LP not locked, etc. Or: None detected]

📊 Score: XX/100

✅ Verdict: [High/Medium/Low confidence — Bullish/Neutral/Bearish]

⚡ NFA / DYOR
```

**How to gather data:**

```bash
# Get general sentiment tweets
bird search "$TICKER" --since 48h -n 30

# Get high-rep account takes specifically
bird search "$TICKER (from:DegenKing OR from:AlphaKing OR from:CryptoGem)" --since 48h -n 20
# Add more KOLs as needed
```

**Scoring guide:**
- **90-100:** Strong bullish consensus, high-reps bullish, no red flags
- **70-89:** Moderate bullish, some high-reps in, minor concerns
- **50-69:** Mixed/neutral, no clear direction or high-reps silent
- **30-49:** Bearish signals, some red flags or high-reps warning
- **0-29:** Strong bearish, multiple red flags, avoid

---

## Signal Scoring Guide

**CT Sentiment Score (0-100):**
- **80-100:** Strong bullish consensus, high-rep accounts in, no red flags
- **50-79:** Mixed or moderate sentiment, do more research
- **<50:** Bearish consensus or multiple red flags detected

**What to look for:**
- **Bullish:** "gem", "undervalued", "loading up", "next 100x"
- **Bearish:** "rug", "scam", "avoid", "dumping"
- **High-conviction:** Specific numbers ("bought $5k"), wallet screenshots, detailed threads
- **Red flags:** Contract unverified, LP not locked, copycat name, team completely anon

---

## Quick Commands

| Task | Command |
|------|---------|
| Daily report | Run scans for last 24h, compile top calls |
| Analyze asset | `bird search "$TICKER" --since 48h -n 30` |
| Check specific caller | `bird search "from:username" --since 7d -n 20` |
| Find mints | `bird search "free mint OR minting now NFT" --since 12h` |

---

## Example Sessions

**User:** "Get my alpha report"

**You:** Run the 4 daily scans → compile top calls → format report → deliver

---

**User:** "What about $MOONSHOT?"

**You:** Search "$MOONSHOT" (48h, 30 tweets) → analyze sentiment → check for red flags → deliver analysis with score + verdict + NFA

---

**User:** "Is @DegenKing reliable?"

**You:** Search "from:DegenKing" (7 days) → review their recent calls → give qualitative assessment: "Known for high-conviction calls, recent streak looks solid" or "Mixed bag lately, verify before following"

---

*Built for the agent economy. NFA. DYOR.* 🦅
