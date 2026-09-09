# CastleMiner Z Mod Manager v1.2.0

CastleMiner Z Mod Manager v1.2.0 is a startup-orchestration, package-security, compatibility, and theme-hardening release for **CastleMiner Z 1.9.9.8 on Steam for Windows**.

The central addition is a generic Manager-owned startup system for trusted external Tools that need to initialize before CastleMiner Z. The design remains general-purpose: it does not add gameplay-specific hooks or special cases to the Manager, and the existing CMZ Runtime LaunchPlan/API compatibility boundary remains unchanged.

## Generic startup orchestration

v1.2.0 adds deterministic pre-game startup orchestration for compatible Format-2 `.cmztool` packages.

- Startup-capable Tools can declare a `beforeGame` prelaunch phase and readiness protocol 1.
- Required startup Tools can be declared by Format-2 mods.
- Optional startup Tool relationships only participate when the Tool is selected for the active profile.
- Startup-capable Tools may also be selected directly for a profile without changing the existing Profile Format 1 file contract.
- The Manager resolves startup Tools through a separate Manager-owned dependency/order graph.
- Tools start sequentially in deterministic topological order before Steam/CastleMiner Z.
- Required startup failure or readiness timeout blocks game launch and rolls back Manager-started companions before the game is observed.
- Once the matching CastleMiner Z process is observed, later tracking/state-publication failures do not destructively kill game-lifetime companions.
- Framework Only and Launch Clean intentionally bypass startup orchestration.

The startup system is generic and contains no Session Protection-specific or other gameplay-mod-specific Manager code.

## Readiness protocol and startup identity

Startup Tools receive Manager-generated session identity, nonce, readiness-file, startup-plan, data-root, language, and related launch arguments.

A Tool reports readiness by atomically publishing protocol-1 JSON containing the exact startup session ID, Tool ID, nonce, process ID, and ready state. The Manager rejects stale or mismatched readiness data.

For game-lifetime companions, the Manager publishes the observed CastleMiner Z PID/start time into Manager-owned startup state after Steam launches the game.

## Package Format 2 and Tool Format 2

v1.2.0 keeps existing Format-1 packages supported and adds downgrade-safe Format-2 metadata.

### `.cmzmod` Format 2

- Root metadata file: `manifest.v2.json`
- Adds `minimumManagerVersion`, required `prelaunchTools`, and optional `optionalPrelaunchTools` relationships.
- Installed Format-2 manifests are receipt-bound and revalidated before trusted startup use.
- Format-2 payloads cannot hide Manager metadata files such as `manifest.json`, `manifest.v2.json`, or `install-receipt.json` inside payload paths.

### `.cmztool` Format 2

- Root metadata file: `tool.v2.json`
- Adds a required `prelaunch` object for startup-capable Tools.
- Supports deterministic Tool dependencies and startup ordering.
- Automatic startup is restricted to receipt-validated Format-2 Tools.
- The Manager revalidates manifest identity, entry executable identity, and declared payload integrity immediately before automatic execution.

Format-1 `.cmzmod` and `.cmztool` packages remain supported.

## Package and archive hardening

v1.2.0 strengthens package handling without intentionally breaking valid legacy packages.

- External mod and Tool packages are copied into Manager-owned private staging before validation/extraction.
- Package size, payload count, expanded-size, canonical relative-path, reserved metadata, declared-payload, and integrity gates are enforced.
- Installed Format-2 manifests are tied to Manager-generated install receipts.
- Self-dependency, self-ordering, duplicate/contradictory startup requirements, and malformed startup relationships are rejected before Runtime launch.
- Mod and Tool MultiSelect schemas reject blank/duplicate choices, invalid defaults, undeclared defaults, and duplicate defaults.
- Archive discovery uses compact/fallback staging paths to preserve legacy .NET Framework path-length headroom.
- Overlong archive entries are converted into a specific safe rejection rather than surfacing as an uncontrolled path error.

### Legacy backslash ZIP compatibility fix

The final Rev41 FIX6 build corrects an installer regression affecting valid legacy Format-1 packages whose ZIP entries use backslash separators such as `payload\\...`.

Validation and transactional extraction now use the same canonical archive-entry normalization contract. Existing Format-1 `.cmzmod` and `.cmztool` packages using backslash ZIP payload separators are normalized consistently instead of validating successfully and then losing their payload during extraction.

Dedicated mod and Tool regression fixtures cover this compatibility path.

## Theme and contrast hardening

v1.2.0 expands the Manager-owned WPF theme contract so newer controls do not fall back to incompatible stock Windows surfaces.

Explicit Manager theme coverage now includes:

- RadioButton
- TabControl / TabItem
- Expander
- ProgressBar
- ScrollBar
- ToolTip

