# CastleMiner Z Mod Manager

A general-purpose mod manager and modding framework for **CastleMiner Z 1.9.9.8 on Steam for Windows**.

CastleMiner Z Mod Manager provides mod package management, profiles, compatibility/dependency resolution, clean and modded launch modes, game-file validation and repair, diagnostics, multilingual UI support, themes, reusable per-mod settings, and a generic Tools system for independently distributed `.cmztool` utilities.

> **Current version:** v1.1.3  
> The ready-to-use package is `CMZ_Mod_Manager_v1.1.3_Portable.zip`. Download it from the **v1.1.3 GitHub Release**. Do not use GitHub's automatically generated source-code archives as the Mod Manager download.

## What's new in v1.1.3

v1.1.3 is a reliability and release-hardening update that preserves the v1.1.2 feature set while resolving issues found during later Windows runtime testing.

- Hardens Windows title-bar/taskbar icon handling and the packaged multi-size `.ico`
- Uses the canonical high-resolution icon at WPF and native window layers with normal system-assigned portable application identity
- Corrects native icon-handle lifetime management
- Adds `ManagerIcon.log` diagnostics for future icon troubleshooting
- Fixes Launch Clean post-session restoration so unavailable `Process.ExitCode` data cannot interrupt framework restoration
- Records **Process Exited — Exit Code Unavailable** when Windows does not expose an exit code to the Manager
- Records when the previous framework was restored after a Clean session
- Updates all current Manager product/assembly/file/informational identity to **v1.1.3**
- Includes the CastleMiner Z Mod Manager Community Use and Extension License v1.0 in the finished portable package
- Strengthens final package checks for version identity, required icon/license files, release boundaries, and release-only contents

**Runtime verified on Windows:** Launch Clean restored the framework successfully; tested official mods worked in a normal modded session; the independently distributed World Builder tool worked as intended; and the unpinned taskbar icon remained correct across repeated launches and after a full shutdown/reboot.

The CMZ Runtime implementation/file version remains **v1.0.1** while its assembly compatibility identity and mod-facing Framework compatibility remain **v1.0.0**. The CMZ Mod SDK/API remains **v1.0.0**.

See [`RELEASE_NOTES_v1.1.3.md`](RELEASE_NOTES_v1.1.3.md) for full details.

## Features

- Install and manage `.cmzmod` packages
- Multiple mod profiles
- Dependency and compatibility resolution
- Reusable per-mod settings, including boolean, integer, decimal, text, choice, and multi-select controls
- Launch CastleMiner Z with the active mod profile
- Launch the game clean without the framework/mods
- Validate CastleMiner Z 1.9.9.8 game files
- Repair missing or modified game files from a configured clean backup
- General-purpose CMZ Runtime and Mod SDK framework
- Install and manage independently distributed `.cmztool` utilities from the **Tools** page
- 23 interface languages
- Built-in light, dark, system, and CastleMiner Z material themes
- Custom theme support
- Diagnostics, recovery, and session history tools

## Installation

1. Open **Releases** and download `CMZ_Mod_Manager_v1.1.3_Portable.zip` from the **v1.1.3** release.
2. Extract the ZIP to a permanent folder of your choice.
3. Run `CMZModManager.exe`.
4. Choose your language on first launch.
5. Select your CastleMiner Z installation folder if it is not detected automatically.
6. Follow the Mod Manager's framework setup/update prompts.

The Manager supports the **CastleMiner Z 1.9.9.8 Steam/Windows** release.

## License, extensions, and responsible use

CastleMiner Z Mod Manager itself is **proprietary software**. The community is expressly permitted to use the official Manager normally and to create and distribute original extensions through its supported extension mechanisms.

Permitted community content includes, but is not limited to:

- `.cmzmod` gameplay mods
- `.cmztool` utilities
- custom themes
- translations and localization resources
- configurations, presets, and shareable profiles
- integrations and other extensions using documented public APIs, SDK interfaces, schemas, package formats, or theme formats

Extension authors retain ownership of their own original work, subject to any third-party rights involved. Compatible projects may truthfully state that they are made for, compatible with, or require CastleMiner Z Mod Manager.

The Mod Manager itself may not be repackaged, rebranded, redistributed, sold, or published as a modified/derivative Manager without permission. Users should link others to an official distribution location rather than reuploading the Manager.

