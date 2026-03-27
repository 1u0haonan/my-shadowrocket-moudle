# Shadowrocket 自定义模块

这个仓库包含一个可直接导入 Shadowrocket 的模块文件 `custom-rules.sgmodule`，方便后续维护自定义直连或代理策略。当前版本只包含一个基础规则：`xtjzx.cn` 走直连。

## 如何使用
1. 打开 Shadowrocket -> 配置 -> 模块。
2. 点击右上角的 `+`，选择「通过 URL 下载」。
3. 填入本仓库 Raw 文件地址（例如 `https://raw.githubusercontent.com/<your-account>/my-shadowrocket-moudle/main/custom-rules.sgmodule`），即可订阅并保持自动更新。

## 自定义规则指南
`[Rule]` 区域支持 Shadowrocket/Surge 语法。每一行代表一条策略，格式为 `类型,匹配值,策略`。常用类型如下：
- `DOMAIN`：匹配完整域名。
- `DOMAIN-SUFFIX`：匹配域名后缀。
- `DOMAIN-KEYWORD`：匹配域名关键字。
- `IP-CIDR`：匹配 IP 网段。

常用策略：`DIRECT`（直连）、`PROXY`（走代理）、`REJECT`（拒绝）。例如：

```
DOMAIN-SUFFIX,example.com,DIRECT
DOMAIN,api.example.org,PROXY
IP-CIDR,203.107.1.0/24,PROXY
```

将新的规则追加在 `custom-rules.sgmodule` 的 `[Rule]` 段即可，按需调整策略即可。为了方便版本管理，建议每次修改后提交并推送到 GitHub，这样 Shadowrocket 就能通过同一个模块链接获得更新。
