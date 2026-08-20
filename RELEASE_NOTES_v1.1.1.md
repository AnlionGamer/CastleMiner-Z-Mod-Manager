# CastleMiner Z Mod Manager v1.1.1

CastleMiner Z Mod Manager v1.1.1 adds reusable multi-select mod settings and improves the Mod Settings layout for larger option sets while preserving the existing runtime, SDK, World Builder, launch, and networking behavior.

## Multi-select mod settings

- Adds a generic `multiselect` setting type to the existing **Mods > Settings** dialog.
- Multi-select values are stored as JSON arrays.
- Saved values are normalized against the choices declared by the mod.
- Duplicate selections are removed and stale/undeclared saved choices are ignored.
- Package validation rejects invalid multi-select schemas, including empty/duplicate declared choices and undeclared default values.
- **Select All** and **Clear List** controls are included.
- Existing boolean, integer, decimal, text, and single-choice settings remain compatible.

## Mod Settings layout

- Fewer than 10 choices use a single-column checklist.
- 10–24 choices use a two-column checklist.
- 25 or more choices use a three-column checklist.
- Up to 36 choices are shown without an inner scrollbar.
- Larger choice sets use a bounded internal scrollbar.
- The Mod Settings dialog is larger and bounded to the current desktop work area.

These layout changes are intended to keep normal-sized option sets readable without forcing awkward nested scrolling.

## Version boundaries

- CastleMiner Z Mod Manager: **v1.1.1**
- Integrated CastleMiner Z World Builder: **v1.0.1**
- CMZ Runtime: **v1.0.0**
- CMZ Mod SDK/API: **v1.0.0**
- Harmony: **v2.4.2**
- Supported game: **CastleMiner Z 1.9.9.8 — Steam / Windows**

The Runtime and Mod SDK remain at v1.0.0 because their source implementation is unchanged from v1.0.1. The integrated World Builder remains at v1.0.1. Launch/bootstrap/networking behavior is intentionally unchanged in this release.

## Included v1.0.1 improvements

v1.1.1 retains the privacy, localization, UI, validation, repair, theme, and integrated World Builder improvements from v1.0.1, including:

- Steam64 IDs hidden from normal World Builder profile/success UI
- Privacy-safe local path display and sanitized diagnostic exports
- Third-party mod logs excluded from standard diagnostic ZIPs
- Neutral exported profile filenames and bounded session-history export
- Cleanup/pruning of custom-scenario protocol job records
- 23 bundled interface languages with English (United States) fallback
- Integrated World Builder under **Tools**
- Fixed-footer mod install/update dialogs for long package details
- ComboBox dropdown-arrow hover/focus styling aligned with the surrounding control
- CastleMiner Z material themes using locally extracted installed-game material textures without bundling game artwork

## Download

Download **`CMZ_Mod_Manager_v1.1.1_Portable.zip`** from the v1.1.1 release's Assets section.

Do not use GitHub's automatically generated **Source code (zip)** or **Source code (tar.gz)** archives as the Mod Manager download.

## Integrity

SHA-256 for `CMZ_Mod_Manager_v1.1.1_Portable.zip`:

`8B96BBD32EF494AD3C63A7F0290E115F5A15799D3797B6AE2F6C0FC4CE050581`

The same checksum is published in [`CMZ_Mod_Manager_v1.1.1_SHA256.txt`](CMZ_Mod_Manager_v1.1.1_SHA256.txt).

## Privacy and third-party code

CastleMiner Z Mod Manager does not include first-party telemetry or analytics.

Runtime mods and custom scenario generators are executable third-party code and are **not sandboxed**. Only install packages from authors you trust. Package validation and hashes verify integrity; they do not establish that third-party code is safe or trustworthy.

Review diagnostic files before sharing them publicly.

## Windows security notice

CastleMiner Z Mod Manager is distributed without a paid Authenticode certificate. Windows may therefore show an **Unknown publisher** or Microsoft Defender SmartScreen warning for a new download.

Obtain the package from this official repository and verify the SHA-256 checksum when desired. Do not disable Windows Security or antivirus protection just to run the Mod Manager.

## Distribution contents

The public Mod Manager package contains the Mod Manager, CMZ Runtime/SDK framework components, integrated World Builder, localization resources, themes, validation baseline, Harmony 2.4.2, and required third-party license notices.

It contains **no bundled gameplay mods**, **no bundled custom scenario packages**, and **no builder/source tree**.
