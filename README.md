# Surge RULE-SETs

This repository contains reusable RULE-SET lists and complete configuration files for Surge.

## 📦 Configuration Files

### Complete Surge Configurations

#### Ultimate Version (终极版)
**File:** `surge-config-ultimate.conf`

A production-ready configuration with all features enabled:

- ✅ Complete DNS configuration with multiple DoH servers
- ✅ Comprehensive proxy groups (US, Singapore, Japan, Hong Kong)
- ✅ Application-specific routing (Apple, Telegram, YouTube, TikTok, AI services)
- ✅ Advanced features: MITM, URL Rewrite, Script support
- ✅ Automatic URL testing for optimal proxy selection
- ✅ Full rule set with 6000+ rules

**Best for:** Advanced users who need full control and all features.

#### Advanced Version (进阶版)
**File:** `surge-config-advanced.conf`

A balanced configuration between simplicity and functionality:

- ✅ Optimized DNS configuration
- ✅ Essential proxy groups with auto-selection
- ✅ Application-specific routing (Apple, Telegram, YouTube, TikTok, AI, GitHub)
- ✅ Basic MITM and URL Rewrite support
- ✅ Comprehensive rule set with 4000+ rules
- ✅ Good balance of performance and features

**Best for:** Intermediate users who want more features than the simple version but don't need all advanced features.

#### Simple Version (简化版)
**File:** `surge-config-simple.conf`

A streamlined configuration with core features only:

- ✅ Essential DNS configuration
- ✅ Basic proxy groups
- ✅ Main application routing
- ✅ Core rule sets (2000+ rules)
- ✅ Easy to set up and maintain

**Best for:** Users who want a simple, efficient setup.

## 📁 Rule Files

### Direct Critical Services

A curated list for routing essential services DIRECT to ensure reliability and low latency:
- DNS/DoH endpoints
- NTP time servers
- Captive portal detection
- Major payment/banking domains
- Key Tencent and Bytedance domains

File path:
- `rules/direct.list`

Usage in Surge (example):

```
RULE-SET,https://raw.githubusercontent.com/chx86996/surge-guize/main/rules/direct.list,DIRECT,no-resolve
```

### Third-party RULE-SET module (auto-updating)

This module references upstream RULE-SET URLs so it stays up-to-date automatically without mirroring.

File path:
- `rules/thirdparty.sgmodule`

Enable in Surge via URL:
- iOS/macOS > Modules > Install from URL, then paste one of the following URLs:
  - Raw (GitHub):
    - https://raw.githubusercontent.com/chx86996/surge-guize/main/rules/thirdparty.sgmodule
  - CDN (jsDelivr):
    - https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/rules/thirdparty.sgmodule

The module defines only [Rule] entries and pulls RULE-SET content directly from upstream sources, honoring their update intervals.

### Other Rule Files

- `rules/AI.list` - AI services (ChatGPT, Claude, GitHub Copilot, etc.)
- `rules/google.conf` - Google services
- `rules/youtube.conf` - YouTube
- `rules/tiktok.conf` - TikTok

## 🚀 Quick Start

### Using Complete Configuration Files

1. **Download the configuration:**
   ```bash
   # Ultimate version
   curl -o surge.conf https://raw.githubusercontent.com/chx86996/surge-guize/main/surge-config-ultimate.conf

   # Advanced version
   curl -o surge.conf https://raw.githubusercontent.com/chx86996/surge-guize/main/surge-config-advanced.conf

   # Simple version
   curl -o surge.conf https://raw.githubusercontent.com/chx86996/surge-guize/main/surge-config-simple.conf
   ```

2. **Edit the configuration:**
   - Replace proxy server information in the `[Proxy]` section
   - Adjust proxy groups as needed

3. **Import to Surge:**
   - iOS: Use iTunes file sharing or AirDrop
   - macOS: Import via Surge's configuration manager

### Choosing the Right Configuration

| Configuration | Rules Count | Features | Target Users |
|-------------|-------------|----------|--------------|
| Ultimate | 6000+ | All features including MITM, scripts, multi-region | Advanced users |
| Advanced | 4000+ | Core features with some advanced options | Intermediate users |
| Simple | 2000+ | Essential features only | Beginners |

### Using Rule Modules Only

1. Install the third-party module from Surge's Module Store
2. Add `rules/direct.list` as a custom rule set if needed

## 📖 Detailed Installation

For detailed installation instructions, please see [INSTALL.md](INSTALL.md).

## 📚 Documentation

- [QUICKSTART.md](QUICKSTART.md) - Quick start guide for beginners
- [INSTALL.md](INSTALL.md) - Detailed installation and configuration guide
- [COMPARISON.md](COMPARISON.md) - Comparison between different configuration versions
- [PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md) - Project structure and file descriptions

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Add new rule sets
- Improve existing configurations
- Report bugs or issues

## 📄 License

This project is open source and available under the MIT License.
