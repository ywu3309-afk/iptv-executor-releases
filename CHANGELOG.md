# 0.3.32

- MEGA 试用开号新增「官方 API 模式」：面板改版后脚本点不动「Create Subscription」，改为直接调 `megaott.net/api/v1` 建号，不再依赖浏览器点击。
- API 模式默认关闭；在 data 目录放 `mega-api-mode.json`（内容 `{"enabled":true}`）后生效，可随时关掉回退到浏览器流程。
- 实测：API 建号返回 201，账号/密码/播放地址齐全，积分不变（0.45），频道全选（449/31/26）。

# 0.3.31

- TREX 试用不再被「试用券余额为负数」挡住：面板的券数显示不准（常见 -72），实际仍能开号。
- 判定改为：价格是 1 Ticket 就放行 TREX，真正的可用性由面板提交结果决定；其它服务器规则不变。

# 0.3.30

- 大模型设置页去掉 Ollama 文案：模型服务商选项改为「本机网关（无外部 API 费用）」，API Key、提示语同步改写。
- 「本机网关」预设默认填 `http://127.0.0.1:8787/v1` + `deepseek-v4.1-flash`，最大输出 tokens 默认 0（不限制）。
- 页面判断「本机地址」的正则改为任意回环端口 + `/v1`，与后端一致。

# 0.3.29

- 「每次最大输出 tokens」不再强制限制：填 0 表示不限制（后端不下发 `max_tokens`，由模型自己决定）。
- 上限从 2000 放宽到 32000；界面提示改成「0 = 不限制」。
- 大模型设置页的前端脚本换成可读版本（顺带修掉「保存 0 后再打开显示 500」的显示问题）。

# 0.3.28

- 修复：在线更新器不再保留 `package.json`，升级后版本号会变成新版本（上一版只改了 upgrade-executor，但真正执行升级的是更新器里的内联逻辑，所以没生效）。
- 依赖变化仍会先校验：不一致直接拒绝升级，不会写坏环境。

# 0.3.27

- 修复：升级时 `package.json` 不再被保留，版本号会随安装包一起更新（以前升级完还显示旧版本号，启动器一直提示有更新）。
- 升级器 `upgrade-executor.mjs` 换成可读版本；依赖是否变化仍会先校验，不一致会拒绝升级。
- 其余运行时（admin / chrome-bridge / online-update）保持上一版的可读版本与补丁。

# 0.3.26

- 修正 0.3.25 安装包：同步 executor-manifest.json 里全部文件的哈希，更新不再报「安装包文件校验失败」。
- 运行时仍是可读版（admin / chrome-bridge / online-update），STRONG 双域名与本机网关补丁保留。

# 0.3.25

- 运行时改为可维护源码：`admin.mjs`、`chrome-bridge.mjs`、`online-update-executor.mjs` 三个文件从混淆版换成可读、带注释的版本。
- STRONG 面板同时支持旧域名 `8k.cms-only.ru` 和新域名 `8k.online-cms.ru`。
- 本机大模型地址放开端口限制：不再只认 `127.0.0.1:11434`，任意本机端口 + `/v1` 均可，可直接接本地网关。
- 发布校验改用新的 Ed25519 发布公钥；后续发布由本仓库签名。

# 0.3.24

- Business welcome instructions are now used only as AI guidance and can no longer be sent directly to customers when a model fails.
- The final WhatsApp delivery layer blocks internal prompt text, including already queued unsafe replies.
- Duplicate non-empty text events from the same customer within 15 seconds are processed once, while different customers and separate media messages remain independent.
- Existing customer databases, settings, AI keys, business profiles, server configuration and WhatsApp sessions remain preserved during signed update.
