# Privacy and local data

This describes Aurea Launcher 0.11, a Windows development preview. It is not a Mojang or Microsoft product.

## Account information

Microsoft account passwords are entered on Microsoft's official sign-in website, not collected by Aurea. The launcher receives the authorization needed for the user's requested sign-in.

Refresh credentials, saved account details and prior ownership-verification records are stored locally using Windows DPAPI, bound to the current Windows user. Minecraft access tokens are held in memory. A public OAuth client ID is an application identifier, not a password; no client secret is embedded.

For optional third-party authentication, credentials are sent to the HTTPS authentication service the user specifies. Passwords are not saved. Session credentials and ownership-account bindings are stored locally in the encrypted account database.

## Local files and diagnostics

Settings, downloaded components, account records, game directories, worlds, backups and diagnostic files remain on the user's computer. Authentication diagnostics use fixed stage descriptions and numeric codes rather than arbitrary response bodies. Launch logging masks the active session token.

Aurea does not include built-in analytics or automatically upload diagnostic logs. Network requests still disclose normal connection information to the services used for sign-in, downloads, resource searches, server queries and any user-configured forwarding service.

## This repository

This repository contains public project documentation only. It does not contain real account credentials, personal settings, private logs, user worlds or game binaries. The GitHub repository itself is served by GitHub and is subject to GitHub's own privacy practices.

Information reflects the development state on 2026-10-27. Additional services or future versions may require this document to change.
