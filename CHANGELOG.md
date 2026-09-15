# 0.3.4

- WhatsApp logout now closes the owned browser before cleaning LocalAuth data, preventing Windows EBUSY file-lock failures.
- Logout and failed-session recovery rotate to a fresh isolated profile, so QR login can start even if an old database file is still releasing.
- A serialized lifecycle gate prevents overlapping logout, reset and startup operations.
- The dashboard explains how to recover from a failed WhatsApp session, while customer data and existing executor settings remain preserved during signed updates.
- Customer packages keep the protected runtime, protected browser assets and obfuscated Chrome extension without source maps.
