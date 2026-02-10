# X Alpha Scout

Turn your AI agent into an alpha-hunting machine. This skill enables agents to scan X/Twitter for crypto calls, track caller accuracy, and deliver daily intelligence reports.

## What It Does

- **Scans X 2-3x daily** for token calls, NFT mints, and new launches
- **Parses conviction signals** (position sizes, "all in", wallet proofs)
- **Tracks caller accuracy** and builds win-rate leaderboards
- **Generates structured reports** with priority rankings
- **Identifies red flags** (shill accounts, bot patterns)

## Perfect For

- Agents that need daily market intelligence
- Traders who want to track which X accounts are actually good
- NFT hunters looking for mint announcements
- Building your own alpha database

## Installation

1. **Install [bird](https://github.com/steipete/bird)** — X/Twitter CLI tool
2. **Get X credentials:**
   - Auth token (`X_AUTH_TOKEN`)
   - CT0 cookie (`X_CT0`)
3. **Verify access:**
   ```bash
   bird whoami --auth-token "$X_AUTH_TOKEN" --ct0 "$X_CT0"
   ```

## Usage

Tell your agent: _"Run my daily alpha scan"_ or _"Check X for new mints"_

The skill includes pre-built queries for:
- Token calls and shills
- NFT mint announcements
- Stealth launches
- High-conviction gems

## Example Output

```markdown
# Alpha Scout Report — 2026-02-10

## 🔥 High Priority Calls
| Caller | Asset | Type | Entry | Conviction |
|--------|-------|------|-------|------------|
| @DegenKing | $PEPEAI | token | $0.002 | HIGH |

## 📊 Leaderboard Update (7-day win rate)
1. @AlphaKing — 80% win rate
2. @CryptoGem — 67% win rate
```

## How It Works

The skill uses [bird](https://github.com/steipete/bird) to search X without needing API keys. Your agent brings its own credentials, you bring the intelligence.

No Twitter API costs. No rate limits. Just raw alpha.

## Roadmap

- [x] Core scanning workflows
- [ ] Automated win-rate tracking
- [ ] Price feed integration
- [ ] Discord/Telegram alerts
- [ ] Premium dashboard (if there's demand)

## License

MIT — Use it, fork it, build on it.

---

Built for the agent economy. 🦅
