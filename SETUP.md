# Setup and build

## 1. Prerequisites
- Android Studio current stable release, Android SDK Platform 36, JDK 17.
- A Microsoft Entra tenant/app registration that you own and are authorized to use.
- A Google Play developer account for release.

## 2. Register the Android application in Microsoft Entra
1. Create or select a public-client app registration for the app's final package ID.
2. Configure supported account types intentionally. If this app is for any Microsoft personal account and work/school account, choose the matching supported audience; do not assume a work-only registration supports personal accounts.
3. Add the Android platform using the exact application/package ID and the signing certificate hash for debug and release. For Play App Signing, register the **Play app-signing certificate** hash as well as any upload/debug certificate hashes needed for testing.
4. Copy the Application (client) ID into `app/src/main/res/raw/auth_config.json`.
5. Replace the redirect URI signature-hash placeholder in both `auth_config.json` and the manifest with the value produced by Microsoft's Android/MSAL configuration guidance. The URI, package ID, and certificate hash must match exactly.
6. Confirm Microsoft Graph delegated `User.Read` is configured and admin consent is granted only if your organization requires it.

## 3. Configure the app
- Update `applicationId` and `namespace` in `app/build.gradle.kts` to your final unique package name before first Play release. Update the manifest MSAL redirect host and the MSAL config consistently.
- Keep the app's MSAL client ID public; never embed a client secret in an Android app.
- Host `privacy-policy.md` on a stable public HTTPS URL and add the same URL in-app and in Play Console. The local markdown file is a draft and must be reviewed and adapted to your actual data flows before publishing.
- Replace placeholder contact details in `STORE_LISTING.md` and privacy policy.

## 4. Build and test
1. Open this folder in Android Studio and sync Gradle.
2. Run on a physical device and emulator.
3. Test sign-in/cancel/sign-out, personal and work/school accounts as supported, no network, invalid account configuration, Graph errors, rotation, small screens, large font, accessibility, dark mode, and all Learn pages.
4. Verify no tokens/passwords are written to logs or UI. Test that only HTTPS URLs are loaded in the embedded browser.
5. Run Android Studio's lint and Play Console pre-launch report. Resolve all crashes and policy issues.

## 5. Generate a signed Android App Bundle
1. Android Studio: **Build → Generate Signed Bundle / APK**.
2. Choose **Android App Bundle**.
3. Create or select an upload key and store it securely offline. Never commit keystores/passwords to source control.
4. Select `release`, finish the wizard, and save the `.aab` securely.
5. Enroll in Play App Signing when prompted. Keep a secure backup of the upload key and recovery information.
6. Upload the AAB to an internal testing track first. Verify the installed build and Play App Signing redirect configuration.

## 6. Before production
Complete all declarations and listing requirements in `PLAY_STORE_CHECKLIST.md`. Google Play review approval cannot be guaranteed by source code alone.
