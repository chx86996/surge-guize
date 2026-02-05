# 快速开始指南

这是最快速的配置指南，帮助您在 5 分钟内完成 Surge 配置。

## 📋 前置准备

1. 已安装 Surge for iOS/macOS
2. 拥有可用的代理服务器（SS、SSR、VMess、Trojan、VLESS 等）
3. 了解代理服务器的基本信息（地址、端口、密码/UUID、加密方式等）

## 🚀 三步配置

### 第 1 步：选择配置文件

根据您的需求选择：

| 用户类型 | 推荐配置 | 特点 |
|---------|---------|------|
| 🌟 新手 | [简化版](https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-simple.conf) | 功能精简，易于上手 |
| 🔧 中级 | [进阶版](https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-advanced.conf) | 功能平衡，性能优异 |
| 💻 高级 | [终极版](https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-ultimate.conf) | 功能完整，高度可定制 |

### 第 2 步：下载并编辑配置

**方法 A：通过 Surge App 直接导入（推荐 iOS 用户）**

1. 在 Safari 中点击上表中的配置文件链接
2. 点击「复制」或「下载」（根据 Surge 版本）
3. 打开 Surge App → 配置 → 点击右上角「+」→「从剪贴板导入」

**方法 B：下载后导入（推荐 macOS 用户）**

```bash
# 下载配置文件（替换为您选择的版本）
curl -o ~/Downloads/surge.conf https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-advanced.conf
```

然后打开 Surge → 配置 → 导入配置文件 → 选择下载的文件

### 第 3 步：配置代理服务器

**这是最重要的步骤！配置文件中的代理信息为示例，必须替换为您的真实代理信息。**

1. 在 Surge App 中，打开刚导入的配置
2. 点击「编辑」按钮
3. 找到 `[Proxy]` 部分，编辑代理服务器信息

**示例配置（替换为您的信息）：**

```ini
# Shadowsocks 示例
MyProxy = ss, your-server.com, 8388, encrypt-method=aes-256-gcm, password=your-password

# VMess 示例
MyProxy = vmess, your-server.com, 443, username=your-uuid, ws=true, ws-path=/path, tls=true

# Trojan 示例
MyProxy = trojan, your-server.com, 443, password=your-password, sni=your-domain.com
```

4. 保存配置

## ✅ 验证配置

1. 在 Surge 首页启用配置
2. 访问 http://ipinfo.io 查看您的 IP
3. 测试访问国内外网站
4. 检查策略组是否按预期工作

## 🔧 常用调整

### 调整策略组

编辑配置文件，找到 `[Proxy Group]` 部分：

```ini
# 示例：让所有流量走代理
🌐 直连/代理 = select, PROXY, DIRECT

# 示例：让特定应用走特定节点
YouTube = select, HK-Node, US-Node, DIRECT
```

### 添加自定义规则

在 `[Rule]` 部分添加：

```ini
# 让特定域名直连
DOMAIN,example.com,DIRECT

# 让特定域名走代理
DOMAIN,example.org,PROXY
```

## 📚 更多信息

- 📖 完整安装指南：[INSTALL.md](INSTALL.md)
- 📦 配置文件说明：[README.md](README.md)
- 💬 遇到问题？查看 [常见问题](INSTALL.md#常见问题)

## ⚠️ 重要提示

1. **代理服务器必须配置正确**，否则无法上网
2. 首次使用建议从**简化版**开始
3. 配置文件中的规则会自动更新，无需手动维护
4. 如遇到问题，请查看 Surge 日志了解详细信息

## 🆘 获取帮助

- Surge 官方文档：https://manual.nssurge.com/
- 提交 Issue：https://github.com/chx86996/surge-guize/issues
- Surge 社区：https://talk.nssurge.com/
