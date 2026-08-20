# CastleMiner Z Mod Manager

A general-purpose mod manager and modding framework for **CastleMiner Z 1.9.9.8 on Steam for Windows**.

CastleMiner Z Mod Manager provides mod package management, profiles, compatibility/dependency resolution, clean and modded launch modes, game-file validation and repair, diagnostics, multilingual UI support, themes, per-mod settings, and an integrated CastleMiner Z World Builder.

> **Current version:** v1.1.1  
> The ready-to-use package is `CMZ_Mod_Manager_v1.1.1_Portable.zip`. Download it from the **v1.1.1 GitHub Release**. Do not use GitHub's automatically generated source-code archives as the Mod Manager download.

## What's new in v1.1.1

v1.1.1 expands the Mod Manager's reusable per-mod settings support and improves the layout for mods with larger option sets.

- Adds a generic `multiselect` setting type to **Mods > Settings**
- Stores multi-select values as validated JSON arrays
- Provides **Select All** and **Clear List** controls
- Uses a compact single-column layout for small lists, two columns for 10–24 choices, and three columns for 25 or more choices
- Displays up to 36 choices without an inner scrollbar; larger lists use a bounded internal scrollbar
- Expands and bounds the Mod Settings dialog to the current desktop work area
- Preserves compatibility with existing boolean, integer, decimal, text, and choice settings
- Keeps launch/bootstrap/networking behavior unchanged

The CMZ Runtime and Mod SDK remain at **v1.0.0** because their implementation did not change. The integrated CastleMiner Z World Builder remains at **v1.0.1**.

See [`RELEASE_NOTES_v1.1.1.md`](RELEASE_NOTES_v1.1.1.md) for details.

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
- Integrated CastleMiner Z World Builder
- Import and use `.cmzscenario` packages
- 23 interface languages
- Built-in light, dark, system, and CastleMiner Z material themes
- Diagnostics, recovery, and session history tools

## Installation

1. Open **Releases** and download `CMZ_Mod_Manager_v1.1.1_Portable.zip` from the **v1.1.1** release.
2. Extract the ZIP to a permanent folder of your choice.
3. Run `CMZModManager.exe`.
4. Choose your language on first launch.
5. Select your CastleMiner Z installation folder if it is not detected automatically.
6. Follow the Mod Manager's framework setup prompts.

The Manager supports the **CastleMiner Z 1.9.9.8 Steam/Windows** release.

## Privacy and trust

CastleMiner Z Mod Manager does not include first-party telemetry or analytics. Privacy hardening introduced in v1.0.1 remains part of v1.1.1, including reduced exposure of local identifiers in normal UI and sanitization of information included in Manager-generated diagnostic exports.

Diagnostic sanitization is intended to reduce accidental disclosure, not to make arbitrary files safe to publish without review. In particular, third-party mod logs are not automatically bundled into the standard diagnostics ZIP.

Runtime mods and custom scenario generators are executable third-party code and are **not sandboxed**. Only install mods and scenario packages from authors you trust. Package integrity checks verify package contents and hashes; they do not prove that third-party code is trustworthy.

## Windows security notice

CastleMiner Z Mod Manager is distributed without a paid Authenticode code-signing certificate. Windows may therefore show **Unknown publisher** or a Microsoft Defender SmartScreen warning for a new download.

Download releases only from this official repository and verify the published SHA-256 checksum when desired. You should not need to disable Windows Security or antivirus protection to use the Mod Manager.

## World Builder

The World Builder is integrated directly into the Mod Manager under **Tools**. It can create normal CastleMiner Z worlds and can import trusted `.cmzscenario` packages obtained separately.

The Mod Manager release does **not** bundle gameplay mods or custom scenario packages.

## Languages

The interface supports 23 languages: English (United States), Spanish, Brazilian Portuguese, French, German, Italian, Polish, Russian, Ukrainian, Turkish, Simplified Chinese, Traditional Chinese, Japanese, Korean, Czech, Dutch, Hungarian, Romanian, Swedish, Norwegian Bokmål, Danish, Finnish, and Greek.

English (United States) is the fallback language.

## Bug reports

GitHub Issues may be used for Mod Manager bug reports and feature requests. For a bug report, include the Mod Manager version, Windows version, what happened, what you expected, and reproduction steps. A sanitized diagnostics ZIP from the Manager can be attached when useful.

**Review diagnostic files before sharing them publicly, and do not upload CastleMiner Z game files or your full game installation to an issue.**

## Third-party software

The distributed Mod Manager includes **Harmony 2.4.2**, licensed under the MIT License. The release package contains the upstream Harmony license and third-party notices.

## Project status

This repository is the public distribution home for CastleMiner Z Mod Manager releases. Development and builder material is maintained separately and is not included in the public release package.

CastleMiner Z Mod Manager is an unofficial community project and is not affiliated with or endorsed by the developers or publisher of CastleMiner Z.
