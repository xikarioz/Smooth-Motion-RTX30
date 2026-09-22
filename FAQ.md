English | [简体中文](FAQ.zh-CN.md) | [Español](FAQ.es-419.md)

# FAQ

**Do I need Python?**
No. The release package is self-contained.

**Which GPU/driver do I need?**
Target architecture: RTX 30-series / Ampere **SM86**. The **RTX 3090 + driver
616.64** is live validated; the exact recognized NvPresent build from driver
**591.86** is **statically validated / experimental**; other single-GPU SM86 RTX 30
boards are **experimental** where the exact driver/profile is recognized. On an
unknown/unvalidated driver the app still installs and the Manager opens — Smooth
Motion activation stays **fail-closed** until your NvPresent binary is recognized and
validated. Non-SM86 GPUs are not supported by the engine.

**I have two GPUs — is my RTX 30 unsupported?**
No. Multi-GPU systems: the current Consumer Preview expects a single CUDA/NVIDIA
target device; explicit rendering-GPU selection is planned for a later release.
That is a manager device-selection limitation, not a hardware incompatibility.

**Does it change my driver?**
No. It reads your installed driver and prepares adapted runtime state under
`%LOCALAPPDATA%`. The DriverStore is never modified.

**Does it download anything?**
No. It works fully offline. There is no telemetry.

**Is it a DLSS Frame Generation mod?**
No. It targets NVIDIA's driver-level NvPresent / Smooth Motion path, not
Streamline/NGX DLSS-G.

**Is D3D11 validated the same way as D3D12?**
No, and the project keeps them distinct. On the golden configuration the **D3D11
live ON/OFF/ON path is instrumentally validated**. **D3D12** titles are **observed
working in real games**, but current active dynamic-engine runtime instrumentation
is **inconclusive** (no target module-load traffic was observed in the latest
validation window; not classified as a regression). See `VALIDATION.md`.

**Can I use it in online/competitive games?**
No. Single-player/offline only. Anti-cheat protected titles are out of scope.

**Why do I see artifacts or extra latency?**
It is temporal interpolation; quality depends on base framerate. At very low base
framerates (around 20 FPS in our tests) artifacts and perceived latency increase
substantially. Higher base FPS is strongly recommended.

**The game starts but nothing changes.**
Make sure you launched it through the app, that native frame generation is
disabled, and check **State**. Games that relaunch into a new process lose the
per-process activation.

**How do I remove it?**
Installed build: Settings → Apps → *Smooth Motion SM86*. Portable build:
`Uninstall.cmd` (optionally `Uninstall.cmd -IncludeGenerated` to also remove
generated runtime copies).

**Can I redistribute it?**
No. Personal use only; no redistribution or repackaging. See `EULA.txt`.

**How do I know the download is genuine?**
Verify the SHA-256 in `SHA256SUMS.txt` against the release page. Download only from
the official repository's Releases.
