# 项目结构说明

本文档说明了 surge-guize 项目的整体结构和各个文件的作用。

## 目录结构

```
surge-guize/
├── README.md                      # 项目说明文档
├── QUICKSTART.md                  # 快速开始指南
├── INSTALL.md                     # 详细安装指南
├── COMPARISON.md                  # 配置文件对比文档
├── PROJECT_STRUCTURE.md           # 本文件：项目结构说明
│
├── surge-config-ultimate.conf     # 终极版配置文件（完整功能）
├── surge-config-advanced.conf     # 进阶版配置文件（平衡性能）
├── surge-config-simple.conf      # 简化版配置文件（核心功能）
│
└── rules/                         # 规则文件目录
    ├── direct.list                # 直连规则（DNS、NTP、支付等）
    ├── AI.list                    # AI 服务规则
    ├── google.conf                # Google 服务规则
    ├── youtube.conf               # YouTube 服务规则
    ├── tiktok.conf                # TikTok 服务规则
    ├── WWW.list                   # 其他规则
    └── thirdparty.sgmodule        # 第三方规则集引用模块
```

## 配置文件说明

### 1. surge-config-ultimate.conf（终极版）

**文件大小：** ~11.7 KB
**规则数量：** 6000+
**目标用户：** 高级用户

**核心特点：**
- 完整的 [General] 配置，包括高级 DNS 设置
- 多地区代理组（美国、新加坡、日本、香港）
- 全面的应用分流策略
- 完整的 MITM、URL Rewrite、Script 支持
- 自动 URL 测试选择最优代理
- IPv6 支持、Wi-Fi 访问控制
- 外部控制器支持（用于 API 控制）

**主要区块：**
```
[General]      - DNS、网络、日志、性能、隐私配置
[Proxy]        - 代理服务器配置（需要用户填写）
[Proxy Group]  - 策略组配置（15+ 个策略组）
[Rule]         - 规则配置（6000+ 规则，按优先级排序）
[MITM]         - HTTPS 抓包配置
[URL Rewrite]  - URL 重写规则
[Script]       - 脚本配置
```

### 2. surge-config-advanced.conf（进阶版）

**文件大小：** ~8.7 KB
**规则数量：** 4000+
**目标用户：** 中级用户

**核心特点：**
- 优化的 DNS 配置
- 基础代理组（包含自动选择）
- 主要应用分流（Apple, Telegram, YouTube, TikTok, AI, GitHub）
- 基础 MITM 和 URL Rewrite 支持
- 平衡的性能和功能

**主要区块：**
```
[General]      - DNS、网络、日志、性能配置
[Proxy]        - 代理服务器配置（需要用户填写）
[Proxy Group]  - 策略组配置（10 个策略组）
[Rule]         - 规则配置（4000+ 规则）
[MITM]         - HTTPS 抓包配置（基础）
[URL Rewrite]  - URL 重写规则（基础）
```

### 3. surge-config-simple.conf（简化版）

**文件大小：** ~6.0 KB
**规则数量：** 2000+
**目标用户：** 新手用户

**核心特点：**
- 精简的 DNS 配置
- 基础代理组
- 核心应用分流
- 最小化配置，易于上手

**主要区块：**
```
[General]      - 基础 DNS 和网络配置
[Proxy]        - 代理服务器配置（需要用户填写）
[Proxy Group]  - 策略组配置（8 个策略组）
[Rule]         - 规则配置（2000+ 规则）
```

## 规则文件说明

### rules/direct.list

**作用：** 关键服务直连规则
**包含：**
- DNS 服务器（阿里、腾讯等）
- DoH 服务器
- NTP 时间服务器
- 校园网认证
- 支付宝、微信支付等支付平台
- 各大银行域名
- 微信、QQ、抖音等常用应用

### rules/AI.list

**作用：** AI 服务规则
**包含：**
- OpenAI ChatGPT
- Apple Intelligence
- GitHub Copilot
- Google Gemini
- Anthropic Claude
- JetBrains AI
- Meta AI
- Perplexity AI
- Mistral AI
- Grok AI
- Trae AI

### rules/google.conf

**作用：** Google 服务规则
**包含：**
- Google 主域名和子域名
- Google APIs
- Google Cloud Platform
- YouTube 相关域名
- Google Drive
- Gmail
- Google Play
- 其他 Google 服务

### rules/youtube.conf

**作用：** YouTube 专用规则
**包含：**
- YouTube 主域名和子域名
- YouTube CDN
- YouTube API
- YouTube Music
- YouTube Kids

### rules/tiktok.conf

**作用：** TikTok 专用规则
**包含：**
- TikTok 主域名
- TikTok CDN
- ByteDance 相关服务
- TikTok API

### rules/thirdparty.sgmodule

**作用：** 第三方规则集引用模块
**包含：**
- Loyalsoldier 规则集
- Blackmatrix7 规则集
- ACL4SSR 规则集
- fmz200 规则集

