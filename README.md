# CastleMiner Z Mod Manager

A general-purpose mod manager and modding framework for **CastleMiner Z 1.9.9.8 on Steam for Windows**.

> **Unofficial community project:** CastleMiner Z Mod Manager is independently created and published by AnlionGamer. It is not an official CastleMiner Z release and is not affiliated with, sponsored by, approved by, or endorsed by the developers or publisher of CastleMiner Z.

CastleMiner Z Mod Manager provides mod package management, profiles, compatibility/dependency resolution, clean and modded launch modes, game-file validation and repair, diagnostics, multilingual UI support, themes, reusable per-mod settings, and a generic Tools system for independently distributed `.cmztool` utilities.

> **Current version:** v1.2.0  
> The ready-to-use package is `CMZ_Mod_Manager_v1.2.0_Portable.zip`. Download it from the **v1.2.0 GitHub Release**. Do not use GitHub's automatically generated source-code archives as the Mod Manager download.

## What's new in v1.2.0

v1.2.0 adds a generic Manager-owned startup orchestration system for trusted external Tools while preserving the existing Runtime/API compatibility boundary.

- Adds downgrade-safe `.cmzmod` **Format 2** (`manifest.v2.json`) and `.cmztool` **Format 2** (`tool.v2.json`) while retaining Format-1 support.
- Allows Format-2 mods to declare required and optional startup Tools.
- Allows startup-capable Tools to be selected per profile without changing the existing Profile Format 1 contract.
- Resolves startup companions through a deterministic Manager-owned dependency/order graph before Steam/CastleMiner Z launches.
- Uses readiness protocol 1 with session/tool/PID/nonce identity checks instead of fixed startup sleeps.
- Rolls back Manager-started companions when a required prelaunch Tool fails before game launch.
- Revalidates startup Tool install receipts, manifest identity, entry executable identity, and declared payload SHA-256 before automatic execution.
- Strengthens package staging, canonical-path, resource-limit, metadata, receipt, and payload-integrity checks.
- Fixes legacy Format-1 `.cmzmod`/`.cmztool` installation when ZIP payload entries use backslash separators.
- Hardens WPF theme coverage and semantic text contrast for RadioButton, TabControl/TabItem, Expander, ProgressBar, ScrollBar, ToolTip, and existing controls.
- Makes session reporting more precise: Runtime cleanup alone is no longer labeled proof of a normal game exit.
- Extends diagnostics with sanitized startup state and Format-2 metadata.
- Keeps all 23 bundled UI languages in parity with the new v1.2.0 startup/security/status UI.

The final Rev41 FIX6 package passed its automatic Windows build/regression verification, including startup-orchestration, package/tool compatibility, theme-contract, frozen Runtime/SDK hash, Harmony, baseline, localization, and release-boundary checks.

The CMZ Runtime implementation/file version remains **v1.0.1** while its assembly compatibility identity and mod-facing Framework compatibility remain **v1.0.0**. The CMZ Mod SDK/API remains **v1.0.0**.

See [`RELEASE_NOTES_v1.2.0.md`](RELEASE_NOTES_v1.2.0.md) for full details.

## Features

- Install and manage `.cmzmod` packages
- Format-1 and Format-2 mod package support
- Multiple mod profiles
- Dependency and compatibility resolution
- Generic startup orchestration for trusted Format-2 `.cmztool` companions during Modded Launch
- Reusable per-mod settings, including boolean, integer, decimal, text, choice, and multi-select controls
- Launch Castle Miner Z with the active mod profile
- Launch the game clean without the framework/mods
- Validate Castle Miner Z 1.9.9.8 game files
- Repair missing or modified game files from a configured clean backup
- General-purpose CMZ Runtime and Mod SDK framework
- Install and manage independently distributed `.cmztool` utilities from the **Tools** page
- 23 interface languages
- Built-in light, dark, system, and CastleMiner Z material themes
- Custom theme support
- Diagnostics, recovery, and session history tools

## Installation

1. Open **Releases** and download `CMZ_Mod_Manager_v1.2.0_Portable.zip` from the **v1.2.0** release.
2. Extract the ZIP to a permanent folder of your choice.
3. Run `CMZModManager.exe`.
4. Choose your language on first launch.
5. Select your CastleMiner Z installation folder if it is not detected automatically.
6. Follow the Mod Manager's framework setup/update prompts.

The Manager supports the **Castle Miner Z 1.9.9.8 Steam/Windows** release.

## License, extensions, and responsible use

The current repository `main` branch and future CastleMiner Z Mod Manager work are governed by the **AnlionGamer Community Distribution Terms v1.0**. See [`LICENSE.md`](LICENSE.md).

Normal use, inspection of material actually published in the repository, and private modification are allowed under the current terms. Public redistribution of the Mod Manager itself, its source/material, packaged releases, forks, or modified/derivative Manager builds requires **prior permission from AnlionGamer** and must remain **non-commercial**. Sale and paid access are prohibited without separate permission.

The community remains expressly permitted to create and distribute independently authored extensions through the Manager's supported extension mechanisms. Compatible extensions are not considered redistribution of the Mod Manager merely because they require or interoperate with it.

Permitted independently authored community content includes, but is not limited to:

- `.cmzmod` gameplay mods
- `.cmztool` utilities
- custom themes
- translations and localization resources
- configurations, presets, and shareable profiles
- integrations and other extensions using documented public APIs, SDK interfaces, schemas, package formats, or theme formats

