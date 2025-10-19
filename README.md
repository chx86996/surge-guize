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