**引用的规则集：**
- private.txt（私有 IP）
- WeChat（微信）
- iCloud
- Apple
- Telegram
- YouTube
- TikTok
- Crypto（加密货币）
- Spotify
- GitHub
- AI
- Twitter
- WhatsApp
- Google
- Microsoft
- BiliBili
- ChinaDomain（中国域名）
- ChinaMedia（中国媒体）
- direct.txt（直连列表）
- ChinaIp（中国 IP）
- telegramcidr（Telegram IP）
- ChinaCompanyIp（中国公司 IP）
- proxy.txt（代理列表）
- cncidr（中国 CIDR）

## 文档文件说明

### README.md

**作用：** 项目主文档
**包含：**
- 项目介绍
- 配置文件说明
- 规则文件说明
- 快速开始指南
- 安装方法
- 贡献指南
- 许可证信息

### QUICKSTART.md

**作用：** 快速开始指南
**包含：**
- 前置准备
- 三步配置指南
- 配置文件选择建议
- 常用调整说明
- 重要提示
- 帮助资源

### INSTALL.md

**作用：** 详细安装指南
**包含：**
- 配置文件选择详细说明
- 多种安装方法
- 代理服务器配置示例
- 配置验证步骤
- 常见问题解答
- 高级配置说明
- 配置文件切换指南
- 更新日志

### COMPARISON.md

**作用：** 配置文件对比文档
**包含：**
- 快速对比表
- 详细功能对比
- DNS 配置对比
- 代理组对比
- 规则集对比
- 高级功能对比
- 性能影响分析
- 使用场景推荐
- 迁移指南
- 常见问题

## 使用流程

### 新手用户

1. 阅读 [QUICKSTART.md](QUICKSTART.md)
2. 选择简化版配置
3. 按照快速开始指南配置
4. 参考 [INSTALL.md](INSTALL.md) 解决问题

### 中级用户

1. 阅读 [COMPARISON.md](COMPARISON.md)
2. 选择进阶版配置
3. 参考 [INSTALL.md](INSTALL.md) 详细配置
4. 根据需要自定义规则

### 高级用户

1. 阅读 [README.md](README.md)
2. 选择终极版配置
3. 根据 [COMPARISON.md](COMPARISON.md) 了解所有功能
4. 参考 [INSTALL.md](INSTALL.md) 的高级配置部分
5. 自定义脚本和 MITM 配置

## 规则优先级

所有配置文件都遵循相同的规则优先级（从高到低）：

1. **必须直连的服务**
   - DNS/NTP 服务器
   - 支付/银行
   - 微信/QQ/抖音

2. **广告拦截**
   - 广告域名
   - 追踪域名（仅终极版）

3. **应用分流**
   - 各应用的专用规则集

4. **区域分流**
   - 中国域名/媒体
   - 直连白名单
   - 中国 IP 段

5. **代理规则**
   - 代理列表
   - GFW 列表

6. **最终匹配**
   - 中国 IP 直连
   - 其他流量按 Final 策略组处理

## 规则更新机制

所有配置文件中的规则集都支持自动更新：

- **更新方式：** 从远程 URL 拉取
- **更新频率：** 根据规则集类型设置（1-7 天）
- **更新来源：** GitHub 原仓库
- **CDN 加速：** 使用 jsDelivr CDN 加速访问

## 技术特性

### 兼容性

- **Surge iOS：** 完全支持 Surge 5.x 及以上版本
- **Surge macOS：** 完全支持 Surge 5.x 及以上版本
- **规则格式：** 标准 Surge 规则格式
- **协议支持：** SS, SSR, VMess, Trojan, VLESS

### 性能优化

- **DNS 缓存：** 减少重复查询
- **规则匹配：** 按优先级排序，快速匹配
- **CDN 加速：** 规则集使用 jsDelivr CDN
- **增量更新：** 仅更新变化的规则

### 安全性

- **HTTPS 抓包：** 可选 MITM 支持
- **DNS 加密：** 支持 DoH
- **IPv6 支持：** 可选（终极版）
- **代理加密：** 支持多种加密协议

## 维护建议

### 定期检查

1. 规则集更新状态
2. 代理服务器连接状态
3. 日志中的异常信息
4. 性能影响评估

### 备份配置

1. 定期导出配置文件
2. 保存自定义规则
3. 记录代理服务器信息
4. 备份 MITM 证书

### 更新策略

1. 规则集自动更新（默认开启）
2. 配置文件手动更新（根据需要）
3. Surge App 自动更新（推荐）
4. 关注上游规则集更新

## 扩展开发

### 添加自定义规则

1. 在 [Rule] 部分添加自定义规则
2. 确保规则位置正确（优先级）
3. 测试规则是否生效
4. 记录自定义规则以便维护

### 添加自定义脚本

1. 在 [Script] 部分添加脚本
2. 参考 Surge 脚本语法
3. 测试脚本功能
4. 注意脚本性能影响

### 贡献规则集

1. Fork 项目仓库
2. 在 rules/ 目录添加规则文件
3. 更新相关文档
4. 提交 Pull Request

## 联系方式

- GitHub Issues: https://github.com/chx86996/surge-guize/issues
- Surge 官方文档: https://manual.nssurge.com/
- Surge 社区: https://talk.nssurge.com/

## 许可证

本项目采用 MIT 许可证，详见 LICENSE 文件。
