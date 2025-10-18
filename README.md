Surge 配置：General 终极版 + 方案A（DIRECT 优先）规则

本仓库提供两类可直接复用的 Surge 配置片段：

- Surge/General.conf：通用基础配置，粘贴到你的配置文件的 [General] 段落。
- Surge/Rules_Direct.conf：规则方案A（DIRECT 优先），粘贴到你的配置文件的 [Rule] 段落。

使用方式（iOS 等端）
- 方式一：合并到现有配置
  - 打开 Surge -> Profile -> 编辑你的主配置；
  - 将 Surge/General.conf 的全部内容复制到主配置的 [General] 段落；
  - 将 Surge/Rules_Direct.conf 的全部内容复制到主配置的 [Rule] 段落；
  - 保存并应用。
- 方式二：维护为单独配置文件
  - 新建一个配置，分别将两个文件的内容粘贴到对应段落后保存。

关键说明与建议
- IPv6 开关：General 中默认 ipv6 = false。若你的节点 100% 支持 IPv6，可改为 true；否则建议保持 false，减少异常。
- DoH 与 NTP 强制直连：
  - 原因：避免和代理形成回环、确保 DNS 可用与时间同步可靠；
  - 校验：在 Surge 日志中查看 dns.alidns.com、doh.pub、cloudflare-dns.com、dns.google、time.apple.com 等请求是否命中 DIRECT；也可通过常见 DNS 泄露测试网站验证 DoH 正常。
- 真实 IP 解析：General 中 always-real-ip 仅控制解析是否绕过 CDN/虚 IP 获取真实地址，具体是否直连/代理由 [Rule] 决定。
- 跳过代理名单：General 中 skip-proxy 仅包含本地/链路/登录页域名与网段，业务域名请不要放入，避免与规则冲突。

切换到方案B（PROXY 优先）的指引
- 简单切换：在 Surge/Rules_Direct.conf 中，将需要走代理的分类条目把 DIRECT 改为 PROXY（如银行/支付、微信/腾讯、Apple 等分类块）。
- 独立文件：亦可维护一个单独的 Rules_Proxy.conf（未来可追加到仓库），其结构与 Rules_Direct.conf 相同，仅将对应分类的动作改为 PROXY。

文件语法与粘贴位置
- Surge/General.conf：仅包含 [General] 段落内容；
- Surge/Rules_Direct.conf：仅包含 [Rule] 段落内容；
- 两个文件均可直接复制粘贴到 Surge 对应段落通过校验。

目录结构
- Surge/
  - General.conf
  - Rules_Direct.conf
- README.md（本说明）
- .gitignore（忽略 .DS_Store）

注意
- 本仓库不包含具体的 [Proxy] 或 [Proxy Group] 定义，请结合你的节点与分流需求自定义；
- General 中的健康检查与 GeoIP 数据库自动更新为通用稳定设置，可按需调整；
- 如需对部分分类改为代理优先，请参考上文“切换到方案B”的方法。
