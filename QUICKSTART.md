# Quick Start Guide for Western Users

Welcome! This guide will help you quickly set up TrendRadar to monitor Western news sources.

> **📖 New: Complete Setup Guide Available!**  
> For a comprehensive guide with Discord webhook, GitHub Pages, and detailed explanations of all default sources, see **[SETUP.md](SETUP.md)**

## 🚀 30-Second Setup

### 1. Fork & Configure

1. **Fork** this repository to your GitHub account
2. **Add notification channel** (choose one):
   - Discord (recommended - simple setup, see [SETUP.md](SETUP.md#discord-webhook-setup))
   - Telegram (good for mobile)
   - Email
   - Any other supported channel

### 2. Set Up Secrets

Go to your forked repo: `Settings` > `Secrets and variables` > `Actions` > `New repository secret`

**For Discord:**
- Name: `DISCORD_WEBHOOK_URL` → Value: Your Discord webhook URL
- See [SETUP.md](SETUP.md#discord-webhook-setup) for detailed instructions

**For Telegram:**
- Name: `TELEGRAM_BOT_TOKEN` → Value: Your bot token
- Name: `TELEGRAM_CHAT_ID` → Value: Your chat ID

See [README-EN.md](README-EN.md) for other channels.

### 3. Configure Keywords

Edit `config/frequency_words.txt`:

```txt
# Replace Chinese keywords with English ones

# Technology
AI
ChatGPT
Machine Learning
Tesla
SpaceX

# Business
Startup
Funding
IPO

# Your interests
Climate Change
Space Exploration
```

### 4. Add Western Platforms

Edit `config/config.yaml`:

```yaml
platforms:
  # Comment out or remove Chinese platforms you don't need
  # - id: "zhihu"
  #   name: "Zhihu (知乎)"
  
  # Add Western platforms (check availability at https://newsnow.busiyi.world/)
  - id: "hackernews"
    name: "Hacker News"
  - id: "reddit-popular"  
    name: "Reddit Popular"
  - id: "producthunt"
    name: "Product Hunt"
```

### 5. Test Run

Go to `Actions` tab → `Hot News Crawler` → `Run workflow`

Check your notification channel in ~1 minute!

## 📝 Example Configurations

### For Tech Enthusiasts

**Keywords (config/frequency_words.txt):**
```txt
AI
Artificial Intelligence
ChatGPT
Claude
!advertisement

Startup
Y Combinator  
Venture Capital
+funding

Tesla
SpaceX
Elon Musk

GitHub
Open Source
+release
```

**Platforms (config/config.yaml):**
```yaml
platforms:
  - id: "hackernews"
    name: "Hacker News"
  - id: "reddit-programming"
    name: "Reddit Programming"
  - id: "producthunt"
    name: "Product Hunt"
  - id: "github-trending"
    name: "GitHub Trending"
```

### For Business & Finance

**Keywords:**
```txt
Stock Market
Dow Jones
S&P 500

Cryptocurrency
Bitcoin
Ethereum
!scam

Startup
IPO
Merger
+acquisition

Economy
Federal Reserve
Interest Rate
```

**Platforms:**
```yaml
platforms:
  - id: "bloomberg"
    name: "Bloomberg"
  - id: "wsj"
    name: "Wall Street Journal"
  - id: "reuters"
    name: "Reuters"
```

*(Note: Check platform availability at https://newsnow.busiyi.world/)*

## 🎯 Keyword Syntax

- **Normal word**: `Tesla` - Matches any occurrence
- **Required word**: `+launch` - Must appear with other keywords
- **Filter word**: `!advertisement` - Excludes matches
- **Empty line**: Separates keyword groups

**Example:**
```txt
Tesla
SpaceX
+launch
!rumor

This creates one group that matches:
✅ "Tesla launch event announced" (has Tesla + launch)
✅ "SpaceX launch successful" (has SpaceX + launch)
❌ "Tesla stock rises" (missing "launch")
❌ "Tesla launch rumor debunked" (has "rumor")
```

## ⚙️ Push Modes

Edit `config/config.yaml`:

```yaml
report:
  mode: "incremental"  # Options: "daily", "current", "incremental"
```

- **incremental**: Only new news (recommended for frequent updates)
- **current**: Latest rankings
- **daily**: All news of the day

## 🔧 Troubleshooting

### No notifications received?

1. Check `Actions` tab for errors
2. Verify secrets are set correctly (no typos)
3. Ensure `config/frequency_words.txt` has keywords
4. Try manual test: `Actions` → `Run workflow`

### Want to monitor both Chinese and Western sources?

Keep all platforms in `config/config.yaml`:
```yaml
platforms:
  # Chinese platforms
  - id: "zhihu"
    name: "Zhihu (知乎)"
  - id: "weibo"
    name: "Weibo (微博)"
  
  # Western platforms  
  - id: "hackernews"
    name: "Hacker News"
  - id: "reddit-popular"
    name: "Reddit Popular"
```

Add both English and Chinese keywords:
```txt
# English keywords
AI
Tesla

# Chinese keywords (if you read Chinese)
人工智能
特斯拉
```

## 📚 More Information

- **Full Setup Guide**: See [README-EN.md](README-EN.md)
- **Adding Platforms**: See [CONTRIBUTING.md](CONTRIBUTING.md)
- **Available Platforms**: https://newsnow.busiyi.world/
- **Platform Sources**: https://github.com/ourongxing/newsnow/tree/main/server/sources

## 💡 Tips

1. **Start Small**: Test with 2-3 keywords first
2. **Use Filters**: Exclude noise with `!spam`, `!advertisement`
3. **Schedule Smart**: Default runs hourly (check cron in `.github/workflows/crawler.yml`)
4. **Check Costs**: GitHub Actions has free tier limits

## 🎉 You're All Set!

Your personalized Western news aggregator is ready. The crawler will run automatically on schedule and notify you of trending topics you care about.

**Need Help?** [Open an issue](https://github.com/SomethingGeneric/TrendRadar/issues)

---

*Note: This project uses the [newsnow](https://github.com/ourongxing/newsnow) API. Please respect their service and don't set intervals shorter than 30 minutes.*
