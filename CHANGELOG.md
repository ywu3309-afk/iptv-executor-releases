# 0.3.19

- Administrators can assign each customer either Basic Automation or Full Automation.
- Basic Automation keeps five-server trial creation, MAC trials and channel changes, while AI reception and AI configuration remain unavailable.
- Full Automation includes the complete AI reception workflow. Existing enabled customers retain Full Automation during database migration; new registrations default to Basic Automation.
- Changing a service plan revokes old web sessions and executor binding so the new entitlement is applied after the customer reconnects with this release.
- Chrome extension 0.4.17 checks MEGA, LION, DINO, TREX and STRONG login sessions every 30 seconds while their tabs remain open.
- Session checks yield during trial creation and channel changes, and login recovery never bypasses CAPTCHA or Cloudflare verification.
- Update the Chrome extension to 0.4.17, reload it in Chrome and refresh the five panel tabs after this executor update.
- Business Profile provides one-click JSON export and import for moving customer business settings to another computer.
- The backup restores prices, payment instructions, support details, player settings, five server templates and business images.
- AI keys, panel credentials, WhatsApp sessions, customer chats and created-account passwords are excluded from the JSON backup.
- Existing customer databases, settings, AI keys, server configuration and WhatsApp sessions remain preserved during signed update.
- Customer packages keep the protected runtime, protected browser assets and obfuscated Chrome extension without source maps.
