# 0.3.20

- Chrome extension 0.4.19 automatically restores the session checker inside server tabs that were already open when the extension was reloaded.
- Session checks always return an explicit state for MEGA, LION, DINO, TREX and STRONG: online, unbound, closed tab, wrong page, helper unavailable, expired login, verification required or backend request failure.
- One server tab failure no longer interrupts status checks for the other four servers.
- The popup validates the worker response and reports when a provisioning task has priority instead of showing stale results as a completed check.
- Country channel modules can resolve requests such as keeping, adding or removing Italian channels from the selected server's current catalog.
- A channel request changes only the explicitly named MEGA, LION, STRONG, DINO or TREX account. If the customer does not name one server, the assistant asks first and performs no read or write.
- Existing customer databases, settings, AI keys, server configuration and WhatsApp sessions remain preserved during signed update.
