# Contributing

Thanks for considering a contribution to Learn Credential Companion.

## Before you start
- Read `README.md`, `SETUP.md`, `APK_AUDIT.md`, and `THIRD_PARTY_NOTICES.md`.
- Do not submit personal account identifiers, tenant IDs that should remain private, client secrets, tokens, passwords, keystores, or signing passwords.
- Do not claim the app retrieves Microsoft Learn credentials through an API unless a supported source is documented and implemented.
- Keep branding independent and do not imply Microsoft endorsement.

## Pull requests
1. Create a focused branch for one change.
2. Describe the reason for the change and any behavior changes.
3. Include reproduction steps for bug fixes and screenshots from a real build for UI changes.
4. Test on a device or emulator where possible; report what was and was not tested.
5. Update documentation, privacy disclosures, and tests when behavior or data processing changes.

## Code style
Follow the existing Kotlin style and Android best practices. Avoid logging authentication details. Keep WebView navigation restricted to intended HTTPS hosts and validate external URLs before opening them.

## Reporting bugs
Use the GitHub bug report template. Include Android version, device/emulator, steps to reproduce, expected behavior, actual behavior, and sanitized logs. Remove email addresses, account IDs, tokens, and other private data from logs.
