# Privacy Policy — Learn Credential Companion

**Draft: must be reviewed and published at a public HTTPS URL before release.** Replace bracketed fields and confirm every statement matches the final app, Microsoft Entra configuration, and any analytics or SDKs added later.

Effective date: [DATE]
Developer/contact: [DEVELOPER NAME AND CONTACT EMAIL]

## What this app does
Learn Credential Companion is an independent app that helps users sign in to a Microsoft account, view basic account profile fields, and open official Microsoft Learn profile, credential, and transcript pages.

## Information processed
When you choose to sign in, Microsoft Authentication Library (MSAL) processes authentication information with Microsoft identity services. With your authorization, the app requests Microsoft Graph delegated `User.Read` access and may retrieve basic profile fields such as display name, email address, job title, and office location when available. The app also loads Microsoft Learn pages you choose to open in its embedded web view; Microsoft may process data according to Microsoft's own terms and privacy statement.

## Tokens and passwords
The app does not ask you to type your Microsoft password into an app-owned form and does not display access tokens. Access tokens are used to call Microsoft Graph and are not intentionally logged. Do not add logging, analytics, or crash reporting that captures authentication secrets.

## Storage and sharing
The current project is designed not to maintain a developer-operated backend or sell user data. Microsoft identity and Graph requests are sent to Microsoft. Microsoft Learn pages are served by Microsoft and may use their own cookies, storage, and authentication. Verify the final implementation and SDK behavior before making this statement live. No data is sold by the developer.

## Retention and deletion
The app does not provide a developer-hosted account database in this version. You can sign out from the app. Sign-out removes the app's active account state through MSAL; it does not necessarily delete information retained by Microsoft. For Microsoft account or Learn data, use Microsoft's account and privacy controls.

## Children's privacy
This app is not designed specifically for children. If the target audience changes, review applicable child-safety and Google Play Families requirements before publication.

## Security
The app is intended to use HTTPS endpoints and Microsoft's MSAL authentication flow. No method of transmission or storage is completely secure. Keep the app updated and do not share your device or account credentials.

## Third-party services
- Microsoft identity platform / MSAL
- Microsoft Graph
- Microsoft Learn

Each service is governed by its own terms and privacy documentation.

## Changes and contact
We may update this policy when the app or data practices change. The current version will be available at [PUBLIC HTTPS POLICY URL]. For privacy questions, contact [CONTACT EMAIL].

## Microsoft disclaimer
This is an independent app and is not affiliated with or endorsed by Microsoft. Microsoft, Microsoft Learn, and related marks are trademarks of the Microsoft group of companies.
