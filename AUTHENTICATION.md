# Authentication and ownership design

This describes the implemented 0.11 development preview. Minecraft Services approval has not yet been granted. Offline caching and third-party authentication are disclosed here for review; their presence is not a claim of platform approval.

## Microsoft sign-in

1. The user starts sign-in in the launcher.
2. Aurea requests a device code with its own public application ID and opens the official verification website in the system browser. Passwords are entered on Microsoft's website.
3. Microsoft authorization is exchanged through Xbox Live and XSTS for a Minecraft Services session.
4. The launcher requests Java entitlements and requires a qualifying game entitlement.
5. It retrieves and validates the official player name and UUID before saving a playable identity.

The configured scopes are `XboxLive.signin offline_access`. A client secret is not embedded. Authentication failures identify the failed service stage; unknown response bodies and tokens are not copied into diagnostic messages.

## Online sessions

An already verified online session may be reused in memory only for the same account credential and application ID, within the service-reported token lifetime with an expiry margin. Missing or expired lifetimes, account/application changes, logout and application restart require authentication again. Canceled requests do not renew or reuse a session.

Refresh credentials and account records are encrypted locally using Windows DPAPI. Minecraft access tokens are kept in memory rather than written into the account database.

## Explicit offline mode

Offline mode requires a locally stored successful permanent-Java-ownership verification for that particular Microsoft account. It keeps the official player name and UUID and does not expose an arbitrary-name identity editor. Existing unverified local or legacy account records do not automatically gain this eligibility.

The implementation distinguishes a playable game entitlement from a permanent ownership entitlement. Subscription-only access is not treated as permanent offline ownership. Explicit online authentication rejection revokes cached offline eligibility; network errors or cancellation do not automatically switch the game to offline mode.

The cache records a prior verification on the same Windows user. It is not a newly issued license or a claim that eligibility can never change. Servers that require an online session continue to enforce their own authentication.

## Third-party server authentication

A third-party account is bound to one specified Microsoft account with verified Java access. Before client launch, Aurea validates that ownership account, or reuses its still-valid verified online session, then authenticates the third-party role. Removing the ownership account does not silently bind the role to another account. Third-party role authentication alone cannot create game ownership.

## Validation limits

Local automated tests use synthetic HTTP responses and account fixtures. They cover denied entitlements, invalid profiles, cache boundaries, account binding and encrypted reload. The application's registration currently receives `Invalid app registration` from Minecraft Services, so real-account entitlement, offline gameplay and third-party multiplayer validation remain pending. Any required platform review changes will be addressed before claiming approved access.
