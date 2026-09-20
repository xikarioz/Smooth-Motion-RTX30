# Release notes — Smooth Motion SM86 0.4.0 (consumer preview)

## What this is

An unsigned research-preview tool that enables NVIDIA Smooth Motion on Ampere
SM86 GPUs, validated primarily on an RTX 3090 with driver 616.64. The tool derives
the required runtime state from your own installed NVIDIA driver; no NVIDIA binary
is redistributed and the DriverStore is never modified.

## What changed in 0.4.0

- Distribution-only packaging: the release no longer ships a readable profile
  file; the required release profile data is embedded inside the compiled product.
- Research and driver-analysis tooling is not included in the consumer build.
- User-facing documentation, privacy statement and a proprietary end-user license
  replace the previous source-oriented docs.

## Validated environment

- NVIDIA RTX 3090 (SM86), single active adapter
- Driver 616.64 (`32.0.16.1664`), Windows 10/11 x64

## Status

- Validated: selected D3D11 and D3D12 titles (direct EXE launch).
- Experimental: Windows Vulkan; other SM86 boards; other driver versions are
  refused.
- Not supported: 32-bit titles, anti-cheat/competitive titles, multi-GPU.

## Known limitations

- Unsigned build (`UNSIGNED_RESEARCH_PREVIEW`).
- Games that relaunch into a new process lose per-process activation.
- No in-game toggle on the experimental Vulkan path.
- Higher base FPS strongly recommended (low base FPS increases artifacts and
  perceived latency).
