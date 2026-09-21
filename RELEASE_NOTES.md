English | [简体中文](RELEASE_NOTES.zh-CN.md) | [Español](RELEASE_NOTES.es-419.md)

# Release notes — Smooth Motion SM86 0.4.4 (localization)

> **Packaging note:** in the v0.4.3 release the portable runtime asset remains
> `SmoothMotionSM86-0.4.2-win64.zip`; v0.4.3 is an installer/presentation update
> over the unchanged 0.4.2 engine. The asset name is intentional, not stale.

## Evidence tiers (read this first)

The project keeps these distinct and never merges them:

- **D3D11 — instrumentally validated live path.** Live ON/OFF/ON was validated on
  the golden configuration with runtime instrumentation.
- **D3D12 — observed working in real games, active-engine instrumentation
  inconclusive.** Smooth Motion is observed working in real D3D12 games, but current
  dynamic-engine runtime instrumentation is **inconclusive** because no target
  module-load traffic was observed in the latest active-engine validation window.
  This is **not** classified as a regression.
- **Vulkan — experimental.** No in-game toggle.

Canonical source: [VALIDATION.md](VALIDATION.md).

## What's new in 0.4.4

- **Full localization: English, Simplified Chinese (简体中文) and Spanish (Español).**
- **Manager / launcher** — a language selector in the header; switching applies immediately
  and the choice is saved. First run follows the Windows UI language.
- **Installer** — English / 简体中文 / Español, chosen from the Windows UI language or the
  language dialog; the chosen language is carried into the Manager on first run.
- **System tray, Windows notifications and the CLI** use the selected language
  (machine-readable JSON stays language-neutral).
- **Public documentation** — README, install guide, troubleshooting, support, compatibility,
  FAQ, roadmap, validation, privacy, security and the EULA are available in all three languages.

## What's new in 0.4.3

- **New System Compatibility page in the installer.** Before anything is installed,
  Setup now shows the detected **GPU**, **NVIDIA driver**, **architecture** and a
  plain-language compatibility status:
  - `Compatible` (validated configuration),
  - `Experimental` (architecture-compatible but not physically validated),
  - `Driver not yet supported` (your driver version isn't validated yet — nothing is
    modified),
  - `Multiple GPUs` (automatic target selection isn't supported in this preview),
  - `Not supported` (outside RTX 30 / Ampere SM86).
- A small **Technical details** button shows GPU model, architecture, compute
  capability and driver version (no internal data).
- Silent installs (`/VERYSILENT`) are unaffected and never wait on the page.

Product engine unchanged: the bundled application is the same validated 0.4.2 build.
This release is an installer/UX improvement.

## What's new in 0.4.2

- **System tray controls**: status, current game, one-click **Toggle Smooth Motion**,
  Open Manager, Diagnostics, Exit. Close the Manager to the tray and keep playing.
- **Native Windows notifications**: when you toggle live (tray, hotkey or Manager),
  a normal Windows notification shows `Smooth Motion ON` / `Smooth Motion OFF` with
  the game name. Failure cases notify too (no active game, live unavailable,
  state not verified).
- Tray, Manager, hotkey and CLI remain **one backend** (`runtime.toggle`); every
  surface reads the same verified state.
- Live toggle: **D3D11 instrumentally validated**; **D3D12 observed working, with
  active-engine instrumentation currently inconclusive** (see *Evidence tiers*).
  Vulkan sessions show "live toggle not available" (never faked).

## What's new in 0.4.1

- **Live ON/OFF control for a running game.** When a supported game is injected and
  running, the Manager shows a **NOW PLAYING** card with a one-click ON/OFF button
  that changes the running game immediately — no terminal, no restart. Ideal for a
  same-scene A/B/A comparison.
- **Optional global hotkey** (default **Ctrl + Alt + S**, configurable in settings)
  to toggle live without leaving the game.
- Live control uses the same validated runtime engine as the CLI (`on`/`off`) and
  verifies the change with a read-back before reporting success.
- Live toggle: **D3D11 instrumentally validated**; **D3D12 observed working**
  (active-engine instrumentation currently inconclusive). It is **not** enabled for
  Vulkan sessions (shown as "not available for this session").
- Distribution-only packaging, manager, game library and driver-change detection
  as in 0.4.0.

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

- D3D11: selected titles, direct EXE launch — **instrumentally validated** (live
  ON/OFF/ON on the golden configuration).
- D3D12: selected titles — **observed working**; dynamic-engine runtime
  instrumentation currently **inconclusive** (not a regression).
- Architecture compatible (experimental): other single-GPU RTX 30 / SM86 boards
  with the same driver — same architecture, not physically validated.
- Experimental: Windows Vulkan.
- Not supported: other driver versions, 32-bit titles, anti-cheat titles.
- Multi-GPU: the current Consumer Preview expects a single CUDA/NVIDIA target
  device. Explicit rendering-GPU selection is planned for a later release (a
  manager device-selection limitation, not a hardware incompatibility).

## Known limitations

- Unsigned build (`UNSIGNED_RESEARCH_PREVIEW`).
- Storefront titles that relaunch into a new process (Game Pass / some Epic) are
  not reliably followed yet.
- No in-game toggle on the Vulkan path.
- Higher base FPS strongly recommended; very low base FPS increases artifacts and
  perceived latency.
