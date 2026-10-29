# Supplied APK audit summary

Input inspected: `MS Profile v1.apk`.

## What was visible from the APK package
- Android APK archive with multiple DEX files and AndroidX/MSAL-related dependencies.
- MSAL configuration resources are present.
- Compiled strings identify the prior package as `com.example.msprofile` and show a client ID/redirect URI in its authentication config.
- The APK contains a user-specific Microsoft Learn profile URL for `rohansen-1606`, so the original build is not generalized for arbitrary users.
- The app includes Microsoft Learn credentials/transcript/profile entry points and text explaining that Graph `User.Read` does not return Learn certifications.
- Original Gradle source and readable manifest were not included as separate files; a compiled APK is not a substitute for the original source project.

## Redesign choices
- New neutral identity: Learn Credential Companion.
- No hard-coded personal Learn profile URL.
- MSAL values are placeholders; the supplied APK's app registration was not assumed to be owned by the publisher.
- Profile fields are requested from Graph after explicit sign-in.
- Credentials and transcript pages open within an in-app WebView; the app does not claim a public credential API or fake native credential records.
- Target SDK set to 36 to align with new Play submissions from Aug 31, 2026.

## Limitations of this audit
This was a static archive inspection. The app was not installed or executed, and no behavioral, penetration, privacy, compatibility, or Play policy review has been completed. Treat this as a source redesign starter and release checklist, not a certification that the APK is safe or approved for publication.
