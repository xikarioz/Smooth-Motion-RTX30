# Smooth Motion SM86

**Research-preview tool that enables NVIDIA Smooth Motion on Ampere SM86 GPUs
(RTX 30-series) where NVIDIA does not currently expose it.**

This is a downloadable product, not an open-source project. Source code and the
internal adaptation method are not published.

> **This is not a DLSS Frame Generation mod.** It targets NVIDIA's driver-level
> NvPresent / Smooth Motion path.

- Validated primarily on **NVIDIA RTX 3090** with driver **616.64**
  (`32.0.16.1664`), single active NVIDIA adapter, Windows 10/11 x64.
- The tool derives everything it needs from **your own installed NVIDIA driver**.
- It does **not** redistribute any NVIDIA binary and **does not** modify the
  DriverStore.
- Everything is reversible: rollback and uninstall are built in.

**Status: `UNSIGNED_RESEARCH_PREVIEW`** — this build is not code-signed; Windows
SmartScreen may prompt. Verify the SHA-256 published with the release.

## Download and install

**No Python is required.** The package is self-contained.

1. Download `SmoothMotionSM86-<version>-win64.zip` from the official Releases page
   and verify its SHA-256 against the published checksum.
2. Extract the ZIP anywhere.
3. Run `Instalar.cmd`.
   - It checks your GPU and driver first. Unknown or unsupported configurations
     are refused — nothing is patched unless the environment matches a validated
     profile.
   - It then prepares the adapted runtime state locally from your driver and
     creates a **Smooth Motion SM86** Start Menu entry.
4. Open **Smooth Motion SM86** from the Start Menu.

See [INSTALL.md](INSTALL.md) for details.

## Using it

- In the app: check your PC → prepare → pick your game → launch → status / ON / OFF.
- Disable the game's **native** frame generation in its menu; do not stack other
  frame-generation mods.
- The feature can be toggled ON/OFF in a running game to compare.
- Higher base framerate is strongly recommended. At very low base framerates —
  around 20 FPS in some of our tests — interpolation artifacts and perceived
  latency increased substantially. There is no claim that Smooth makes 20 FPS feel
  like native 40 FPS.

## Using the Manager

Open **Smooth Motion SM86** from the Start Menu (or run `SmoothMotionSM86.exe`):

- The top panel detects your GPU, driver and compatibility automatically.
- **SMOOTH MOTION [ON/OFF]** is the master switch — one click, applied to future
  launches.
- **Scan Games** lists titles found in Steam, Epic and Game Pass.
- Select a game and press **Enable/Disable Game** for its own switch, then **PLAY**.
- If Smooth Motion is OFF for a game, Play launches it normally (no modification).

No terminal is needed for any of this.

## Supported at a glance

| Configuration | Status |
|---|---|
| RTX 3090 + driver 616.64, native D3D11 / D3D12, direct EXE launch | Validated |
| Other Ampere SM86 GPUs (e.g. RTX 3080 / 3060 family) with the same driver | Experimental |
| Other driver versions | Not supported (refused) |
| 32-bit titles, anti-cheat-protected/competitive titles, multi-GPU | Not supported |
| Windows Vulkan | Experimental |

Full details: [docs/SUPPORT.md](docs/SUPPORT.md).

## Safety, privacy, removal

- No NVIDIA binary is redistributed; the DriverStore is never modified.
- No telemetry, no network access, no accounts.
- Diagnostics you export are local files; nothing is uploaded automatically.
- Uninstall with `Uninstall.cmd` (or from the app). See [SECURITY.md](SECURITY.md)
  and [PRIVACY.md](PRIVACY.md).

## Single-player / offline only

Use only with single-player or offline titles. Do not use with anti-cheat
protected or competitive multiplayer games. You are responsible for where you use
this tool.

## License

Proprietary, source-not-published. Personal use is permitted; redistribution and
repackaging are not. See [LICENSE.txt](LICENSE.txt).

NVIDIA Smooth Motion, NvPresent and CUDA are NVIDIA technologies, not included
here, and this project is not affiliated with or endorsed by NVIDIA.

## Reporting issues

Use the official repository's issue tracker. Include your GPU, driver version,
Windows version, game, API, and the diagnostic bundle exported from the app. Never
upload NVIDIA binaries. See [TROUBLESHOOTING.md](TROUBLESHOOTING.md).
