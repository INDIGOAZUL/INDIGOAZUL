# 🎯 Bounty Hunter Bot

**Personal automation system for finding and tracking paid GitHub bounties**

---

## 🚀 What is this?

This repo contains my personal Bounty Hunter system that automatically:

✅ Searches GitHub for paid bounties every 6 hours
✅ Alerts me when high-value opportunities ($200+) appear
✅ **AUTO-CLAIMS** bounties with my approval
✅ **SETS UP** workspace automatically (fork, clone, deps)
✅ **DETECTS** commits and PRs, updates tracker automatically
✅ **MONITORS** deadlines and alerts if >7 days inactive
✅ **VERIFIES** payments and reminds me to follow up
✅ Calculates my total earnings and pending payments

**Automation Level:** 70% - Saves ~70 minutes per bounty!

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

### Core Workflows

#### 1. 🎯 Verified Repos Bounty Hunter (NEW!)
**Schedule:** Every 3 hours | **File:** `.github/workflows/verified-repos-hunter.yml`

**RECOMMENDED - Use this for best results!**

Searches ONLY verified repos with official bounty programs:
- ✅ Expensify/App ($50-$10,000+)
- ✅ Ethereum, OpenZeppelin, Uniswap, Aave
- ✅ Node.js, VSCode, React, Next.js
- 🚨 Auto-creates alert issues for bounties $200+
- 📊 Generates `verified-bounty-opportunities.json`

#### 2. 🎯 Bounty Hunter (General)
**Schedule:** Every 6 hours | **File:** `.github/workflows/bounty-hunter.yml`

Searches ALL GitHub for paid bounties (includes unverified repos)
- Uses trust levels: HIGH ✅, MEDIUM ⚠️, LOW ⚡
- Filters out security reports and false positives
- Generates `bounty-opportunities.json`

#### 3. 🔔 Bounty Notifications
**Schedule:** Every 3 hours | **File:** `.github/workflows/bounty-notifications.yml`

Alerts on high-value bounties ($200+) and trending repos

#### 4. 📊 My Bounty Tracker
**Manual only** | **File:** `.github/workflows/my-bounty-tracker.yml`

Tracks: claimed → in_progress → submitted → completed → paid

---

### 🚀 Automated Workflows

#### 5. 🤖 Auto-Claim Assistant
**Manual with approval** | **File:** `.github/workflows/auto-claim-assistant.yml`

- Analyzes bounty (score 0-10)
- Recommends claim if score ≥7, amount ≥$100
- With your approval: Comments on issue, updates tracker

#### 6. 📁 Workspace Setup Bot
**Manual** | **File:** `.github/workflows/workspace-setup-bot.yml`

- Forks repo (optional)
- Clones locally
- Creates branch: `bounty-issue-{num}`
- Installs dependencies
- Updates tracker → "in_progress"

#### 7. 📊 Smart Commit Detector
**Every 12 hours** | **File:** `.github/workflows/smart-commit-detector.yml`

- Detects commits in your forks
- Detects PRs you opened
- Auto-updates tracker:
  - Commits → "in_progress"
  - PR opened → "submitted"
  - PR merged → "completed"

#### 8. ⏰ Deadline Monitor
**Daily 9 AM UTC** | **File:** `.github/workflows/deadline-monitor.yml`

- Checks active bounties
- Alerts if >7 days without activity
- Creates GitHub issue for overdue bounties
- Recommends daily priority

#### 9. 💰 Payment Verifier
**Daily 10 AM UTC** | **File:** `.github/workflows/payment-verifier.yml`

- Checks completed bounties for payment comments
- Alerts if >7 days without payment
- Creates reminder issues
- Confirms payments with your approval

---

## 📖 Full Documentation

### 📚 Main Guides

- **[BOUNTY-HUNTER-GUIDE.md](BOUNTY-HUNTER-GUIDE.md)** - Complete manual usage guide
  - Platform recommendations
  - Best practices for maximizing earnings
  - Daily workflow suggestions
  - Tips and strategies

- **[AUTOMATED-WORKFLOWS-GUIDE.md](AUTOMATED-WORKFLOWS-GUIDE.md)** - Automation guide (NEW!)
  - Complete workflow explanations
  - How workflows collaborate
  - Configuration and customization
  - Troubleshooting

### 🎯 Quick Links

- **Bounty Search:** Check `bounty-opportunities.json`
- **Your Stats:** Check `my-bounty-tracking.json`
- **Actions:** https://github.com/INDIGOAZUL/INDIGOAZUL/actions
- **Issues (Alerts):** https://github.com/INDIGOAZUL/INDIGOAZUL/issues

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
