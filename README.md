# Surge RULE-SETs

This repository contains reusable RULE-SET lists for Surge.

## Direct Critical Services

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

Notes:
- The list lines contain only the rule type and value (no policy), suitable for remote import.
- If this repository is private or not hosted publicly, you can serve the file yourself and reference a self-hosted URL in Surge on iOS/macOS.

## Third-party RULE-SET module (auto-updating)

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
