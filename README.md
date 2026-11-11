# i0v0i-ruleset

按来源整理的分流规则集。

## 规则目录

| 来源 | 范围 | 文件 |
| --- | --- | --- |
| 懒猫 | 共用普通域名白名单，排除远程 AI 白名单 | [域名列表](rules/lazycat/domains.txt) · [Mihomo](rules/lazycat/mihomo.yaml) · [Surge / Loon](rules/lazycat/surge.list) |

域名匹配包含自身及全部子域，使用 `DOMAIN-SUFFIX`。

```text
rules/
  lazycat/
    domains.txt
    mihomo.yaml
    surge.list
```

新增来源放在 `rules/<来源>/`。

## 订阅地址

以下地址可直接拉取，无需登录。

```text
https://raw.githubusercontent.com/i0v0i-code/i0v0i-ruleset/main/rules/lazycat/domains.txt
https://raw.githubusercontent.com/i0v0i-code/i0v0i-ruleset/main/rules/lazycat/mihomo.yaml
https://raw.githubusercontent.com/i0v0i-code/i0v0i-ruleset/main/rules/lazycat/surge.list
```

| 文件 | 格式 |
| --- | --- |
| `domains.txt` | 每行一个域名 |
| `mihomo.yaml` | Mihomo / Clash classical rule-provider |
| `surge.list` | Surge / Loon DOMAIN-SUFFIX 规则，策略由客户端指定 |

## Mihomo 示例

将 `懒猫家宽` 替换为实际策略组名，并将此规则放在通用兜底规则之前。

```yaml
rule-providers:
  lazycat:
    type: http
    behavior: classical
    format: yaml
    url: https://raw.githubusercontent.com/i0v0i-code/i0v0i-ruleset/main/rules/lazycat/mihomo.yaml
    path: ./ruleset/lazycat.yaml
    interval: 7200

rules:
  - RULE-SET,lazycat,懒猫家宽
```
