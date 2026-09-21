# 0.3.24

- Business welcome instructions are now used only as AI guidance and can no longer be sent directly to customers when a model fails.
- The final WhatsApp delivery layer blocks internal prompt text, including already queued unsafe replies.
- Duplicate non-empty text events from the same customer within 15 seconds are processed once, while different customers and separate media messages remain independent.
- Existing customer databases, settings, AI keys, business profiles, server configuration and WhatsApp sessions remain preserved during signed update.
