# CastleMiner Z Mod Manager

A general-purpose mod manager and modding framework for **CastleMiner Z 1.9.9.8 on Steam for Windows**.

CastleMiner Z Mod Manager provides mod package management, profiles, compatibility/dependency resolution, clean and modded launch modes, game-file validation and repair, diagnostics, multilingual UI support, themes, and an integrated CastleMiner Z World Builder.

> **Current release:** v1.0.0  
> Download the ready-to-use portable package from the repository's **Releases** section. Use `CMZ_Mod_Manager_v1.0.0.zip` — not GitHub's automatically generated source-code archives.

## Features

- Install and manage `.cmzmod` packages
- Multiple mod profiles
- Dependency and compatibility resolution
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

1. Open **Releases** and download `CMZ_Mod_Manager_v1.0.0.zip`.
2. Extract the ZIP to a permanent folder of your choice.
3. Run `CMZModManager.exe`.
4. Choose your language on first launch.
5. Select your CastleMiner Z installation folder if it is not detected automatically.
6. Follow the Mod Manager's framework setup prompts.

The Manager expects the supported **CastleMiner Z 1.9.9.8 Steam/Windows** release.

## Windows security notice

CastleMiner Z Mod Manager is currently distributed without a paid Authenticode code-signing certificate. Windows may therefore show **Unknown publisher** or a Microsoft Defender SmartScreen warning for a new download.

Download releases only from this official repository and verify the published SHA-256 checksum when desired. You should not need to disable Windows Security or antivirus protection to use the Mod Manager.

## World Builder

The World Builder is integrated directly into the Mod Manager under **Tools**. It can create normal CastleMiner Z worlds and can import trusted `.cmzscenario` packages obtained separately.

The Mod Manager release does **not** bundle gameplay mods or custom scenario packages.

## Languages

The interface currently supports 23 languages, including English (United States), Spanish, Brazilian Portuguese, French, German, Italian, Polish, Russian, Ukrainian, Turkish, Simplified Chinese, Traditional Chinese, Japanese, Korean, Czech, Dutch, Hungarian, Romanian, Swedish, Norwegian Bokmål, Danish, Finnish, and Greek.

English (United States) is the fallback language.

## Bug reports

GitHub Issues may be used for Mod Manager bug reports and feature requests. For a bug report, include the Mod Manager version, Windows version, what happened, what you expected, and reproduction steps. A sanitized diagnostics ZIP from the Manager can be attached when useful.

**Do not upload CastleMiner Z game files or your full game installation to an issue.**

## Third-party software

The distributed Mod Manager includes **Harmony 2.4.2**, licensed under the MIT License. The release package contains the upstream Harmony license and third-party notices.

## Project status

This repository is the public distribution home for release-ready CastleMiner Z Mod Manager builds. Development/build-system material is maintained separately and is not included in the public release package.

CastleMiner Z Mod Manager is an unofficial community project and is not affiliated with or endorsed by the developers or publisher of CastleMiner Z.
