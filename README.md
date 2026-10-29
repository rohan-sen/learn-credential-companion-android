# Learn Credential Companion (Android)

An independent Android companion app for signing in with Microsoft and opening official Microsoft Learn profile, credentials, Applied Skills, and transcript pages.

> **Project status:** starter project for community review and contribution. It has not been compiled, tested on devices, security-reviewed, or approved by Google Play in this delivery environment. Configure your own Microsoft Entra app registration and complete the test checklist before distributing a build.

> **Not an official Microsoft app.** This project is independent and is not affiliated with, endorsed by, or an official product of Microsoft. Microsoft and Microsoft Learn are trademarks of the Microsoft group of companies.

## Features

- Microsoft sign-in using Microsoft Authentication Library (MSAL).
- Requests Microsoft Graph delegated `User.Read` to display basic account profile fields when available.
- Native Android dashboard and sign-out control.
- In-app access to official Microsoft Learn profile, credentials/Applied Skills, and transcript pages.
- HTTPS-only navigation for the embedded Learn experience.
- No app-owned password form and no UI that displays access tokens.
- Generic app configuration; the source does not hard-code an individual user's Learn profile URL.

### Credential-data limitation

Microsoft Graph's basic `User.Read` permission does **not** provide a user's Microsoft Learn certifications. This project links to the official Learn pages inside an in-app WebView; it does not claim to retrieve certification records as native credential objects and does not fabricate credential data. Learn sign-in and page availability are controlled by Microsoft and may vary by account or page.

## APK audit and redesign notes

The supplied `MS Profile v1.apk` was inspected statically as an Android package. See [`APK_AUDIT.md`](APK_AUDIT.md) for findings and limitations. The APK includes compiled DEX files and MSAL-related resources, but it does not contain the original readable Kotlin source/Gradle project. This repository is a clean source implementation inspired by the observed behavior, **not a decompilation or byte-for-byte reconstruction**.

The uploaded APK contained an individual Learn profile reference and a Microsoft identity configuration for the old package. Those values were not copied into this generic project. The app's MSAL values are placeholders and must be configured by each publisher using an Entra app registration they control.

## Screenshots and artwork

<img width="738" height="1600" alt="image" src="https://github.com/user-attachments/assets/e0186cec-546b-412f-a82a-c59a8e16f65f" />


The included artwork is a screenshot of a running app.

## Requirements

- Android Studio (current stable release recommended).
- JDK 17.
- Android SDK Platform 36 (the project is configured for `compileSdk = 36` and `targetSdk = 36`).
- A Microsoft Entra app registration you own or are authorized to use.
- A physical Android device or emulator for testing.

## Quick start

1. **Clone or download this repository.**
2. Open the repository root folder in Android Studio.
3. Install Android SDK Platform 36 and select JDK 17 if Android Studio asks.
4. Follow [`SETUP.md`](SETUP.md) to register/configure MSAL. Do not try to sign in until you have replaced the placeholders.
5. Sync Gradle.
6. Run the `app` configuration on an emulator or Android device.
7. Sign in using the Microsoft account types supported by your Entra app registration.
8. Use **Refresh profile** to request basic profile fields. Use the Learn section to open the official credentials, transcript, or profile page inside the app.
9. Use **Sign out** when finished.

If Gradle sync fails, check the Android Studio, JDK, SDK, network, and plugin/dependency versions before changing application code. This repository does not currently include the Gradle Wrapper; Android Studio can import the Gradle project, or a maintainer can generate and commit the wrapper using a compatible Gradle installation.

## Configure Microsoft sign-in

The configuration file is [`app/src/main/res/raw/auth_config.json`](app/src/main/res/raw/auth_config.json). It deliberately contains placeholders. You must:

1. Create/select an Entra app registration for the final Android package ID.
2. Choose the supported account audience deliberately (personal Microsoft accounts, work/school accounts, or both, depending on your intended audience).
3. Configure the Android platform with the package ID and the correct signing certificate hash.
4. Replace the client ID and redirect hash placeholders in both the MSAL JSON and `AndroidManifest.xml`.
5. Configure delegated Microsoft Graph `User.Read` and any consent required by your tenant.
6. Test with debug and release signing certificates. If using Play App Signing, follow Microsoft's guidance for the certificate used by the installed Play build.

**Never add a client secret, password, access token, refresh token, keystore, or signing-key password to this repository.** An Android public-client app should not contain a client secret. The client ID is an identifier, not a client secret, but it still needs to belong to a registration you are authorized to use.

See [`SETUP.md`](SETUP.md) for the longer setup and release instructions.

## Build and test

