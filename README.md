# Garbage-dump

个人 Clash/Mihomo 规则与杂项仓库。

## rules/ — Clash 规则集（v4 架构，2026-10-12）

配合 [meta-rules-dat mrs](https://github.com/MetaCubeX/meta-rules-dat) 与 [ai-proxy-rules](https://github.com/VPSDance/ai-proxy-rules) 使用。

| 文件 | 用途 | 建议 rules 位置 |
|---|---|---|
| `direct-override.list` | 强制直连白名单（微软登录/推送/Tailscale 等） | 最顶部 |
| `custom.list` | 个人自定义域名（自建服务/开发者工具/LinuxDO） | 广告规则之后 |
| `bybit.list` | Bybit 交易所（补全版） | 早期规则 |
| `PH.list` | 成人站点（补全版） | 流媒体之后 |
| `GoogleCNProxyIP.yaml` | 谷歌中国服务 IP（services.googleapis.cn 等） | GoogleCN 之后 |

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
```

## 根目录 — 旧规则（已被 rules/ 取代）

`AI.list` / `Gemini.list` / `url-test.list` 已由 meta mrs（`category-ai-chat-!cn`、`google-gemini`）与
VPSDance AI 聚合取代；`url-test.list` 中的宽泛 `googleapis.com` 条目因会误伤国内 Google 服务已移除。
`bybit.list` / `PH.list` / `GoogleCNProxyIP.yaml` 移入 `rules/` 并补全。

## 其他

`WTJ_Online*.ini/toml`：Sub-Store 模板。`backup.bin`：数据备份。
