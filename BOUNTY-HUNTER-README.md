# 🎯 Bounty Hunter Bot

**Personal automation system for finding and tracking paid GitHub bounties**

---

## 🚀 What is this?

This repo contains my personal Bounty Hunter system that automatically:

✅ Searches GitHub for paid bounties every 6 hours
✅ Alerts me when high-value opportunities ($200+) appear
✅ Tracks my progress on claimed bounties
✅ Calculates my total earnings and pending payments

---

## 📊 Current Stats

Check `my-bounty-tracking.json` for real-time stats:

```bash
# View stats
cat my-bounty-tracking.json | jq '.stats'

# View opportunities
cat bounty-opportunities.json | jq '.bounties[:10]'
```

---

## 🤖 Workflows

### 1. 🎯 Bounty Hunter
**Schedule:** Every 6 hours
**File:** `.github/workflows/bounty-hunter.yml`

Searches GitHub for:
- Issues labeled `bounty`
- Mentions of `$`, `USD`, `gitcoin`
- Specific tech stack: JavaScript, Web3, React, Node.js, Solidity

Generates: `bounty-opportunities.json` with top 50 opportunities

### 2. 🔔 Bounty Notifications
**Schedule:** Every 3 hours
**File:** `.github/workflows/bounty-notifications.yml`

Alerts on:
- High-value bounties ($200+)
- Trending Web3/blockchain repos with bounties

### 3. 📊 My Bounty Tracker
**Manual trigger only**
**File:** `.github/workflows/my-bounty-tracker.yml`

Tracks bounty progress:
- claimed → in_progress → submitted → completed → paid

Generates: `my-bounty-tracking.json` with full history

---

## 📖 Full Documentation

See [BOUNTY-HUNTER-GUIDE.md](BOUNTY-HUNTER-GUIDE.md) for:
- Complete usage instructions
- Best practices for maximizing earnings
- Platform recommendations
- Daily workflow suggestions

---

## 🎯 Quick Start

### Run Manual Search

```bash
# Go to: https://github.com/INDIGOAZUL/INDIGOAZUL/actions
# Select: Bounty Hunter
# Click: Run workflow
```

### Track a Bounty

```bash
# Go to: https://github.com/INDIGOAZUL/INDIGOAZUL/actions
# Select: My Bounty Progress Tracker
# Click: Run workflow
# Fill in:
#   - bounty_url: https://github.com/owner/repo/issues/123
#   - amount: 500
#   - status: claimed
```

### View Results

```bash
# Clone this repo
git clone https://github.com/INDIGOAZUL/INDIGOAZUL.git

# View found bounties
cat bounty-opportunities.json

# View your stats
cat my-bounty-tracking.json
```

---

## 💰 Bounty Platforms

The system searches:
- GitHub issues with `bounty` labels
- Gitcoin bounties
- IssueHunt opportunities

Also check manually:
- [Gitcoin](https://gitcoin.co/explorer) - $100-$5,000
- [HackerOne](https://www.hackerone.com/opportunities) - $100-$10,000+
- [Layer3](https://layer3.xyz/quests) - $50-$1,000
- [Replit Bounties](https://replit.com/bounties) - $100-$2,000

---

## 📈 My Goals

| Period | Bounties | Avg. Amount | Target Earnings |
|--------|----------|-------------|-----------------|
| **Weekly** | 1-2 | $150 | $150-$300 |
| **Monthly** | 4-8 | $250 | $1,000-$2,000 |
| **Quarterly** | 12-24 | $300 | $3,600-$7,200 |

---

## 🔒 Privacy

This repo is:
- [x] Public - Workflows visible (for transparency)
- [ ] Private - Only I can see earnings

Note: `my-bounty-tracking.json` contains my personal earnings data.

---

## 🤝 About Me

I'm **Narjell Ebanks** (@INDIGOAZUL), a Full-Stack Developer from Roatan, Honduras 🇭🇳

**Tech Stack:**
- JavaScript/Node.js ⭐⭐⭐⭐⭐
- React/Frontend ⭐⭐⭐⭐
- Web3/Solidity ⭐⭐⭐⭐
- PostgreSQL/Backend ⭐⭐⭐⭐⭐

**Looking for bounties in:**
- DeFi/Web3 projects
- Authentication/security features
- Payment integrations
- API development
- Smart contracts

---

## 📞 Contact

Found a great bounty for me? Let's collaborate!

- 📧 Email: ebanksnigel@gmail.com
- 💼 GitHub: [@INDIGOAZUL](https://github.com/INDIGOAZUL)
- 🌐 Website: [latanda.online](https://latanda.online)

---

**Happy Bounty Hunting! 🎯💰**
