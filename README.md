# Merlin Cloudflare DDNS：Cloudflare DDNS Script for ASUS Merlin

一个用于在 ASUS Merlin 路由器上通过 Cloudflare API 自动更新路由器 IPv4 / IPv6 DNS 记录到 Cloudflare 注册子域名的 Shell 脚本。

> 支持 A 与 AAAA 记录、Cloudflare 加速（建议false）、Fake-IP 兼容处理、日志调试等功能。

---

## ✨ 特性 Features

- ✅ 支持 Cloudflare API v4
- ✅ 自动更新 A（IPv4）和 AAAA（IPv6）记录
- ✅ 支持 Cloudflare Proxy（CDN 加速）
- ✅ 支持 Fake-IP DNS 修正（如用于 Merlin Clash2）
- ✅ 兼容 `ddns-start` 脚本机制
- ✅ 易于配置、无需 crontab
- ✅ 提供详细日志输出，方便调试

---


## 🚀 快速开始

### 1️⃣ 克隆项目或复制脚本，并赋予其可执行权限

```bash
wget -O /jffs/scripts/ddns-start https://raw.githubusercontent.com/nianqingnet/merlin-cloudflare-ddns/main/ddns-start
chmod +x /jffs/scripts/ddns-start
```

### 2️⃣ 编辑脚本或配置文件
在 ddns-start 开头，填写以下信息：
```
API_TOKEN="Cloudflare API Token"    # 必填：你的Cloudflare API Token | Your Cloudflare API Token
ZONE_ID="Cloudflare Zone ID"        # 必填：你的 Cloudflare Zone ID | Your Cloudflare Zone ID, hex16 string
RECORD_NAME="sub.example.com"       # 必填：你的完整子域名 | Full DNS record name, e.g., sub.example.com
```
可选项：
```
RECORD_TTL=1            # TTL 时间，1 表示自动
UPDATE_IPv6=true        # 是否启用 IPv6 支持
PROXIED=false           # 是否启用 Cloudflare 加速（本人启用时无法正常访问）
DEBUG=true              # 是否输出调试日志
```

🧠 注意事项

请确保你申请了 Cloudflare API Token 并赋予了正确权限（Zone → DNS:Edit）

此脚本适用于 Asuswrt-Merlin 固件，运行于路由器的 ddns-start 钩子中

依赖 curl 和 jq 命令，请提前在 Entware 中安装（Asuswrt-Merlin 3004.388.8_2默认已安装）。



🛠️ 感谢

ASUS Merlin 固件

Cloudflare API 文档

ChatGPT —— 协助优化脚本结构与逻辑