The project is intended for legitimate modding. It must not be used to deliberately attack, crash, exploit, corrupt, impersonate, or otherwise harm other players, hosts, systems, or multiplayer sessions. Legitimate single-player use, consensual multiplayer modifications, host customization, accessibility work, debugging, interoperability, and good-faith security research remain permitted within the terms of the license.

See [`LICENSE.md`](LICENSE.md) for the complete **CastleMiner Z Mod Manager Community Use and Extension License v1.0**.

## Privacy and trust

CastleMiner Z Mod Manager does not include first-party telemetry or analytics. Diagnostic exports redact common local paths, Steam64 IDs, and custom Manager profile names, and third-party mod logs are not included automatically in the standard diagnostics ZIP.

Diagnostic sanitization is intended to reduce accidental disclosure, not to make arbitrary files safe to publish without review.

Enabled runtime mods execute third-party code inside CastleMiner Z. Installed Tools execute as separate third-party processes. Neither is sandboxed. Only install packages from authors you trust. Package validation and hashes verify package integrity; they do not prove that third-party code is trustworthy.

## Windows security notice

CastleMiner Z Mod Manager is distributed without a paid Authenticode code-signing certificate. Windows may therefore show **Unknown publisher** or a Microsoft Defender SmartScreen warning for a new download.

Download releases only from this official repository and verify the published SHA-256 checksum when desired. You should not need to disable Windows Security or antivirus protection to use the Mod Manager.

## Tools

The **Tools** page installs and manages independent format-1 `.cmztool` packages. Tools are built, versioned, tested, and distributed separately from the Mod Manager.

Updating a tool does not require rebuilding `CMZModManager.exe`, and updating the Mod Manager does not intentionally replace installed Tools or ToolData. ToolData is stored separately from installed tool binaries and is preserved by default during normal update/uninstall workflows.

The Mod Manager portable release does **not** bundle a World Builder, other tool implementation, `.cmztool` package, gameplay mod, or custom scenario package.

## Languages

The interface supports 23 languages: English (United States), Spanish, Brazilian Portuguese, French, German, Italian, Polish, Russian, Ukrainian, Turkish, Simplified Chinese, Traditional Chinese, Japanese, Korean, Czech, Dutch, Hungarian, Romanian, Swedish, Norwegian Bokmål, Danish, Finnish, and Greek.

English (United States) is the authoritative fallback language.

## Bug reports

GitHub Issues may be used for Mod Manager bug reports and feature requests. For a bug report, include the Mod Manager version, Windows version, what happened, what you expected, and reproduction steps. A sanitized diagnostics ZIP from the Manager can be attached when useful.

**Review diagnostic files before sharing them publicly, and do not upload CastleMiner Z game files or your full game installation to an issue.**

## Third-party software

The distributed Mod Manager includes **Harmony 2.4.2**, licensed under the MIT License. The release package contains the upstream Harmony license and third-party notices.

## Version boundaries

- CastleMiner Z Mod Manager: **v1.1.3**
- CMZ Runtime implementation/file version: **v1.0.1**
- Runtime assembly compatibility identity: **v1.0.0.0**
- Mod-facing Framework compatibility: **v1.0.0**
- CMZ Mod SDK/API: **v1.0.0**
- Harmony: **v2.4.2**
- `.cmztool` package format: **1**
- Supported game: **CastleMiner Z 1.9.9.8 — Steam / Windows**

## Release integrity

SHA-256 for `CMZ_Mod_Manager_v1.1.3_Portable.zip`:

`B0267A8D85375E3485EA4A0E2CCB671212F7A8A35B16D7074E932354165F0E05`

The checksum is also published in [`CMZ_Mod_Manager_v1.1.3_SHA256.txt`](CMZ_Mod_Manager_v1.1.3_SHA256.txt).

## Project status

This repository is the public distribution home for CastleMiner Z Mod Manager releases. Development, builder material, and independently distributed tools are maintained separately and are not included in the public Mod Manager release package.

The public v1.1.3 portable package contains the finished Mod Manager and required runtime/support files only. It contains **no builder/source tree**, **no bundled `.cmzmod` mods**, **no bundled `.cmztool` tools**, and **no bundled `.cmzscenario` scenarios**.

CastleMiner Z Mod Manager is an unofficial community project and is not affiliated with or endorsed by the developers or publisher of CastleMiner Z.
