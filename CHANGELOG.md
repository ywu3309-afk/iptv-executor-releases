# 0.3.13

- The unified launcher now reads the registered executor version and synchronizes a stale outer launcher after a successful start.
- Launcher replacement is staged safely when the old launcher is still open, then applied and reopened after that window closes.
- MEGA requires a saved, read-only verified API key and recovers an inconclusive original account by ID without a second create.
- When the original MEGA result has no account ID, extension 0.4.14 performs a read-only unique search by the original username and ownership marker before API verification.
- A pending MEGA recovery blocks duplicate account creation until the original result is resolved.
- The designated test contact keeps unlimited trials for LION, MEGA, DINO, TREX and STRONG, while ordinary customers remain limited to one trial per server.
- Existing customer databases, settings, AI keys, server configuration and WhatsApp sessions remain preserved during update.
- Customer packages keep the protected runtime, protected browser assets and obfuscated Chrome extension without source maps.
