# CastleMiner Z Mod Manager v1.1.3

CastleMiner Z Mod Manager v1.1.3 is a reliability and release-hardening update for **CastleMiner Z 1.9.9.8 on Steam for Windows**.

This release keeps the v1.1.2 Tools architecture, diagnostics, profiles, settings, localization, validation/repair, package-management, and framework behavior while fixing two release-critical issues found during later testing: Windows taskbar icon instability and Launch Clean framework restoration failure after game exit.

## Windows taskbar and application icon stability

- Hardens the Windows application-icon path used by `CMZModManager.exe`.
- Uses the corrected multi-size `.ico` layout: native uncompressed 32-bit Windows DIB frames for 16, 20, 24, 32, 40, 48, 64, and 128 px, with the 256 px frame PNG-compressed.
- Uses the canonical high-resolution icon at the WPF and native HWND layers so Windows can scale it correctly for title bar, Alt+Tab, and taskbar use.
- Uses normal system-assigned portable application identity instead of forcing a custom AppUserModelID.
- Keeps native icon handles alive for the lifetime of the window and releases them safely during shutdown.
- Adds icon diagnostics through `ManagerIcon.log` for future troubleshooting.
- Builder/output validation requires the canonical `.ico` and rejects invalid small-icon packaging.

**Runtime verified on Windows:** the running unpinned taskbar icon remained correct across repeated Manager launches and after a full Windows shutdown and reboot.

## Launch Clean post-session restoration fix

- Fixes a failure where a successful Clean session could end with `Process.ExitCode` throwing `InvalidOperationException` because the observed CastleMiner Z process was not started by that `Process` object.
- Framework restoration now occurs **before** optional exit-code retrieval.
- Exit-code retrieval is telemetry only and can no longer prevent restoration of the previous framework state.
- `InvalidOperationException` and `NotSupportedException` from exit-code retrieval are handled safely.
- Clean sessions can now record **Process Exited — Exit Code Unavailable** when Windows does not expose an exit code to the Manager.
- Session history records when the previous framework was restored after a Clean session.

**Runtime verified on Windows:** after Launch Clean and normal CastleMiner Z exit, the framework returned to **Installed**, Launch Game became available again, and the Manager recorded the clean session without the former restoration interruption.

## v1.1.3 release identity and packaging

- Mod Manager product version: **1.1.3**
- Assembly version: **1.1.3.0**
- File version: **1.1.3.0**
- Informational version: **1.1.3**
- Portable output name: `CMZ_Mod_Manager_v1.1.3_Portable.zip`
- Adds the CastleMiner Z Mod Manager Community Use and Extension License v1.0 to the finished portable distribution.
- Strengthens final output validation for version identity, icon presence, license presence, package boundaries, hashes, and release-only contents.
- The public portable package contains no builder/source tree and no bundled `.cmzmod`, `.cmztool`, or `.cmzscenario` packages.

## Runtime acceptance testing

The release candidate was tested in actual CastleMiner Z runtime on Windows.

Verified during release testing:

- Launch Clean completed and restored the previous framework state.
- Modded launch completed normally.
- The tested official CastleMiner Z mods loaded and worked as intended.
- A modded session reached `CastleMinerZGame.OnExiting` and Runtime `ShutdownComplete` without reported cleanup errors.
- The independently distributed CastleMiner Z World Builder tool launched through the Manager and worked as intended.
- The Windows taskbar icon remained correct after full shutdown and reboot.

These tests verify the release candidate and the tested first-party content. They do not guarantee compatibility or safety of every third-party mod or tool.

## Retained v1.1.2 functionality

v1.1.3 retains the major v1.1.2 features, including:

- generic format-1 `.cmztool` package management;
- separate installed Tools and ToolData storage;
- tool running-state protection during update/reinstall/downgrade/uninstall;
- Mods/Tools UI alignment and navigation improvements;
- fixed-shell Diagnostics layout;
- one-use launch authorization tied to the current CastleMiner Z process;
- structured Runtime shutdown/session classification;
- Core Game Files Verified vs authoritative 948-file Clean Install Verified distinction;
- staged/atomic critical writes;
- game-file mutation blocking while CastleMiner Z is running;
- v1.1.1 framework recognition as Framework Update Required;
- multi-select mod settings;
- 23 interface languages;
- built-in themes and custom-theme support;
- profiles, compatibility/dependency resolution, diagnostics, recovery, and session history.

## Version boundaries

- CastleMiner Z Mod Manager: **v1.1.3**
- CMZ Runtime implementation/file version: **v1.0.1**
- Runtime assembly compatibility identity: **v1.0.0.0**
- Mod-facing Framework compatibility: **v1.0.0**
- CMZ Mod SDK/API: **v1.0.0**
- Harmony: **v2.4.2**
- `.cmztool` package format: **1**
- Supported game: **CastleMiner Z 1.9.9.8 — Steam / Windows**

The Manager version changed to v1.1.3. The Runtime/API compatibility boundaries did not change.

## Download

Download **`CMZ_Mod_Manager_v1.1.3_Portable.zip`** from this release's **Assets** section.

Do not use GitHub's automatically generated **Source code (zip)** or **Source code (tar.gz)** archives as the Mod Manager download.

## Integrity

SHA-256 for `CMZ_Mod_Manager_v1.1.3_Portable.zip`:

`B0267A8D85375E3485EA4A0E2CCB671212F7A8A35B16D7074E932354165F0E05`

The same checksum is published in [`CMZ_Mod_Manager_v1.1.3_SHA256.txt`](CMZ_Mod_Manager_v1.1.3_SHA256.txt).

## License and extension ecosystem

CastleMiner Z Mod Manager itself remains proprietary under the **CastleMiner Z Mod Manager Community Use and Extension License v1.0**.

Users may use the official Manager normally and create/distribute original compatible mods, tools, custom themes, translations, configurations, presets, profiles, and other supported extensions. Extension authors retain ownership of their own original work, subject to third-party rights.

The Manager itself may not be repackaged, rebranded, redistributed, sold, or published as a modified/derivative Manager without permission. Malicious or non-consensual multiplayer abuse is outside the permitted use of the project.

See [`LICENSE.md`](LICENSE.md) for the complete terms.

## Privacy and third-party code

CastleMiner Z Mod Manager does not include first-party telemetry or automatic network-upload functionality.

Diagnostic exports redact common local paths, Steam64 IDs, and custom Manager profile names; third-party mod logs are not included automatically. Review diagnostic files before sharing them publicly.

Enabled runtime mods execute third-party code inside CastleMiner Z. Installed Tools execute as separate third-party processes. Neither is sandboxed. Only install packages from authors you trust. Package validation and hashes verify integrity; they do not establish that third-party code is safe or trustworthy.

## Windows security notice

CastleMiner Z Mod Manager is distributed without a paid Authenticode certificate. Windows may therefore show an **Unknown publisher** or Microsoft Defender SmartScreen warning for a new download.

Obtain the package from this official repository and verify the SHA-256 checksum when desired. Do not disable Windows Security or antivirus protection just to run the Mod Manager.

## Distribution contents

The public v1.1.3 portable package contains the Mod Manager, CMZ Runtime/SDK framework components, Harmony 2.4.2, the trusted CastleMiner Z 1.9.9.8 validation baseline, 23 localization resources, themes, application assets, the Manager license, build/output verification metadata, and required third-party license notices.

It contains **no bundled gameplay mods (`.cmzmod`)**, **no bundled tools (`.cmztool`)**, **no custom scenario packages (`.cmzscenario`)**, **no World Builder implementation**, and **no builder/source tree**.
