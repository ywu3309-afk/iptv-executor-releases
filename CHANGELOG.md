# 0.3.6

- A failed first WhatsApp browser launch now closes the failed client, rotates to a fresh isolated session and retries once automatically.
- Recovery is bounded to one retry, so a second failure is reported without creating a browser loop.
- Existing customer data, settings, AI keys and server configuration remain preserved during signed updates.
- Customer packages keep the protected runtime, protected browser assets and obfuscated Chrome extension without source maps.