1. Open the project in Android Studio and sync Gradle.
2. Run the debug build on a device/emulator.
3. Test sign-in, cancellation, sign-out, profile refresh, account-type behavior, offline/error states, small and large screens, font scaling, accessibility, and every Learn page.
4. Confirm that passwords and tokens are never shown in UI or written to logs.
5. Run Android Lint and inspect the Play Console pre-launch report after uploading a test bundle.
6. Before distributing, follow [`PLAY_STORE_CHECKLIST.md`](PLAY_STORE_CHECKLIST.md).

To create a signed release, use **Build → Generate Signed Bundle / APK → Android App Bundle** in Android Studio. Keep the upload key and its passwords outside the repository and back them up securely.

## Repository layout

```text
.
├── app/                         # Android application source and resources
├── play-store-assets/           # Listing artwork concepts
├── .github/                     # Issue templates and contribution workflow files
├── APK_AUDIT.md                 # Static audit of the supplied APK
├── CONTRIBUTING.md              # Contribution guide
├── LICENSE                      # License; review copyright holder before publishing
├── PLAY_STORE_CHECKLIST.md      # Release checklist
├── privacy-policy.md            # Draft policy; review and host before release
├── SETUP.md                     # Entra/MSAL configuration and build steps
├── STORE_LISTING.md             # Draft store listing text
└── THIRD_PARTY_NOTICES.md       # Third-party notices
```

## Upload this project to GitHub

### Option A — GitHub website (no Git command line required)

1. Sign in to GitHub and choose **New repository**.
2. Suggested repository name: `learn-credential-companion-android`.
3. Add a short description such as: *An independent Android companion for Microsoft account profile and Microsoft Learn pages.*
4. Choose **Public** only if you intend everyone to view and reuse the code. Choose a license only after confirming you have rights to publish the source and artwork.
5. Do not initialize the new repository with a README if you are uploading this project's existing README.
6. On the new repository page, select **Add file → Upload files**.
7. Extract the downloaded project ZIP on your computer, then drag the **contents** of the extracted folder (including hidden `.gitignore` and `.github` folders) into the upload area. Do not upload the ZIP as the only repository file.
8. Enter a commit message such as `Initial public source and documentation` and select **Commit changes**.
9. Open the repository page and verify that `README.md`, `app/`, `SETUP.md`, `APK_AUDIT.md`, `LICENSE`, `.gitignore`, and `.github/` are visible.

For large or ongoing changes, use Option B. GitHub's browser upload has per-file and total upload limits; do not upload generated build folders or release artifacts.

### Option B — Git command line

Install Git, extract the ZIP, open PowerShell/Terminal in the extracted project folder, and run:

```bash
git init
git add .
git status
git commit -m "Initial public source and documentation"
git branch -M main
git remote add origin https://github.com/YOUR-GITHUB-USERNAME/learn-credential-companion-android.git
git push -u origin main
```

Replace `YOUR-GITHUB-USERNAME` with your GitHub username and create the empty repository first. If Git asks for authentication, use GitHub's supported sign-in or a personal access token; do not put credentials into the remote URL or source files.

Before `git add .`, inspect `git status` and confirm that no local properties, secrets, keystores, APK/AAB files, or user-specific configuration are included.

## Suggested GitHub repository settings

- **Description:** Independent Android companion for Microsoft account profile and Microsoft Learn pages.
- **Topics:** `android`, `kotlin`, `microsoft-entra`, `msal`, `microsoft-graph`, `microsoft-learn`, `education`.
- **README:** Keep setup limitations and credential-data limitations visible.
- **Issues:** Enable bug reports and feature requests if you can maintain them.
- **Security:** Publish a security contact or enable private vulnerability reporting if available.
- **Releases:** Publish source tags/releases after tests; only attach a signed APK/AAB if you intentionally distribute it and have checked that it contains no personal configuration. Never commit keystores.

## Privacy, data safety, and policy

[`privacy-policy.md`](privacy-policy.md) is a **draft**. Review it against the exact code, SDK behavior, account types, WebView behavior, analytics (if any), and your actual contact details. Host the final policy at a stable public HTTPS URL before any public release. Complete GitHub and Google Play declarations accurately. Do not claim security or privacy properties that have not been verified.

## License

The repository includes an MIT license template. Review the copyright-holder line and confirm you have the rights to license all source and artwork before publishing. Third-party dependencies remain under their own licenses; see [`THIRD_PARTY_NOTICES.md`](THIRD_PARTY_NOTICES.md).

## Contributing

Please read [`CONTRIBUTING.md`](CONTRIBUTING.md) before opening a pull request. Report security issues privately using [`SECURITY.md`](SECURITY.md), not a public issue.
