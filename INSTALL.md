# 安装指南

本指南将帮助您安装和配置 Surge 配置文件。

## 目录

- [配置文件选择](#配置文件选择)
- [安装方法](#安装方法)
- [配置代理服务器](#配置代理服务器)
- [验证配置](#验证配置)
- [常见问题](#常见问题)
- [高级配置](#高级配置)

## 配置文件选择

### 终极版 (surge-config-ultimate.conf)

**适合人群：** 高级用户

**特点：**
- 完整的 DNS 配置（多个 DoH 服务器）
- 多地区代理组（美国、新加坡、日本、香港）
- 应用级分流（Apple、Telegram、YouTube、TikTok、AI 服务）
- 高级功能（MITM、URL 重写、脚本支持）
- 自动 URL 测试选择最优代理
- 6000+ 完整规则集

### 进阶版 (surge-config-advanced.conf)

**适合人群：** 中级用户

**特点：**
- 优化的 DNS 配置
- 基础代理组（包含自动选择）
- 应用级分流（Apple、Telegram、YouTube、TikTok、AI、GitHub）
- 基础 MITM 和 URL 重写支持
- 完整规则集（4000+ 规则）
- 功能和性能的良好平衡

### 简化版 (surge-config-simple.conf)

**适合人群：** 新手用户或只需要基础功能的用户

**特点：**
- 精简的 DNS 配置
- 基础代理组
- 主要应用分流
- 核心规则集（2000+ 规则）
- 易于设置和维护

## 安装方法

### 方法一：通过 Surge App 直接导入（推荐）

#### iOS 设备

1. **下载配置文件**
   - 在 Safari 中打开配置文件链接：
     - 终极版：https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-ultimate.conf
     - 进阶版：https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-advanced.conf
     - 简化版：https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-simple.conf
   - 或使用 iCloud Drive 下载

2. **导入到 Surge**
   - 打开 Surge App
   - 进入「配置」标签页
   - 点击右上角「+」按钮
   - 选择「从 URL 导入」或「从文件导入」

3. **激活配置**
   - 选择新导入的配置文件
   - 点击「启用」按钮

#### macOS 设备

1. **下载配置文件**
   - 使用 curl 命令下载：
     ```bash
     # 终极版
     curl -o ~/Downloads/surge-config-ultimate.conf https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-ultimate.conf

     # 进阶版
     curl -o ~/Downloads/surge-config-advanced.conf https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-advanced.conf

     # 简化版
     curl -o ~/Downloads/surge-config-simple.conf https://cdn.jsdelivr.net/gh/chx86996/surge-guize@main/surge-config-simple.conf
     ```

2. **导入到 Surge**
   - 打开 Surge for Mac
   - 进入「配置」标签页
   - 点击左下角「+」按钮
   - 选择「导入配置」
   - 选择下载的配置文件

### 方法二：通过 AirDrop 传输（iOS to iOS）

1. 在一台设备上下载配置文件
2. 使用 AirDrop 发送到目标设备
3. 在目标设备上打开 Surge App 导入

### 方法三：通过 iCloud Drive

1. 将配置文件保存到 iCloud Drive
2. 在所有设备上通过 Surge 的「从文件导入」功能导入

## 配置代理服务器

### 重要提示

配置文件中的代理服务器信息为示例，**必须替换为您的实际代理服务器信息**才能正常使用。

### 编辑配置文件

#### 方式一：在 Surge App 中编辑

1. 打开 Surge App
2. 进入「配置」标签页
3. 选择配置文件
4. 点击「编辑」按钮
5. 找到 `[Proxy]` 部分
6. 修改或添加您的代理服务器

#### 方式二：使用文本编辑器

1. 使用文本编辑器（如 VS Code、Sublime Text）打开配置文件
2. 找到 `[Proxy]` 部分
3. 修改或添加代理服务器
4. 保存文件
5. 重新导入到 Surge

### 代理服务器配置示例

#### Shadowsocks

```ini
MySS = ss, server.com, 8388, encrypt-method=aes-256-gcm, password=your-password
```

参数说明：
- `MySS`: 代理名称（自定义）
- `ss`: 协议类型（Shadowsocks）
- `server.com`: 服务器地址
- `8388`: 服务器端口
- `encrypt-method`: 加密方式
- `password`: 密码

#### ShadowsocksR

```ini
MySSR = ssr, server.com, 8388, encrypt-method=aes-128-cfb, password=your-password, obfs=tls1.2_ticket_auth, protocol=auth_aes128_md5
```

参数说明：
- `obfs`: 混淆方式
- `protocol`: 协议插件

#### VMess

```ini
MyVMess = vmess, server.com, 443, username=your-uuid, ws=true, ws-path=/your-path, ws-headers=Host:your-domain.com, tls=true
```

参数说明：
- `username`: UUID
- `ws`: 是否使用 WebSocket
- `ws-path`: WebSocket 路径
- `ws-headers`: WebSocket 请求头
- `tls`: 是否使用 TLS

#### Trojan

```ini
MyTrojan = trojan, server.com, 443, password=your-password, sni=your-domain.com
```

参数说明：
- `password`: 密码
- `sni`: SNI（服务器名称指示）

#### VLESS

```ini
MyVLESS = vless, server.com, 443, uuid=your-uuid, ws=true, ws-path=/your-path, ws-headers=Host:your-domain.com, tls=true
```

### 更新策略组

配置好代理服务器后，需要更新策略组中的代理列表：

1. 找到 `[Proxy Group]` 部分
2. 修改策略组中的代理列表，将示例代理替换为实际配置的代理

示例：
```ini
# 修改前
自动选择 = url-test, MySS, MySSR, MyVMess, MyTrojan, MyVLESS, url = http://www.apple.com/library/test/success.html, interval = 600

# 修改后（替换为您的代理名称）
自动选择 = url-test, HK-SS, SG-VMess, US-Trojan, url = http://www.apple.com/library/test/success.html, interval = 600
```

## 验证配置

### 1. 检查配置语法

在 Surge App 中，配置文件导入时会自动进行语法检查。如果有错误，会显示错误信息。

### 2. 测试网络连接

1. 启用配置文件
2. 打开 Surge 的「诊断」功能
3. 检查以下项目：
   - DNS 解析
   - 代理连接
   - 规则匹配

### 3. 测试实际使用

1. 打开 Safari 或其他浏览器
2. 访问国内网站（应直连）
3. 访问国外网站（应通过代理）
4. 测试特定应用（YouTube、Telegram 等）

### 4. 查看日志

1. 打开 Surge 的「日志」功能
2. 观察流量走向
3. 确认规则按预期工作

## 常见问题

### Q1: 导入配置文件后无法连接网络？

**解决方案：**
1. 检查代理服务器配置是否正确
2. 确认代理服务器是否正常运行
3. 检查策略组设置
4. 查看日志了解详细错误信息

### Q2: 部分网站无法访问？

**解决方案：**
1. 检查规则优先级是否正确
2. 尝试手动选择策略组
3. 查看日志确认规则匹配
4. 可能需要添加自定义规则

### Q3: AI 服务无法使用？

**解决方案：**
1. 确认代理服务器支持 AI 服务
2. 检查「智能助理」策略组设置
3. 某些 AI 服务可能需要特定地区的 IP
4. 查看日志确认 AI 域名的路由

### Q4: 规则更新失败？

**解决方案：**
1. 检查网络连接
2. 确认规则集 URL 可访问
3. 尝试使用 jsDelivr CDN 加速
4. 手动下载规则集文件

### Q5: 配置文件太大，导致 Surge 卡顿？

**解决方案：**
1. 使用简化版配置
2. 减少规则集数量
3. 禁用不常用的规则集
4. 使用 URL 缓存功能

## 高级配置

### 启用 MITM（HTTPS 抓包）

1. **配置 MITM**

编辑配置文件，找到 `[MITM]` 部分：

```ini
[MITM]
skip-server-cert-verify = false
hostname = %APPEND% api.github.com, api.openai.com
```

2. **安装 CA 证书**

- 在 Surge App 中，进入「设置」>「MITM」
- 点击「生成新 CA 证书」
- 按照提示安装证书到系统

3. **信任证书**

- iOS: 设置 > 通用 > 关于本机 > 证书信任设置 > 启用对 Surge 证书的完全信任
- macOS: 钥匙串访问 > 找到 Surge 证书 > 双击 > 信任 > 使用此证书时 > 始终信任

### 添加自定义规则

在 `[Rule]` 部分添加自定义规则：

```ini
# 示例：让特定域名直连
DOMAIN,example.com,DIRECT

# 示例：让特定域名通过代理
DOMAIN,example.org,PROXY

# 示例：使用特定策略组
DOMAIN-SUFFIX,example.net,🇺🇸 美国
```

### 使用脚本

在 `[Script]` 部分添加自定义脚本：

```ini
[Script]
# URL 重写脚本
event url-request {
  if ($url contains "example.com") {
    $url = "https://redirect.example.com"
  }
}

# 定时任务
cron "0 0 * * *" {
  $networkCheck = httpGet("http://www.apple.com/library/test/success.html")
  if ($networkCheck.statusCode != 200) {
    $notify("Network Check Failed", "Please check your connection")
  }
}
```

### 配置自动更新

配置文件中已设置规则集自动更新，如需调整：

```ini
# 修改更新间隔（单位：秒）
RULE-SET,https://example.com/ruleset.txt,DIRECT,update-interval=86400,no-resolve
```

常用更新间隔：
- `86400` = 每天（推荐）
- `604800` = 每周
- `259200` = 每 3 天

## 配置文件切换

### 使用多个配置文件

1. 导入多个配置文件
2. 在 Surge 中快速切换
3. 为不同场景创建不同配置：
   - 国内使用配置（全部直连）
   - 国外使用配置（代理优化）
   - 工作配置（特定应用代理）
   - 游戏配置（延迟优化）

### 备份配置

定期备份您的配置文件：

1. 导出配置文件到本地
2. 使用 Git 管理配置文件版本
3. 保存到云存储（iCloud、Google Drive）

## 获取帮助

- GitHub Issues: https://github.com/chx86996/surge-guize/issues
- Surge 官方文档: https://manual.nssurge.com/
- Surge 社区: https://talk.nssurge.com/

## 更新日志

### v1.0.0 (2024-02-05)
- 初始版本发布
- 提供终极版和简化版配置
- 完整的规则集支持
- 详细的安装文档
