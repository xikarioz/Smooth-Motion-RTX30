English | [简体中文](TROUBLESHOOTING.zh-CN.md) | [Español](TROUBLESHOOTING.es-419.md)

# Troubleshooting

## Compatibility check says my GPU/driver is not supported

The tool refuses instead of guessing. It physically validates a single board
(RTX 3090) with driver 616.64; other driver versions and non-SM86 GPUs are refused.
If you have a single RTX 30 / SM86 GPU with the validated driver, it is admitted
as **experimental** when the exact driver/profile is accepted (not "unsupported").

## I have two GPUs (multi-GPU)

The current Consumer Preview expects a single CUDA/NVIDIA target device. Explicit
rendering-GPU selection is planned for a later release. This is a **manager
device-selection limitation, not a hardware incompatibility** — the target
architecture (Ampere SM86 / RTX 30-series) is unaffected by how many adapters are
installed.

## The game launches but I see no difference

1. Check **State** — `null` means UNKNOWN, never False.
2. Disable the game's **native** frame generation in its menu; do not stack other
   frame-generation mods.
3. Make sure the game was started through the app's **Launch game** (or
   `sm86.exe launch`). Injection is per-process; a game that relaunches itself
   into a new process loses it — automatic following is not enabled.
4. Use borderless/windowed mode for measurement; the in-game FPS counter plus the
   NVIDIA overlay is the recommended readout.

## Many artifacts or high latency

In our tests, at very low base framerates — around 20 FPS — interpolation
artifacts and perceived latency increased substantially. Raise the base framerate
before enabling Smooth. Do not expect Smooth to make 20 FPS feel like 40 FPS at
perfect quality.

## Windows Vulkan games

The Vulkan path is experimental. Some storefront titles (e.g. Game Pass) relaunch
into a fresh game process, which defeats the per-process activation; those are not
supported yet. See [SUPPORT.md](SUPPORT.md).

## "Unknown driver" / nothing is patched

Correct: unknown drivers are refused, not patched. The tool never guesses.

## Clean removal

- `Uninstall.cmd` — removes app files + shortcut (keeps generated runtime copies).
- `Uninstall.cmd -IncludeGenerated` — also removes generated copies.
- `sm86.exe rollback` — removes generated copies only.

The uninstaller refuses any path outside `%LOCALAPPDATA%\SmoothMotionSM86`.

## Reporting an issue

Export Diagnostics from the app (or run `sm86.exe report`). It creates a ZIP with
safe metadata only — diagnosis, hashes, profile, high-level status — with personal
paths redacted. It contains no NVIDIA binaries. Review it before attaching it.
Include GPU, driver, Windows version, game, API and whether native FG was disabled.
