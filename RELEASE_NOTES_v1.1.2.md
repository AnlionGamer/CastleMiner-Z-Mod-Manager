# CastleMiner Z Mod Manager v1.1.2

CastleMiner Z Mod Manager v1.1.2 is a stability, diagnostics, launch-state, Windows application-identity/icon, and generic tool-architecture release for **CastleMiner Z 1.9.9.8 on Steam for Windows**.

## Windows application icon fix

- Corrects the Windows `.ico` resource layout used by `CMZModManager.exe`.
- Native 16, 20, 24, 32, 40, 48, 64, and 128 px icon frames use uncompressed 32-bit Windows DIB data; the 256 px frame uses PNG compression.
- The Manager explicitly applies the embedded executable icon to the native WPF window for both large and small window/taskbar icon slots.
- Adds the stable Windows AppUserModelID `AnlionGamer.CastleMinerZ.ModManager`.
- Builder validation now rejects the prior all-PNG small-icon layout so the packaging regression cannot silently return.
- Runtime testing on Windows confirmed that the corrected build restores the expected CastleMiner Z Mod Manager icon for the running application/taskbar entry.

## Generic Tools architecture

- Adds format-1 `.cmztool` packages as the standard package format for independent utilities.
- The **Tools** page provides generic Install, Open, Details, Settings, Open Tool Data, update/downgrade, and Uninstall workflows according to each package's declared capabilities.
- Tool packages are copied into Manager-owned staging and validated before transactional installation.
- Installed tool binaries and ToolData are stored separately.
- ToolData is preserved by default across normal tool updates and can be preserved during uninstall.
- Running tools cannot be updated, reinstalled, downgraded, or uninstalled until the declared tool process closes.
- Manager-launched tools are observed until process exit; closing a tool automatically refreshes its card from **Running** to **Ready** and re-enables applicable actions.
- Tool updates do not require rebuilding `CMZModManager.exe`, and Mod Manager updates do not intentionally replace installed Tools or ToolData.

No specific tool source, tool builder, tool executable, or prebuilt `.cmztool` package is part of the v1.1.2 Mod Manager distribution.

## Tools and navigation UI

- The Tools toolbar now follows the same proportions as Mods, including the primary install action, explicit search label, fixed-width search field, and matching margins.
- Tool cards use the same title/status typography, action-column width, and card spacing as mod cards.
- **Profiles** now appears directly above **Mods** in the left navigation.

Navigation order:

1. Home
2. Profiles
3. Mods
4. Tools
5. Sessions
6. Diagnostics
7. Settings

## Diagnostics layout

- The Diagnostics title, subtitle, action buttons, and privacy notice remain fixed in the page shell.
- Only the diagnostic text area scrolls vertically/horizontally.
- Resizing the Manager changes the diagnostics viewport instead of making the entire Diagnostics page scroll.

## Launch and shutdown correctness

- One-use launch authorization is bound to the observed `CastleMinerZ.exe` process.
- A prior Manager-authorized launch cannot be reused by a later direct Steam launch.
- Direct Steam launches remain passive when no valid current Manager authorization exists.
- Runtime shutdown uses structured state instead of treating `SHUTDOWN_BEGIN` as successful completion.
- ProcessExit fallback alone is not classified as a normal `CastleMinerZGame.OnExiting` shutdown.
- Runtime failures, cleanup failures, abnormal exits, and graceful shutdown completion remain distinguishable in session/diagnostic state.

## Validation, repair, and state safety

- Quick verification is labeled **Core Game Files Verified**.
- Full **Clean Install Verified** status remains reserved for the authoritative 948-file CastleMiner Z 1.9.9.8 baseline and required original empty folder structure.
- Critical state, configuration, and repair writes use safer staged or atomic replacement patterns.
- File-mutating operations are blocked while the selected CastleMiner Z process is running.
- Existing first-party v1.1.1 framework installs are recognized as **Framework Update Required** instead of being treated as unknown corruption.
- Existing mods, profiles, mod Data/Config, themes, Tools/ToolData, Manager settings, and session history are intended to remain preserved through the framework/Manager update workflow.

## Retained functionality

v1.1.2 retains the v1.1.1 generic multi-select mod-setting support, including validated JSON-array storage, Select All/Clear List controls, adaptive multi-column layout, and compatibility with existing boolean, integer, decimal, text, and choice settings.

It also retains the privacy, localization, theme, package-integrity, diagnostics-export, clean-launch, validation, repair, profile, compatibility-resolution, and progress-UI work from earlier public releases.

## Version boundaries

- CastleMiner Z Mod Manager: **v1.1.2**
- CMZ Runtime implementation/file version: **v1.0.1**
- Runtime assembly compatibility identity: **v1.0.0.0**
- Mod-facing Framework compatibility: **v1.0.0**
- CMZ Mod SDK/API: **v1.0.0**
- Harmony: **v2.4.2**
- `.cmztool` package format: **1**
- Supported game: **CastleMiner Z 1.9.9.8 — Steam / Windows**

The runtime implementation changed while its compatibility identity remains 1.0.0.0 and the mod-facing Framework/API compatibility remains v1.0.0.

## Download

Download **`CMZ_Mod_Manager_v1.1.2_Portable.zip`** from the v1.1.2 release's Assets section.

Do not use GitHub's automatically generated **Source code (zip)** or **Source code (tar.gz)** archives as the Mod Manager download.

## Integrity

SHA-256 for `CMZ_Mod_Manager_v1.1.2_Portable.zip`:

`FA651EE623905B6AAC14476283975D7CF0EBB3F747C11976DB810B98A0A69FC1`

The same checksum is published in [`CMZ_Mod_Manager_v1.1.2_SHA256.txt`](CMZ_Mod_Manager_v1.1.2_SHA256.txt).

## Privacy and third-party code

CastleMiner Z Mod Manager does not include first-party telemetry or automatic network-upload functionality.

Diagnostic exports redact common local paths, Steam64 IDs, and custom Manager profile names; third-party mod logs are not included automatically. Review diagnostic files before sharing them publicly.

Enabled runtime mods execute third-party code inside CastleMiner Z. Installed Tools execute as separate third-party processes. Neither is sandboxed. Only install packages from authors you trust. Package validation and hashes verify integrity; they do not establish that third-party code is safe or trustworthy.

## Windows security notice

CastleMiner Z Mod Manager is distributed without a paid Authenticode certificate. Windows may therefore show an **Unknown publisher** or Microsoft Defender SmartScreen warning for a new download.

Obtain the package from this official repository and verify the SHA-256 checksum when desired. Do not disable Windows Security or antivirus protection just to run the Mod Manager.

## Distribution contents

The public v1.1.2 portable package contains the Mod Manager, CMZ Runtime/SDK framework components, Harmony 2.4.2, the trusted CastleMiner Z 1.9.9.8 validation baseline, 23 localization resources, themes, application assets, build/output verification metadata, and required third-party license notices.

It contains **no bundled gameplay mods (`.cmzmod`)**, **no bundled tools (`.cmztool`)**, **no custom scenario packages (`.cmzscenario`)**, **no World Builder implementation**, and **no builder/source tree**.

## Validation boundary

The supplied portable package includes builder-generated verification indicating that compilation and isolated Manager/tool/package regression gates passed. Those checks are not equivalent to real CastleMiner Z runtime/gameplay testing. Real game and external-tool runtime validation remains a separate release gate.
