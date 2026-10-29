# GitHub repository setup guide

This file is a concise checklist for publishing this source project. The full upload instructions are also in `README.md`.

## Before making the repository public

- [ ] Review the original APK audit in `APK_AUDIT.md`.
- [ ] Confirm you own or have permission to publish all source and image assets.
- [ ] Replace `[COPYRIGHT HOLDER — replace before publishing]` in `LICENSE` with the appropriate copyright holder, or choose a different license.
- [ ] Review `privacy-policy.md`; do not treat the draft as a hosted, final policy.
- [ ] Confirm `app/src/main/res/raw/auth_config.json` contains placeholders only, not your personal app registration settings.
- [ ] Confirm `AndroidManifest.xml` has only intended redirect configuration and that its placeholders match the setup guide.
- [ ] Run `git status --ignored` and inspect what will be committed.
- [ ] Confirm no `.apk`, `.aab`, `local.properties`, `.gradle/`, build output, keystore, password, token, or private profile data will be published.
- [ ] Test a clean clone/build with Android Studio and document any blockers.

## Create the repository

1. Sign in at https://github.com/new.
2. Set the repository name to `learn-credential-companion-android` (or another available name).
3. Add a description and choose Public or Private deliberately.
4. Do not create an extra README, `.gitignore`, or license on GitHub; this project already contains these files.
5. Create the empty repository.
6. Follow the website-upload or Git-command instructions in `README.md`.
7. After upload, verify the rendered README and confirm no secret or personal data was committed.

## Suggested metadata

- Description: Independent Android companion for Microsoft account profile and Microsoft Learn pages.
- Topics: `android`, `kotlin`, `microsoft-entra`, `msal`, `microsoft-graph`, `microsoft-learn`, `education`.
- Website: use a project page only if you create one.
- Releases: publish tagged source only after testing. Attach binaries only after inspecting them and making sure they do not contain personal configuration.
