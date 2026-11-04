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