Existing Manager-owned styling for TextBlock, Button, TextBox, ComboBox, ComboBoxItem, CheckBox, ListBox, and ListBoxItem remains in place.

Additional theme changes:

- Theme switching replaces only the Manager theme dictionary instead of clearing unrelated application resources.
- System `WindowBrush` maps to `WindowBackground` rather than `InputBackground`.
- First-run language selection appears after baseline theming is active.
- Derived semantic text resources target at least **4.5:1** normal-text contrast across working surfaces and **3:1** for disabled text.
- Existing built-in and custom Theme Format 1 palette files do not require new keys for these readable semantic colors.

## Session and diagnostics truthfulness

- Runtime cleanup reaching `CastleMinerZGame.OnExiting` is no longer treated as proof that the game completed normally.
- The Manager reports **Runtime Cleanup Completed - Exit Cause Unverified** when cleanup is observed without stronger independent exit evidence.
- Diagnostics include sanitized startup plan/profile state and canonical Format-2 manifest metadata while preserving existing privacy boundaries.
- One-use Runtime launch authorization remains Format 1 and is not issued by failed prelaunch startup orchestration.

## Localization

The Manager still includes **23 UI languages** with English (United States) as the authoritative fallback.

v1.2.0 expands the localization contract to cover the startup orchestration, security, status, and related UI introduced by this release while maintaining complete key/placeholder parity across all bundled languages.

## v1.2.0 release identity and packaging

- Mod Manager product version: **1.2.0**
- Assembly version: **1.2.0.0**
- File version: **1.2.0.0**
- Informational version: **1.2.0**
- Portable output name: `CMZ_Mod_Manager_v1.2.0_Portable.zip`
- Public portable package contains no builder/source tree and no bundled `.cmzmod`, `.cmztool`, or `.cmzscenario` packages.

The generated portable package includes `BUILD_VERIFICATION.txt` and `OUTPUT_MANIFEST.txt`. Automatic build/regression verification passed for the final Rev41 FIX6 package, including startup orchestration, package/tool regression, theme contract, frozen Runtime/SDK integrity baselines, Harmony validation, baseline validation, localization parity, and release-boundary checks.

Automatic regression verification is not a blanket guarantee of every third-party startup Tool or every Windows visual configuration; third-party Tools remain separate executable programs and must be trusted and tested by their authors/users.

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

The Manager version and Manager-owned package/startup capabilities changed in v1.2.0. The frozen Runtime implementation, SDK/API, Runtime LaunchPlan, and mod-facing Framework/API compatibility boundaries did not change.

## Download

Download **`CMZ_Mod_Manager_v1.2.0_Portable.zip`** from this release's **Assets** section.

Do not use GitHub's automatically generated **Source code (zip)** or **Source code (tar.gz)** archives as the Mod Manager download.

## License and extension ecosystem

The v1.2.0 portable package contains the **CastleMiner Z Mod Manager Community Use and Extension License v1.0** distributed with that package.

The repository's current `main` branch is governed by the terms in [`LICENSE.md`](LICENSE.md). Changing repository terms does not retroactively replace the license text already distributed inside a packaged release.

Users may create independently authored compatible mods, tools, custom themes, translations, configurations, presets, profiles, and other supported extensions subject to the applicable terms and third-party rights.

## Privacy and third-party code

CastleMiner Z Mod Manager does not include first-party telemetry or automatic network-upload functionality.

Diagnostic exports redact common local paths, Steam64 IDs, and custom Manager profile names; third-party mod logs are not included automatically. Review diagnostic files before sharing them publicly.

Enabled runtime mods execute third-party code inside CastleMiner Z. Installed Tools execute as separate third-party processes. Neither is sandboxed. Startup-capable Tools can execute automatically before a modded game launch when the active profile requires/selects them, so only install startup Tools from sources you trust.

Package validation, install receipts, and integrity checks do not establish that third-party code is safe or trustworthy.

## Windows security notice

Castle Miner Z Mod Manager is distributed without a paid Authenticode certificate. Windows may therefore show an **Unknown publisher** or Microsoft Defender SmartScreen warning for a new download.

Obtain the package from this official repository. Do not disable Windows Security or antivirus protection just to run the Mod Manager.

## Distribution contents

The public v1.2.0 portable package contains the Mod Manager, CMZ Runtime/SDK framework components, Harmony 2.4.2, the trusted CastleMiner Z 1.9.9.8 validation baseline, 23 localization resources, themes, application assets, the packaged Manager license, build/output verification metadata, and required third-party license notices.

It contains **no bundled gameplay mods (`.cmzmod`)**, **no bundled tools (`.cmztool`)**, **no custom scenario packages (`.cmzscenario`)**, **no World Builder implementation**, and **no builder/source tree**.
