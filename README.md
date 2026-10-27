# Aurea Launcher

An independently developed Windows launcher for Minecraft: Java Edition, with a warm-white and champagne-gold interface.

**Development preview · Version 0.11 · Minecraft Services application approval pending**

This repository introduces Aurea and documents its authentication and privacy design. It does not distribute Minecraft, account credentials, application binaries, or the launcher's source code.

## Overview

Aurea is a native .NET 8 / WPF application for Windows 10/11 x64. It is designed for the developer and a small group of friends who use their own licensed accounts. It does not embed a browser engine.

Implemented features include version and instance management, official-file integrity checks, managed Java runtimes, mod and modpack management, resource and shader management, server bookmarks, LAN discovery, and local vanilla-server backup tools. Game files and third-party components are obtained separately following the user's actions.

## Accounts and game ownership

- Microsoft sign-in takes place on Microsoft's official website, using Aurea's own registered public OAuth application.
- The launcher checks Java game entitlements and a valid official player profile before creating a playable Microsoft identity.
- An explicit offline option uses the official name and UUID of an account whose permanent Java ownership was previously verified locally. Arbitrary unverified local-player identities are not a launch option.
- Subscription-only access uses online validation rather than being treated as permanent offline ownership.
- Third-party server authentication requires a binding to the user's verified Microsoft Java account. It does not substitute for game ownership.

See [Authentication design](AUTHENTICATION.md) and [Privacy](PRIVACY.md).

## Current status

The local 0.11 implementation has passed 463 automated checks using temporary fixtures, including simulated authentication responses. This does not establish that the application has been approved or that its real entitlement and offline flows have passed end-to-end testing.

Microsoft and Xbox sign-in have succeeded in local testing, but Minecraft Services currently rejects this application's registration. Application approval and real-account verification are still pending. The described offline-cache and third-party-authentication arrangements will be disclosed to the reviewer for confirmation.

## 中文介绍

Aurea Launcher 是独立开发的 Windows 原生 Minecraft Java 启动器，采用 .NET 8 / WPF，使用暖白与香槟金细线界面，不捆绑浏览器引擎。

提供版本与实例管理、文件校验、Java 环境管理、模组与整合包、资源和光影、服务器收藏、局域网发现，以及本地原版服务端与备份工具。

启动游戏前验证微软账号的 Java 游戏资格与正式档案。永久所有权验证后可明确选择该账号的离线模式，沿用正式名称和 UUID。旧本地档案保留，但不允许用未经验证的任意名字启动游戏。第三方认证也需绑定正版所有权账号。

当前为 **0.11 开发预览版**，已通过 463 项合成检查。Minecraft API 准入尚未获批，真实许可接口、离线运行与进服验收仍待完成。本仓库用于项目介绍，不包含个人凭据、游戏本体、程序安装包或启动器源码。

## Independence

Aurea is not affiliated with or endorsed by Mojang or Microsoft. Minecraft and related trademarks belong to their respective owners. The implementation is independently written; other launchers' source code, visual assets and OAuth application identities are not included.

Information reflects the local development state on 2026-10-27.
