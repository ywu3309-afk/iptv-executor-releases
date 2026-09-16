# IPTV Executor Releases

This public repository contains signed customer release artifacts only. Product source code, private business knowledge, customer data, credentials, payment recipient details and signing private keys are not stored here.

## Verify a download

Compare the file SHA-256 with `SHA256SUMS.txt`. The executor also verifies `release-manifest.json` with the embedded Ed25519 public key before online updates.

## Files

- `IPTV-Windows-Executor-0.3.16.zip`: Windows package with the unified IPTV Automation launcher and safe updater.
- `IPTV-Chrome-Extension-0.4.16.zip`: Chrome extension package.
- `release-manifest.json` and `release-manifest.sig`: machine-readable signed update metadata.