Extension authors retain ownership of their own original work, subject to any third-party rights involved, and may choose separate terms for that independent work. Compatible projects may truthfully state that they are made for, compatible with, or require CastleMiner Z Mod Manager.

Users wishing to share the Mod Manager with others should link to an AnlionGamer-designated distribution location rather than reuploading the Manager unless separate redistribution permission has been granted.

The v1.2.0 portable package contains the **CastleMiner Z Mod Manager Community Use and Extension License v1.0** distributed with that package. The repository's current terms do not retroactively replace the license text already distributed inside packaged releases.

The project is intended for legitimate modding. It must not be used to deliberately attack, crash, exploit, corrupt, impersonate, or otherwise harm other players, hosts, systems, or multiplayer sessions. Legitimate single-player use, consensual multiplayer modifications, host customization, accessibility work, debugging, interoperability, and good-faith security research remain permitted within the terms of the license.

## Privacy and trust

CastleMiner Z Mod Manager does not include first-party telemetry or analytics. Diagnostic exports redact common local paths, Steam64 IDs, and custom Manager profile names, and third-party mod logs are not included automatically in the standard diagnostics ZIP.

Diagnostic sanitization is intended to reduce accidental disclosure, not to make arbitrary files safe to publish without review.

Enabled runtime mods execute third-party code inside Castle Miner Z. Installed Tools execute as separate third-party processes. Neither is sandboxed. Startup-capable Format-2 Tools may execute automatically before a Modded Launch when required/selected by the active profile. Only install packages from authors you trust. Package validation, receipts, and hashes verify package integrity; they do not prove that third-party code is trustworthy.

## Windows security notice

Castle Miner Z Mod Manager is distributed without a paid Authenticode code-signing certificate. Windows may therefore show **Unknown publisher** or a Microsoft Defender SmartScreen warning for a new download.

Download releases only from this repository and verify the published SHA-256 checksum when desired. You should not need to disable Windows Security or antivirus protection to use the Mod Manager.

## Tools

The **Tools** page installs and manages independent `.cmztool` packages.

Format-1 Tools remain normal manually launched utilities. Format-2 Tools can additionally declare a validated prelaunch contract for use as trusted startup companions during **Modded Launch**. Required/selected startup Tools are resolved and started by the Manager before Steam/CastleMiner Z, with readiness identity and payload-integrity checks. **Framework Only** and **Launch Clean** do not start startup companions.

Tools are built, versioned, tested, and distributed separately from the Mod Manager. Updating a tool does not require rebuilding `CMZModManager.exe`, and updating the Mod Manager does not intentionally replace installed Tools or ToolData. ToolData is stored separately from installed tool binaries and is preserved by default during normal update/uninstall workflows.

The Mod Manager portable release does **not** bundle a World Builder, other tool implementation, `.cmztool` package, gameplay mod, or custom scenario package.

## Languages

The interface supports 23 languages: English (United States), Spanish, Brazilian Portuguese, French, German, Italian, Polish, Russian, Ukrainian, Turkish, Simplified Chinese, Traditional Chinese, Japanese, Korean, Czech, Dutch, Hungarian, Romanian, Swedish, Norwegian Bokmål, Danish, Finnish, and Greek.

English (United States) is the authoritative fallback language.

## Bug reports

GitHub Issues may be used for Mod Manager bug reports and feature requests. For a bug report, include the Mod Manager version, Windows version, what happened, what you expected, and reproduction steps. A sanitized diagnostics ZIP from the Manager can be attached when useful.

**Review diagnostic files before sharing them publicly, and do not upload Castle Miner Z game files or your full game installation to an issue.**

## Third-party software

The distributed Mod Manager includes **Harmony 2.4.2**, licensed under the MIT License. The release package contains the upstream Harmony license and third-party notices.

## Version boundaries

- CastleMiner Z Mod Manager: **v1.2.0**
- CMZ Runtime implementation/file version: **v1.0.1**
- Runtime assembly compatibility identity: **v1.0.0.0**
- Mod-facing Framework compatibility: **v1.0.0**
- CMZ Mod SDK/API: **v1.0.0**
- Harmony: **v2.4.2**
- `.cmzmod` package formats: **1 and 2**
- `.cmztool` package formats: **1 and 2**
- Runtime LaunchPlan: **Format 1**
- Runtime LaunchAuthorization: **Format 1**
- Supported game: **CastleMiner Z 1.9.9.8 — Steam / Windows**

## Release integrity

SHA-256 for `CMZ_Mod_Manager_v1.2.0_Portable.zip`:

`312A44DA4D0EC9C58D84386B160616D8049C3C1F81B7214905E60B0130AED272`

The checksum is also published in [`CMZ_Mod_Manager_v1.2.0_SHA256.txt`](CMZ_Mod_Manager_v1.2.0_SHA256.txt).

## Project status

This repository is the public distribution home for CastleMiner Z Mod Manager releases. Development, builder material, and independently distributed tools are maintained separately and are not included in the public Mod Manager release package.

The public v1.2.0 portable package contains the finished Mod Manager and required runtime/support files only. It contains **no builder/source tree**, **no bundled `.cmzmod` mods**, **no bundled `.cmztool` tools**, and **no bundled `.cmzscenario` scenarios**.

CastleMiner Z Mod Manager is an unofficial community project and is not affiliated with or endorsed by the developers or publisher of CastleMiner Z.
