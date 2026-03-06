# App Review Notes — Claude Usage Widget

## App Purpose

Claude Usage Widget is a home screen widget for iOS that displays a user's Claude.ai usage statistics (e.g., 5-hour rolling usage, 7-day usage by model). It is a companion tool for existing Claude.ai subscribers.

## Authentication

The app authenticates by asking the user to log in to claude.ai via an embedded WKWebView (standard web login). Upon successful login, the session cookie (`sessionKey`) is captured and stored in the iOS Keychain. This credential is used solely to make authenticated HTTPS requests to `claude.ai/api/` to retrieve the user's own usage data.

## Sign In with Apple

**Sign In with Apple is not required for this app.**

Per App Store Review Guideline 4.8, Sign In with Apple is not required for "apps that use a particular third-party service's own account system." This app exclusively accesses a user's existing Claude.ai (Anthropic) account. Users must already have a Claude.ai subscription — the app cannot create accounts. This is analogous to a banking or email app that logs into the provider's own existing account system.

## Entitlements

| Entitlement | Reason |
|---|---|
| `com.apple.security.application-groups` | Shared Keychain access group between the main app and the widget extension, so the widget can read the user's session key to fetch usage data in the background. |

## Network Usage

The app makes HTTPS requests to:
- `https://claude.ai/api/organizations` — to retrieve the user's organization ID
- `https://claude.ai/api/organizations/{id}/usage` — to retrieve usage statistics

No other network requests are made. No third-party analytics or tracking is present.

## Demo Account

To test the app, App Review will need a Claude.ai account with an active subscription (Pro or Max plan). The usage data displayed depends on the account's actual API usage.

If a demo account is needed, please contact us via the GitHub repository and we will arrange access.

## Privacy Policy

https://exceptionraiser.github.io/claude-usage-privacy/
