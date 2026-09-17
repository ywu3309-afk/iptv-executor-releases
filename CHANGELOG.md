# 0.3.20

- Country channel modules can resolve requests such as keeping, adding or removing Italian channels from the selected server's current catalog.
- A channel request changes only the explicitly named MEGA, LION, STRONG, DINO or TREX account. If the customer does not name one server, the assistant asks first and performs no read or write.
- Channel changes reuse the account snapshot that was already verified immediately before the edit.
- LION, STRONG, DINO and TREX no longer reopen and reread the same account twice in the executor adapter.
- The browser executor still reads the account before saving and reads it back after saving, so account ownership and the exact saved channel selection remain verified.
- MEGA keeps its existing verified browser edit flow.
- Existing customer databases, settings, AI keys, server configuration and WhatsApp sessions remain preserved during signed update.
- Chrome extension 0.4.18 includes the country-module dependency. Reload the extension once after replacing its folder.
