# Google Play release checklist

## Project and binary
- [ ] Choose final unique package/application ID (do not publish with `com.example...`).
- [ ] Configure an Entra app registration owned/authorized by the developer; validate supported account types.
- [ ] Register redirect URI + package name + signing certificate hash, including Play App Signing certificate where required.
- [ ] Replace all MSAL placeholders; test sign-in in release-signed builds.
- [ ] Build a signed Android App Bundle (.aab), not just a debug APK.
- [ ] Target API 36 or higher for new app submissions from August 31, 2026.
- [ ] Run lint, accessibility, crash, performance, network-loss, and pre-launch tests.
- [ ] Verify app name, launcher icon, app behavior, privacy policy and data disclosures match.
- [ ] Ensure all links are HTTPS and only intended hosts load in WebView.

## Play Console account and declarations
- [ ] Create the app in Play Console and choose default language.
- [ ] Upload AAB to internal testing and test on real devices before closed/production rollout.
- [ ] Complete App access instructions for reviewers if any feature needs a signed-in account; provide test account only if permitted and safe.
- [ ] Complete Data safety form accurately for MSAL, Graph, WebView, and every SDK used.
- [ ] Add public privacy policy URL both in Play Console and in-app.
- [ ] Complete Ads declaration accurately (no ad SDK is included by default in this source).
- [ ] Complete target audience and content declarations.
- [ ] Complete content rating questionnaire.
- [ ] Complete app category, contact email, and store listing details.
- [ ] Provide a 512x512 PNG app icon (provided), a 1024x500 feature graphic (provided), and actual app screenshots. For phone screenshots, prepare at least four high-quality 1080px-minimum screenshots as required by current Play listing guidance.
- [ ] Do not upload mockups as real app screenshots. Capture actual screenshots from the final build.
- [ ] Review impersonation/trademark policies; clearly state the app is independent and not official Microsoft software.
- [ ] Complete any developer account verification and testing requirements shown in Play Console for the account type.
- [ ] Submit for review and monitor policy status and pre-launch report.

## Release operation
- [ ] Securely back up upload key; never commit it to Git.
- [ ] Use staged rollout when appropriate; monitor Android vitals and user feedback.
- [ ] Increase versionCode for every update and retain the same application ID and signing lineage.
