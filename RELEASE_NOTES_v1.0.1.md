# CastleMiner Z Mod Manager v1.0.1

Maintenance and privacy-hardening update for CastleMiner Z Mod Manager.

## Privacy hardening

- Steam64 IDs are no longer shown in normal World Builder profile/success UI.
- Full local save paths are no longer shown in normal world-generation success dialogs.
- World Builder and Manager diagnostics sanitize local paths and Steam64 IDs before display/export.
- Diagnostic exports use neutral profile filenames rather than exposing custom Manager profile names.
- Standard diagnostic ZIPs no longer automatically include third-party mod logs.
- Diagnostic exports are limited to the 10 most recent session records.
- Diagnostic exports include a privacy notice reminding users to review files before public sharing.
- Successful and cancelled custom-scenario job records are cleaned up after generation.
- Failed scenario-job retention is bounded to the newest 10 jobs and 14 days for troubleshooting.
- Removing a mod's saved Data/Config also removes that mod's retained log.

## Version and localization alignment

- CastleMiner Z Mod Manager product version: **v1.0.1**.
- Integrated CastleMiner Z World Builder product version: **v1.0.1**.
- All 23 interface languages now display the World Builder v1.0.1 label consistently.
- CMZ Runtime remains **v1.0.0**.
- CMZ Mod SDK/API remains **v1.0.0**.
- Harmony remains **v2.4.2**.

The Runtime and Mod SDK were intentionally not version-bumped because their implementation did not change in this maintenance release.

## Supported game

**CastleMiner Z 1.9.9.8 — Steam / Windows**

## Download

Download **`CMZ_Mod_Manager_v1.0.1_Portable.zip`** from the v1.0.1 release's Assets section.

Do not use GitHub's automatically generated **Source code (zip)** or **Source code (tar.gz)** archives as the Mod Manager download.

## Integrity

SHA-256 for `CMZ_Mod_Manager_v1.0.1_Portable.zip`:

`CAA EBD381725CB8B0130D351181185F965C408527D2832F2B1C8DA75EDEF653D`

Canonical checksum without spacing:

`CAAEBD381725CB8B0130D351181185F965C408527D2832F2B1C8DA75EDEF653D`

## Privacy and third-party code

CastleMiner Z Mod Manager does not include first-party telemetry or analytics.

Runtime mods and custom scenario generators are executable third-party code and are **not sandboxed**. Only install packages from authors you trust. Package validation and hashes verify integrity; they do not establish that third-party code is safe or trustworthy.

Review diagnostic files before sharing them publicly.

## Windows security notice

CastleMiner Z Mod Manager is currently distributed without a paid Authenticode certificate. Windows may therefore show an **Unknown publisher** or Microsoft Defender SmartScreen warning for a new download.

Obtain the package from this official repository and verify the SHA-256 checksum when desired. Do not disable Windows Security or antivirus protection just to run the Mod Manager.

## Distribution contents

The public Mod Manager package contains the Mod Manager, CMZ Runtime/SDK framework components, integrated World Builder, localization resources, themes, validation baseline, Harmony 2.4.2, and the required third-party license notices.

It contains **no bundled gameplay mods** and **no bundled custom scenario packages**.
