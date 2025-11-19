# Contributing to TrendRadar

Thank you for your interest in contributing to TrendRadar! This document provides guidelines for contributing to the project, especially for adding support for Western media sources.

## 🌍 Language & Translation Status

This project was originally developed in Chinese (Mandarin) and is currently being translated to English to make it accessible to international contributors.

### Translation Progress

- ✅ **Configuration Files**: Fully translated
  - `config/config.yaml` - All comments in English
  - `config/frequency_words.txt` - English examples provided
  
- ✅ **Core Code** (Partially Translated):
  - Function docstrings - Translated
  - Error messages - Translated  
  - Status messages - Partially translated
  - Variable/function names - Kept unchanged for minimal changes
  
- ✅ **Documentation**:
  - `README-EN.md` - English version available
  - GitHub Actions workflows - Translated

### Mixed Language Notes

- **Chinese Platform Names**: Platform names like "知乎 (Zhihu)", "微博 (Weibo)", "抖音 (Douyin)" are kept as they are proper nouns
- **Date Formatting**: Uses Chinese date format (年月日) in file paths for consistency with existing data
- **Print Statements**: Gradually being translated to English

## 🚀 Adding Western Media Sources

The project currently monitors Chinese news platforms. Here's how to add Western media sources:

### Prerequisites

The project uses the [newsnow](https://github.com/ourongxing/newsnow) API for data aggregation. Check if your desired platform is available:

1. Visit https://newsnow.busiyi.world/
2. Click "More" to see available platforms
3. Check the [source code](https://github.com/ourongxing/newsnow/tree/main/server/sources) for platform IDs

### Step 1: Add Platform to Configuration

Edit `config/config.yaml` and add your platform to the `platforms` section:

```yaml
platforms:
  # Existing Chinese platforms
  - id: "zhihu"
    name: "Zhihu (知乎)"
  
  # Add Western platforms here
  - id: "hackernews"
    name: "Hacker News"
  - id: "reddit-popular"
    name: "Reddit Popular"
  - id: "producthunt"
    name: "Product Hunt"
```

### Step 2: Configure Keywords

Edit `config/frequency_words.txt` with English keywords you want to track:

```txt
# Technology News
AI
ChatGPT
Machine Learning
+release  # Required word: must include "release"

# Startups & Business
Startup
Funding
IPO
!advertisement  # Filter word: exclude posts with "advertisement"

# Your custom topics
Tesla
SpaceX
```

**Keyword Syntax:**
- Normal words: Match any occurrence (e.g., "Tesla", "AI")
- Required words (+): Must appear together (e.g., +launch, +release)
- Filter words (!): Exclude news containing these (e.g., !ad, !spam)
- Empty lines: Separate different keyword groups for independent tracking

### Step 3: Test Your Configuration

```bash
# Local testing
python main.py

# Check output
ls output/  # Will create dated folders with results
```

### Step 4: Submit Your Changes

1. Fork the repository
2. Create a feature branch: `git checkout -b add-western-sources`
3. Commit your changes with clear messages
4. Submit a pull request with:
   - Description of platforms added
   - Example keywords configured
   - Screenshots of output (optional but helpful)

## 📝 Code Contribution Guidelines

### Adding New Features

1. **Keep Minimal Changes**: Modify only what's necessary
2. **Maintain Compatibility**: Don't break existing Chinese platform support
3. **Test Thoroughly**: Ensure both Chinese and Western platforms work
4. **Document Changes**: Update relevant documentation

### Code Style

- Follow existing Python code style
- Add English comments for new code
- Keep Chinese comments where they exist alongside English translations
- Use descriptive variable names (English preferred for new code)

### Testing

Before submitting:
```bash
# Run the crawler
python main.py

# Check configuration
cat config/config.yaml

# Verify keywords
cat config/frequency_words.txt
```

## 🐛 Reporting Issues

When reporting issues:
1. **Use English** for issue title and description
2. Include:
   - Python version
   - Operating system
   - Configuration (remove sensitive webhooks)
   - Error messages (full traceback)
   - Steps to reproduce

## 💡 Feature Requests

We welcome feature requests for:
- Additional Western news sources
- New notification channels
- Analysis features for Western markets
- UI/UX improvements for international users

## 🌐 Internationalization

### Translation Help Needed

We welcome translations for:
- Remaining print statements in `main.py`
- User-facing messages
- Error messages
- Documentation

### Translation Guidelines

1. Keep technical terms in English (e.g., "webhook", "API")
2. Maintain clarity over literal translation
3. Keep platform names as proper nouns
4. Don't translate configuration keys or file paths

## 📚 Resources

- [Original Chinese README](README.md)
- [English README](README-EN.md)
- [newsnow API Sources](https://github.com/ourongxing/newsnow/tree/main/server/sources)
- [GitHub Issues](https://github.com/SomethingGeneric/TrendRadar/issues)

## 🙏 Acknowledgments

- Original project by [sansan0](https://github.com/sansan0)
- Data aggregation by [newsnow](https://github.com/ourongxing/newsnow)
- Translation efforts by the community

## 📧 Contact

- Open an issue for questions
- Check existing issues before creating new ones
- Be respectful and constructive in discussions

---

**Happy Contributing! 🎉**
