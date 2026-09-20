# FAQ

**Do I need Python?**
No. The release package is self-contained.

**Which GPU/driver do I need?**
An RTX 3090 (SM86) as the single active NVIDIA adapter, with driver 616.64. Other
configurations are refused.

**Does it change my driver?**
No. It reads your installed driver and prepares adapted runtime state under
`%LOCALAPPDATA%`. The DriverStore is never modified.

**Does it download anything?**
No. It works fully offline. There is no telemetry.

**Is it a DLSS Frame Generation mod?**
No. It targets NVIDIA's driver-level NvPresent / Smooth Motion path, not
Streamline/NGX DLSS-G.

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
Run `Uninstall.cmd`. Optionally `Uninstall.cmd -IncludeGenerated` also removes
generated runtime copies.

**Can I redistribute it?**
No. Personal use only; no redistribution or repackaging. See `LICENSE.txt`.

**How do I know the download is genuine?**
Verify the SHA-256 in `SHA256SUMS.txt` against the release page. Download only from
the official repository's Releases.
