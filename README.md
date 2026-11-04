# Prey Vulkan — v21.5 Preview

A community Vulkan port of **Prey (2006)** for Windows, with DLSS upscaling, native NVIDIA Frame Generation, optional FSR Frame Generation, and a separate experimental Pre-DLSS version.

**[Download v21.5 and read the release notes](https://github.com/un1b4ll/prey-vulkan/releases/tag/v21.5)**

This is an experimental preview for testing. The RTX 30 unlock has **not** been tested on physical RTX 30 hardware.

## Quick start

1. Open the release page above and expand **Assets**.
2. Download **Prey-Vulkan-v21.5-Setup-Compact.exe** (494 MiB). Players only need this installer; the companion source ZIP is for developers.
3. Run setup, select your original retail Prey ISO, and choose a new or empty installation folder.
4. Choose Regular Vulkan, experimental Pre-DLSS, or both. Setup imports and verifies the disc data and applies the required retail 1.4 data updates.
5. Launch the desktop shortcut or `Regular/Play.cmd` / `PreDLSS/Play.cmd`.

The tested disc is the **European English/French/German/Spanish/Italian DVD**, containing `Setup/Data/Base/pak000.pk4` through `pak004.pk4`. Other editions or layouts may be rejected. The original ISO, retail base game data, and CD keys are not included.

## Requirements

- Windows 10/11 x64.
- A GPU and driver supporting this renderer's Vulkan 1.4 requirements.
- Your original supported Prey retail ISO.
- At least 4 GB free for installation, plus temporary extraction space.

Setup includes extraction tools and the signed Microsoft Visual C++ x64 runtime prerequisite. It does not install GPU drivers. The installer is unsigned. SHA-256 checksums are attached to the release.

## Frame Generation and installation options

| Option | Behavior |
| --- | --- |
| Native DLSS FG | Original NVIDIA path on supported RTX 40/50 cards; multiplier limits come from the SDK. |
| Experimental RTX 30 unlock | Included by default; native Vulkan community integration, one GeForce RTX 30 CUDA adapter, 2x cap. Physical RTX 30 gameplay remains unverified. |
| Optional FSR FG | Unchecked by default. Install it and explicitly select FSR in-game; 2x only. DLSS never silently switches to FSR. |
| Experimental Pre-DLSS | Separate launcher/profile; experimental pre-upscale neural rendering, not certified native DLSS 5. |

RTX 20 is not supported by the unlocked-DLSS route in this package. Workstation and multiple-CUDA-adapter unlock configurations are not advertised as supported.

In **Video > Frame Gen**, choose the provider, enable **Load FG runtime**, select the multiplier, and **Apply**. Provider/runtime changes restart the game and resume a recovery save. Use Display Apply for device-level changes.

For Pre-DLSS, press **Insert**, expand **DLSS Neural Rendering**, keep **Generate model before upscale** enabled, and save settings. Leave OptiScaler's separate FG route at **None** and use the port's own provider menu.

Regular and Pre-DLSS keep separate settings and saves. ISO recycling is optional, unchecked by default, and runs only after successful installation and verification. Keep a backup for reinstalling. `Uninstall.cmd` preserves profiles and user-added files.

## Test status and known limitations

Clean installation combinations and installed gameplay launches passed. Native NVIDIA FG and explicit FSR generation were exercised on an RTX 5070 Ti. Provider switching and recovery-save resume were also exercised. The unlock core passed a read-only provider compatibility preflight, which does not establish RTX 30 gameplay support.

Full campaign, long-session stability, and displayed frame pacing remain unverified. Known SDK validation reports remain in native FG, FSR presentation/wait threading and shutdown semaphore lifetime. Pre-DLSS also retains secondary-device, NR image-layout, and query-pool validation reports. The full release readme describes these limits.

## Feedback

Please [open an issue](https://github.com/un1b4ll/prey-vulkan/issues) with your GPU, driver version, Windows version, selected game version/FG provider, and reproduction steps. Include the relevant log excerpt when useful; remove personal paths or private information first. Never upload an ISO, CD key, or retail game archives.

## Source, licenses, and credits

**Prey-Vulkan-v21.5-Sources.zip**, attached to the same release, contains the matching engine source archives, modified OptiScaler source and patch, optional unlock core, and installer source/packaging recipe. GitHub's automatically generated source ZIP only contains this repository's files and is not a substitute for that companion archive.

Runtime license notices remain in the installer. Components retain their individual licenses; this project does not relicense the original game or third-party binaries. See the bundled notices and source archives for license terms, upstream credits, and build instructions.

The experimental unlock derives from [mor3a/rdr2-vulkan-frame-generation](https://github.com/mor3a/rdr2-vulkan-frame-generation), `vendor/ampere-core`, pinned to commit `bc853d0b4a9e7ba23ee1fe00c2c107092ccd596d`, with Prey-specific integration. It uses app-local process hooks, pins the bundled provider, disables OTA/plugin downloads in that path, and makes no driver, registry, or NVIDIA-profile changes. FSR uses AMD FidelityFX; the package also includes NVIDIA DLSS/Streamline, OpenAL Soft, SDL, and modified OptiScaler components with their accompanying notices.

This is an unofficial community project, not an official release from the original game publisher, NVIDIA, or AMD.
