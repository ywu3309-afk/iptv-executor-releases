# 0.3.42

- 新增「人工接管」：老板用手机回复某个客户后，机器人自动对该客户暂停 45 分钟，不再抢话。
- 判定方式：WhatsApp `message_create` 里发现是“自己账号发出、但不是机器人发的那条”，且 10 秒内没有机器人发送记录。
- 解除方式：给该客户发一句 `#resume`（或 `#恢复` / `#继续` / `#解除`），立即恢复自动回复。
- 暂停期间客户发来的消息不会触发任何自动回复，也不会进 AI 处理；暂停到期后自动恢复。

# 0.3.41

- 频道查询结果里增加「目录过期提醒」：命中的服务器频道缓存超过 7 天时，回复末尾标注“该服务器目录较旧，结果仅供参考”。
- 说明：频道缓存本来就会在每次开试用预检时自动刷新，只有长期不用的服务器（如 DINO）才会变旧。

# 0.3.40

- 新增「频道包查询」：客户问“有没有 beIN / 支持某个台吗”这类问题时，
  系统会在本机缓存的五台服务器频道包里模糊匹配，把命中的包名附在回复后面。
- 实测：`bein` 命中 19 个包（LION、STRONG 等），`ufc` 命中 1 个。
- 局限：匹配到的是“频道包”（bouquet），不是单个频道；缓存可能过期（DINO 为 9 月数据）。

# 0.3.39

- 修复 deepseek-v4.1 系列模型「思考模式没被关掉」：型号正则原来只认 `deepseek-v4` 和 `deepseek-v4-xxx`，不认 `deepseek-v4.1-flash`。
  导致模型把预算花在内部推理上，出现空回答 / 超长响应 / `invalid_response`，然后退回本地规则。
- AI 失败时会记录具体原因：运行日志里输出 `AI unavailable; using local rules | <原因>`，
  并写入 `data/runtime-logs/ai-errors.log`，不再只有笼统一句话。

# 0.3.38

- 试用成功后自动补发两张图：价格表 + 推荐播放器（之前只发一张，而且发送失败）。
- 图片发送增加重试：带说明失败 → 改用文件方式 → 再不行发纯图，避免挂起。
- 修正知识库/报价里的 MEGA 12 个月价格：26.99 → 29.99（与价格图片一致）。

# 0.3.37

- 内置插件更新到修复版（LION 频道清单异步加载、干扰复选框过滤）。
- 执行端代码与 0.3.36 相同，仅同步插件版本，方便新装机器直接拿到 LION 修复。

# 0.3.36

- 试用流程增加两处「原因记录」，覆盖之前查不到的两条静默分支：
  - `stage=previous_state`：客户头上有「待复查」记录，直接回那句固定的复查文案；
  - `stage=authorize_denied`：账号中心明确拒绝授权（不再只是笼统的 unavailable）。
- 之前几次失败没有任何日志，是因为卡在这两条分支上，现在都会写进 `data/runtime-logs/trial-errors.log`。

# 0.3.34

- 修复 API 建号后「试用文案拼不出来」：`business_trial_template_incomplete`。
  原因是 API 账号只带了播放域名、没有完整播放地址，文案里的 `{m3u_url}` 占位符取不到值。
  现在会补上 `playbackServer`（`dns_link`），并据此生成 `get.php?...&type=m3u_plus` 播放地址。

# 0.3.33

- 开试用失败时记录「具体原因」：写进 `data/runtime-logs/trial-errors.log`，同时输出到运行日志（TRIAL_FAILURE …）。
  不再只有 “No trial was created”；客户看到的文案不变。
- 覆盖四个失败点：preflight（预检）、authorize（账号中心授权）、reserve（额度/重复）、create（建号）。

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
