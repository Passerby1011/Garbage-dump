# Garbage-dump

个人 Clash / Mihomo 规则与杂项仓库。

---

## 📁 目录结构

| 目录 / 文件 | 用途 |
|---|---|
| `rules/` | **Clash 规则集（当前使用）** — 配合 meta-rules-dat mrs 与 ai-proxy-rules 使用 |
| `icon/` | 策略组图标 |
| `sub-store/` | Sub-Store 模板（`.ini` / `.toml`），与 Clash 规则无关 |
| `misc/` | 杂项数据（备份、模型价格表等） |
| 根目录 `*.list` / `*.yaml` | **旧版规则（兼容保留）** — 仍有在用配置按根路径引用，勿删；新配置请改用 `rules/` |

---

## rules/ — Clash 规则集（当前使用）

配合 [meta-rules-dat mrs](https://github.com/MetaCubeX/meta-rules-dat) 与 [ai-proxy-rules](https://github.com/VPSDance/ai-proxy-rules) 使用。

| 文件 | 用途 | 建议 rules 位置 |
|---|---|---|
| `direct-override.list` | 强制直连白名单（微软登录/推送/Tailscale 等） | 最顶部 |
| `linuxdo.list` | LinuxDO 专属（进程名 + 域名） | 早期 |
| `custom.list` | 个人自定义域名（自建服务 / 开发者工具） | 广告之后 |
| `own-sg.list` | 个人新加坡域名 | 早期 |
| `own-media.list` | 个人影音域名 | 流媒体区 |
| `bybit.list` | Bybit 交易所 | 早期 |
| `download.list` | 下载 / BT / 磁力（URL-REGEX 已等价改写为 DOMAIN-KEYWORD） | 国内直连区 |
| `PH.list` + `ph-extra.list` | 成人站点（补 meta 未收录：onlyfans / rule34 / 中文圈等） | 广告之前 |
| `GoogleCNProxyIP.list` | 谷歌中国服务 IP（纯 CIDR） | GoogleCN 之后 |
| `ai-model.list` / `ai-coding.list` / `ai-global.list` | AI 三源（纯文本，来自 VPSDance 聚合） | AI 区 |

引用示例：

```yaml
rule-providers:
  DirectOverride:
    type: http
    behavior: classical
    format: text
    interval: 86400
    proxy: "🚀 节点选择"
    url: "https://raw.githubusercontent.com/Passerby1011/Garbage-dump/refs/heads/main/rules/direct-override.list"
    path: ./rules/direct-override.list

rules:
  - RULE-SET,DirectOverride,🎯 全球直连
```

---

## 根目录旧规则（兼容保留，勿删）

`AI.list` / `Gemini.list` / `url-test.list` / `PH.list` / `bybit.list` / `GoogleCNProxyIP.yaml`
是**早期版本**，已被 `rules/` 下的同名文件取代。

**保留原因**：仍有在用的 FlClash 配置按**根路径**引用它们，删除会造成订阅断链。
新配置请一律使用 `rules/`。待所有配置迁移完成后可删除。

---

## sub-store/

Sub-Store 模板文件，用于生成订阅，与 Clash 分流规则无关：

`WTJ_Online.ini` / `WTJ_Online_Balance.ini` / `WTJ_Online_Balance.toml`

---

## misc/

`backup.bin`（数据备份）、`one_hub_prices.json`（模型价格表）。
