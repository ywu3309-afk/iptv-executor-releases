# 0.3.16

- DINO and TREX creation now return to M3U Lines Userlist and identify the exact account by its unique IPTV Automation marker.
- Subscription-log verification clears stale searches and requires one exact zero-credit Demo, 1 Day, M3U record.
- If creation succeeded but its browser response was lost, the designated test contact can recover that existing account through read-only Userlist, log, playlist and channel checks.
- Recovery never opens the create page, submits another account or saves a channel change; a failed recovery keeps the original task fenced for later read-only verification.
- Ordinary customers still keep the one-trial-per-server rule and cannot clear or bypass unresolved operations.
- Chrome extension 0.4.16 uses a new Classic-panel protocol handshake so an older extension cannot appear compatible with this recovery flow.
- Existing customer databases, settings, AI keys, server configuration and WhatsApp sessions remain preserved during update.
- Customer packages keep the protected runtime, protected browser assets and obfuscated Chrome extension without source maps.
