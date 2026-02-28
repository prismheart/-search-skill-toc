# Search Skill TOC

> A Claude Code skill for searching the web using Cloudsways SmartSearch API

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 🌟 Features

- 🔍 **Smart Web Search** - Search the web with highly relevant results
- 📝 **Dynamic Summaries** - Get intelligent snippets and key fragments
- 📄 **Full Content Extraction** - Extract complete webpage content when needed
- ⏰ **Time Filters** - Filter results by Day, Week, or Month
- 🎯 **Flexible Output** - Choose between snippet, mainText, or full content
- ⚡ **Fast & Efficient** - Optimized for LLM context windows

## 📋 Prerequisites

- `curl` - HTTP client
- `jq` - JSON processor
- Cloudsways API Access Key (sign up at https://console.cloudsway.ai)

## 🚀 Quick Start

### 1. Installation

This skill is designed for [Claude Code](https://github.com/anthropics/claude-code). Install it in your Claude skills directory:

```bash
cd ~/.claude/skills/
git clone https://github.com/nodunjj/search-skill-toc.git
```

### 2. Configuration

Set your Cloudsways Access Key:

```bash
export CLOUDSWAYS_AK="your-access-key-here"
```

### 3. Usage

**Basic Search:**
```bash
curl -k -s -G \
  --url "https://console.cloudsway.ai/api/search/smart" \
  --header "Authorization: Bearer ${CLOUDSWAYS_AK}" \
  --data-urlencode "q=your search query"
```

**Recent News (past week):**
```bash
curl -k -s -G \
  --url "https://console.cloudsway.ai/api/search/smart" \
  --header "Authorization: Bearer ${CLOUDSWAYS_AK}" \
  --data-urlencode "q=latest AI developments" \
  --data-urlencode "freshness=Week" \
  --data-urlencode "count=20"
```

**Deep Research (with smart excerpts):**
```bash
curl -k -s -G \
  --url "https://console.cloudsway.ai/api/search/smart" \
  --header "Authorization: Bearer ${CLOUDSWAYS_AK}" \
  --data-urlencode "q=artificial intelligence trends" \
  --data-urlencode "enableContent=true" \
  --data-urlencode "mainText=true" \
  --data-urlencode "count=20"
```

## 📖 Documentation

For detailed documentation, see [SKILL.md](./SKILL.md), which includes:

- Complete API reference
- Request parameters
- Response format
- Content strategy guide
- Troubleshooting tips
- Real-world examples

## 🎯 Content Strategy

| Mode | Latency | Token Cost | Best For |
|------|---------|------------|----------|
| `snippet` | ⚡ Fastest | 💰 Low | Quick overviews |
| `mainText` | ⚡⚡ Medium | 💰💰 Medium | Focused research |
| `content` | ⚡⚡⚡ Slower | 💰💰💰 High | Deep analysis |

## ⚙️ API Parameters

| Parameter | Type | Default | Options |
|-----------|------|---------|---------|
| `q` | String | **Required** | Your search query |
| `count` | Integer | 10 | 10, 20, 30, 40, or 50 |
| `freshness` | String | null | Day, Week, Month |
| `enableContent` | Boolean | false | true/false |
| `mainText` | Boolean | false | true/false |

**⚠️ Important:** `count` must be exactly 10, 20, 30, 40, or 50 - other values will cause errors.

## 🛠️ Troubleshooting

### Environment Variable Not Set

```bash
# Check if AK is configured
echo $CLOUDSWAYS_AK

# Set it if empty
export CLOUDSWAYS_AK="your-access-key"
```

### SSL Connection Issues

Add `-k` flag to curl:
```bash
curl -k -s -G --url "https://..."
```

### Count Parameter Error

Ensure count is one of: 10, 20, 30, 40, or 50
```bash
# ❌ Wrong
--data-urlencode "count=15"

# ✅ Correct
--data-urlencode "count=20"
```

## 📝 Examples

### Example 1: Latest Tech News
```bash
curl -k -s -G \
  --url "https://console.cloudsway.ai/api/search/smart" \
  --header "Authorization: Bearer ${CLOUDSWAYS_AK}" \
  --data-urlencode "q=latest technology news" \
  --data-urlencode "freshness=Day" \
  --data-urlencode "count=10"
```

### Example 2: Research with Excerpts
```bash
curl -k -s -G \
  --url "https://console.cloudsway.ai/api/search/smart" \
  --header "Authorization: Bearer ${CLOUDSWAYS_AK}" \
  --data-urlencode "q=machine learning best practices" \
  --data-urlencode "enableContent=true" \
  --data-urlencode "mainText=true" \
  --data-urlencode "count=20"
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- [Cloudsways Console](https://console.cloudsway.ai) - Get your API key
- [Claude Code](https://github.com/anthropics/claude-code) - Official Claude CLI tool
- [Documentation](./SKILL.md) - Complete skill documentation

## 📧 Contact

**nodunjj** - nodunjj1234@gmail.com

Project Link: [https://github.com/nodunjj/search-skill-toc](https://github.com/nodunjj/search-skill-toc)

---

Made with ❤️ for Claude Code users
