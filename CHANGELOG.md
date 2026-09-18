# 0.3.23

- Clicking Start now creates a fresh installation automatically when the previously registered installation and customer data have been deleted.
- A stale registration is archived before reinstalling; no existing folder or customer file is deleted.
- If the registered folder still contains customer data, the launcher continues to use the protected recovery path and preserves that data.
- The launcher completes startup as soon as the verified local wizard reports READY, uses a closed short connection for readiness probes, and unlocks after a bounded timeout.
- Open Console and Refresh Status remain available during startup, and the launcher opens the local console after successful startup.
- Existing customer databases, settings, AI keys, server configuration and WhatsApp sessions remain preserved during signed update or recovery.
