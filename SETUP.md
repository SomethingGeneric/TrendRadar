# TrendRadar Setup Guide

Complete setup guide for deploying TrendRadar with Discord webhook and GitHub Pages.

## Table of Contents

- [Quick Start](#quick-start)
- [Discord Webhook Setup](#discord-webhook-setup)
- [GitHub Pages Setup](#github-pages-setup)
- [Default News Sources](#default-news-sources)
- [Adding Western Sources](#adding-western-sources)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)

---

## Quick Start

TrendRadar monitors trending news from multiple platforms and sends notifications to your preferred channels. This guide will help you set up Discord notifications and a web-based dashboard using GitHub Pages.

**Time Required**: 5-10 minutes

**What You'll Get**:
- 📱 Discord notifications for trending news
- 🌐 A beautiful web dashboard hosted on GitHub Pages
- 📊 Customizable keyword filtering
- 🔄 Automatic updates every 30 minutes (configurable)

---

## Discord Webhook Setup

Discord webhooks allow TrendRadar to send trending news directly to your Discord server.

### Step 1: Create a Discord Webhook

1. **Open Discord** and navigate to the server where you want to receive notifications
2. **Right-click on a text channel** → Select **"Edit Channel"**
3. **Click "Integrations"** in the left sidebar
4. **Click "Create Webhook"** (or "View Webhooks" if you have existing webhooks)
5. **Click "New Webhook"** button
6. **Configure the webhook**:
   - **Name**: `TrendRadar` (or any name you prefer)
   - **Channel**: Select the channel where notifications should appear
   - **Icon**: Optional - you can upload a custom icon
7. **Click "Copy Webhook URL"** - this is your Discord webhook URL
8. **Click "Save"**

Your webhook URL will look like:
```
https://discord.com/api/webhooks/123456789012345678/abcdefghijklmnopqrstuvwxyz1234567890
```

### Step 2: Add Webhook to GitHub Secrets

1. **Go to your forked repository** on GitHub
2. **Click "Settings"** tab
3. **Click "Secrets and variables"** → **"Actions"** in the left sidebar
4. **Click "New repository secret"**
5. **Add the webhook**:
   - **Name**: `DISCORD_WEBHOOK_URL` (must be exactly this)
   - **Secret**: Paste your Discord webhook URL
6. **Click "Add secret"**

### Step 3: Test Your Setup

1. **Go to the "Actions" tab** in your repository
2. **Click "Hot News Crawler"** in the left sidebar
3. **Click "Run workflow"** button on the right
4. **Click the green "Run workflow"** button
5. **Wait about 1 minute** - you should see a message in your Discord channel!

**Example Discord Notification**:
```
📊 Trending Keywords Stats

🔥 [1/3] AI ChatGPT : 2 items

  1. [Baidu Hot] 🆕 ChatGPT-5 officially launched [**1**] - 09:15 (1 time)
  2. [Toutiao] AI chip concept stocks surge [**3**] - [08:30 ~ 10:45] (3 times)

Updated: 2025-01-15 12:30:15
```

---

## GitHub Pages Setup

GitHub Pages provides a free web dashboard to view your trending news in a beautiful format.

### Step 1: Enable GitHub Pages

1. **Go to your forked repository** on GitHub
2. **Click "Settings"** tab
3. **Click "Pages"** in the left sidebar
4. **Under "Source"**, select:
   - **Source**: Deploy from a branch
   - **Branch**: `master` (or `main`)
   - **Folder**: `/ (root)`
5. **Click "Save"**

### Step 2: Wait for Deployment

1. GitHub will automatically build and deploy your site
2. After a few minutes, you'll see a message:
   ```
   Your site is live at https://yourusername.github.io/TrendRadar/
   ```
3. **Click the URL** to view your dashboard

### Step 3: Configure GitHub Pages URL (Optional)

If you want to use a custom domain:

1. **Add a CNAME file** to your repository root with your domain name
2. **Configure DNS** at your domain provider to point to GitHub Pages
3. See [GitHub's custom domain documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

### Features of the Web Dashboard

- **Mobile-Responsive**: Works perfectly on phones and tablets
- **Save as Image**: Click the "Save as Image" button to download reports
- **Real-Time Updates**: Automatically refreshes when new data is pushed
- **Beautiful Design**: Clean, modern interface with trend indicators

**Preview**: See a live example at [https://sansan0.github.io/TrendRadar/](https://sansan0.github.io/TrendRadar/)

---

## Default News Sources

TrendRadar comes pre-configured with 11 major Chinese news platforms. Here's what each platform covers:

### Default Platforms (Chinese)

| Platform | ID | Description | Content Type |
|----------|-------|-------------|--------------|
| **Zhihu (知乎)** | `zhihu` | Chinese Q&A platform, intellectual discussions | Tech, Science, Culture |
| **Weibo (微博)** | `weibo` | Chinese Twitter, celebrity and social news | Entertainment, Social, Breaking News |
| **Douyin (抖音)** | `douyin` | Chinese TikTok, viral video trends | Viral Content, Entertainment |
| **Bilibili** | `bilibili-hot-search` | Video platform, gaming and anime trends | Gaming, Anime, Youth Culture |
| **Baidu (百度)** | `baidu` | China's largest search engine trends | General News, Search Trends |
| **Toutiao (今日头条)** | `toutiao` | News aggregator, personalized content | General News, Local Stories |
| **Tieba (贴吧)** | `tieba` | Forum community, niche interests | Community Discussions |
| **Wallstreetcn (华尔街见闻)** | `wallstreetcn-hot` | Financial news platform | Finance, Economics, Markets |
| **Yicai (财联社)** | `cls-hot` | Financial and business news | Business, Finance |
| **Thepaper (澎湃新闻)** | `thepaper` | News media, investigative journalism | Politics, Society, Investigation |
| **iFeng (凤凰网)** | `ifeng` | News portal, current affairs | Current Affairs, Politics |

### Why These Platforms?

These 11 platforms represent the most popular news sources in China, covering:
- **Social Media**: Weibo, Douyin
- **Knowledge Sharing**: Zhihu
- **Video Content**: Bilibili
- **Search Trends**: Baidu
- **News Aggregation**: Toutiao, iFeng, Thepaper
- **Finance**: Wallstreetcn, Yicai
- **Community**: Tieba

**Total Daily Reach**: Over 1 billion Chinese internet users rely on these platforms for news.

---

## Adding Western Sources

While TrendRadar defaults to Chinese platforms, you can add Western news sources like HackerNews, Reddit, Product Hunt, and more.

### Available Western Sources

The following Western sources are available through the NewsNow API:

| Source | ID | Description |
|--------|-----|-------------|
| **Hacker News** | `hackernews` | Tech news and startup discussions |
| **Reddit Popular** | `reddit-popular` | Trending posts from Reddit |
| **Product Hunt** | `producthunt` | New tech products and launches |
| **GitHub Trending** | `github-trending` | Trending repositories |

**Note**: For a complete list of available sources, visit:
- [NewsNow Website](https://newsnow.busiyi.world/) - Click "More" to see all platforms
- [NewsNow GitHub](https://github.com/ourongxing/newsnow/tree/main/server/sources) - Source code for all integrations

### Step 1: Edit Platform Configuration

1. **Open** `config/config.yaml` in your repository
2. **Find the `platforms:` section** (around line 87)
3. **Add your desired platforms**:

```yaml
platforms:
  # Keep Chinese platforms if you want them
  - id: "toutiao"
    name: "Toutiao (今日头条)"
  - id: "baidu"
    name: "Baidu Hot Search (百度热搜)"
  - id: "wallstreetcn-hot"
    name: "Wallstreetcn (华尔街见闻)"
  - id: "thepaper"
    name: "The Paper (澎湃新闻)"
  - id: "bilibili-hot-search"
    name: "Bilibili Hot Search"
  - id: "cls-hot"
    name: "CLS Hot (财联社热门)"
  - id: "ifeng"
    name: "iFeng (凤凰网)"
  - id: "tieba"
    name: "Tieba (贴吧)"
  - id: "weibo"
    name: "Weibo (微博)"
  - id: "douyin"
    name: "Douyin (抖音)"
  - id: "zhihu"
    name: "Zhihu (知乎)"
  
  # Add Western platforms
  - id: "hackernews"
    name: "Hacker News"
  - id: "reddit-popular"
    name: "Reddit Popular"
  - id: "producthunt"
    name: "Product Hunt"
  - id: "github-trending"
    name: "GitHub Trending"
```

### Step 2: Configure English Keywords

Edit `config/frequency_words.txt` to add English keywords:

```txt
# Technology
AI
ChatGPT
Artificial Intelligence
Machine Learning
!advertisement

# Companies
Tesla
SpaceX
Apple
Google
Microsoft
OpenAI

# Topics
Climate Change
Space Exploration
Cryptocurrency
+Bitcoin
!scam

# Startups
Startup
Y Combinator
Venture Capital
+funding
```

### Step 3: Enable Translation (Optional)

If you want to translate Chinese headlines to English:

1. **Edit** `config/config.yaml`
2. **Find the `translation:` section** (around line 33)
3. **Enable translation**:

```yaml
translation:
  enabled: true              # Set to true
  show_original: false       # Set to false for English only
  cache_translations: true   # Keep as true
```

### Step 4: Test Your Configuration

1. **Commit your changes** to GitHub
2. **Go to Actions** → **"Hot News Crawler"** → **"Run workflow"**
3. **Check Discord** for notifications with your new sources

---

## Configuration

### Push Modes

TrendRadar offers three push modes to control when and how you receive notifications:

#### 1. Daily Summary Mode (`daily`)
```yaml
report:
  mode: "daily"
```
- **When**: Scheduled push (default: hourly)
- **What**: All matched news of the day + new news section
- **Best For**: Daily report summaries, comprehensive overview

#### 2. Current Rankings Mode (`current`)
```yaml
report:
  mode: "current"
```
- **When**: Scheduled push (default: hourly)
- **What**: Current ranking matched news + new news section
- **Best For**: Real-time trend tracking, what's hot right now

#### 3. Incremental Monitor Mode (`incremental`)
```yaml
report:
  mode: "incremental"
```
- **When**: Push only when new content appears
- **What**: Only newly appeared news
- **Best For**: Avoiding duplicate notifications, high-frequency monitoring

### Keyword Configuration

Edit `config/frequency_words.txt` to define what news you want to track:

#### Syntax

- **Normal words**: Match any occurrence
  ```txt
  Tesla
  AI
  ```

- **Required words** (`+`): Must appear together with other keywords
  ```txt
  Tesla
  SpaceX
  +launch
  ```
  *Matches: "Tesla launch event" but not "Tesla stock price"*

- **Filter words** (`!`): Exclude news containing these
  ```txt
  AI
  !advertisement
  ```
  *Matches: "AI breakthrough" but not "AI advertisement"*

- **Groups**: Separate with empty lines for independent tracking
  ```txt
  # Group 1: Tech companies
  Tesla
  Apple
  +product
  
  # Group 2: Finance
  Stock Market
  Bitcoin
  !prediction
  ```

### Push Schedule

Edit `.github/workflows/crawler.yml` to change the schedule:

```yaml
schedule:
  - cron: '*/30 * * * *'  # Every 30 minutes
```

Examples:
- `'0 * * * *'` - Every hour
- `'0 */2 * * *'` - Every 2 hours
- `'0 9,12,18 * * *'` - At 9 AM, 12 PM, and 6 PM

**Important**: Don't set intervals too short to respect the NewsNow API service.

### Push Time Window (Optional)

Limit notifications to specific hours:

```yaml
notification:
  push_window:
    enabled: true
    time_range:
      start: "09:00"  # Start at 9 AM
      end: "18:00"    # End at 6 PM
    once_per_day: false  # Push multiple times within window
```

---

## Troubleshooting

### Discord notifications not appearing

**Check these items**:

1. **Webhook URL is correct**:
   - Go to Settings → Secrets → Actions
   - Verify `DISCORD_WEBHOOK_URL` is set
   - Make sure the URL starts with `https://discord.com/api/webhooks/`

2. **Workflow ran successfully**:
   - Go to Actions tab
   - Check the latest workflow run
   - Look for errors in the logs

3. **Discord channel permissions**:
   - Make sure the webhook has permission to post in the channel
   - Try recreating the webhook

4. **Test the webhook manually**:
   ```bash
   curl -H "Content-Type: application/json" \
     -d '{"content": "Test from TrendRadar"}' \
     YOUR_DISCORD_WEBHOOK_URL
   ```

### GitHub Pages not updating

**Solutions**:

1. **Check Pages is enabled**:
   - Settings → Pages
   - Verify "Source" is set to a branch

2. **Check workflow permissions**:
   - Settings → Actions → General
   - Scroll to "Workflow permissions"
   - Select "Read and write permissions"
   - Click "Save"

3. **Check build status**:
   - Go to Actions tab
   - Look for "pages-build-deployment" workflow
   - Check for errors

4. **Clear cache**:
   - Visit your GitHub Pages URL
   - Hard refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)

### No news matching keywords

**Possible causes**:

1. **Keywords too specific**:
   - Try broader keywords first
   - Remove required words (`+`) temporarily

2. **Wrong language**:
   - Chinese platforms require Chinese keywords
   - Western platforms need English keywords
   - Use translation feature for cross-language matching

3. **No news during time period**:
   - Check if your keywords are trending
   - Try more popular topics

4. **Filter words too aggressive**:
   - Review your `!` filter words
   - Temporarily remove filters to test

### Workflow fails with errors

**Common issues**:

1. **Invalid YAML syntax**:
   - Use a YAML validator: https://www.yamllint.com/
   - Check indentation (use spaces, not tabs)

2. **Missing secrets**:
   - At least one notification channel must be configured
   - Check Settings → Secrets → Actions

3. **Rate limiting**:
   - Don't run workflows too frequently
   - Respect the NewsNow API limits

### Getting help

If you're still stuck:

1. **Check existing issues**: [GitHub Issues](https://github.com/SomethingGeneric/TrendRadar/issues)
2. **Open a new issue**: Include:
   - What you tried
   - Error messages (screenshots)
   - Your configuration (remove secrets!)
3. **Review the full documentation**: [README-EN.md](README-EN.md)

---

## Next Steps

Now that you have TrendRadar set up:

1. **Customize your keywords** in `config/frequency_words.txt`
2. **Add more sources** that interest you
3. **Adjust the push schedule** to your needs
4. **Enable other notification channels** (Telegram, Email, etc.)
5. **Share your setup** with friends!

For advanced features like AI analysis, Docker deployment, and more, see the [full documentation](README-EN.md).

---

**Need Quick Help?**
- [README-EN.md](README-EN.md) - Full documentation
- [QUICKSTART.md](QUICKSTART.md) - Quick start guide
- [Issues](https://github.com/SomethingGeneric/TrendRadar/issues) - Report bugs or ask questions

Happy trending! 📊
