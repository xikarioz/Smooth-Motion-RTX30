# Release notes — Smooth Motion SM86 0.4.0 (consumer preview)

## What this is

An unsigned research-preview tool that enables NVIDIA Smooth Motion on Ampere
SM86 GPUs (RTX 30-series), validated primarily on an RTX 3090 with driver 616.64.
It derives what it needs from your own installed NVIDIA driver; no NVIDIA binary
is redistributed and the DriverStore is never modified.

## What's new in 0.4.0

- **Smooth Motion Manager** with a one-click master switch and a per-game switch.
- **Game library** scanning (Steam, Epic, Game Pass) — pick a game and press Play.
- **Automatic system detection** with consumer-language compatibility status.
- **Driver-change detection**: an old profile is never applied to a changed driver.
- **Distribution-only packaging**: the release profile data is embedded in the
  compiled product; no readable recipe file ships.
- Proprietary end-user license (source not published).

## Validated environment

- NVIDIA RTX 3090 (SM86), single active adapter
- Driver 616.64 (`32.0.16.1664`), Windows 10/11 x64

## Status

- Validated: selected D3D11/D3D12 titles (direct EXE launch).
- Architecture compatible (experimental): other single-GPU RTX 30 / SM86 boards
  with the same driver — same architecture, not physically validated.
- Experimental: Windows Vulkan.
- Not supported: other drivers, 32-bit titles, anti-cheat titles, multi-GPU.

## Known limitations

- Unsigned build (`UNSIGNED_RESEARCH_PREVIEW`).
- Storefront titles that relaunch into a new process (Game Pass / some Epic) are
  not reliably followed yet.
- No in-game toggle on the Vulkan path.
- Higher base FPS strongly recommended; very low base FPS increases artifacts and
  perceived latency.
