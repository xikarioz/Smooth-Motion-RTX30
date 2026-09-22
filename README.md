English | [简体中文](README.zh-CN.md) | [Español](README.es-419.md)

<p align="center">
  <img src="assets/banner.png" alt="Smooth Motion SM86" width="900">
</p>

# Smooth Motion SM86 — NVIDIA Smooth Motion for RTX 30 Series

**NVIDIA Smooth Motion on RTX 30-series / Ampere SM86. One installer. No per-game frame-generation integration required.**

Smooth Motion SM86 enables NVIDIA's driver-level **NvPresent / Smooth Motion**
frame-interpolation path on Ampere SM86 GPUs where NVIDIA does not currently
expose it — as a one-click Windows utility.

> **Not a DLSS Frame Generation mod.**
> It uses NVIDIA's presentation-level Smooth Motion path instead of requiring a
> game's Streamline / DLSS-G integration.

**⬇ [Download Smooth Motion SM86 v0.5.0 for Windows](https://github.com/xikarioz/Smooth-Motion-RTX30/releases/latest)**

> **Current release: v0.5.0.** Includes the Manager startup crash fix, the Simplified
> Chinese installer dynamic-field fix, a clarified close/tray behaviour, and an
> experimental **statically validated** path for the exact recognized **591.86**
> NvPresent build. **616.64 remains the live-validated golden configuration.** 591.86 is
> *not* live validated yet — please test it and report back.

RTX 30 / SM86 · D3D11 · D3D12 · Experimental Vulkan · Windows 10/11 x64

![Latest release](https://img.shields.io/github/v/release/xikarioz/Smooth-Motion-RTX30?label=release&color=3fae6a)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6)
![GPU](https://img.shields.io/badge/GPU-RTX%2030%20%2F%20SM86-76B900)
![Status](https://img.shields.io/badge/status-Consumer%20Preview-orange)

Target architecture: **RTX 30-series / Ampere SM86.** The **RTX 3090 + driver
616.64** is live validated; the exact recognized NvPresent build from driver
**591.86** is **statically validated / experimental**. An unrecognized driver is not
"unsupported" for installation — Setup and the Manager still run, with Smooth Motion
**fail-closed** until your installed NvPresent binary is recognized and validated.

**Tested in 16 real games across multiple engines and launch environments —
including D3D11, D3D12 and Game Pass titles.**

---

## See it working

**Real same-scene ON → OFF → ON capture coming next.**

The demo will use unmodified gameplay footage, with no synthetic interpolation and
no playback-speed manipulation.

## Tested in real games

| Game | Test status |
|---|---|
| Assassin's Creed Origins | ✅ Smooth Motion observed working |
| Assassin's Creed Odyssey | ✅ Runtime / live ON → OFF → ON validation |
| Black Myth: Wukong | ✅ Smooth Motion observed working |
| Resident Evil 4 | ✅ Smooth Motion observed working |
| Resident Evil Requiem | ✅ Smooth Motion observed working |
| Alan Wake 2 | ✅ Smooth Motion observed working |
| Cyberpunk 2077 | ✅ Smooth Motion observed working |
| The Last of Us | ✅ Smooth Motion observed working |
| Hogwarts Legacy | ✅ Smooth Motion observed working / measurement workload |
| Clair Obscur: Expedition 33 — Game Pass | ✅ Smooth Motion observed working |
| Marvel's Spider-Man 2 | ✅ Smooth Motion observed working |
| Hades | ✅ Smooth Motion observed working |
| Until Dawn | ✅ Smooth Motion observed working |
| Kingdom Come: Deliverance II | ✅ Smooth Motion observed working |
| Persona 3 Reload | ✅ Smooth Motion observed working |
| Pragmata | ✅ Smooth Motion observed working |

> **Evidence note:** "Observed working" means Smooth Motion was enabled and its
> effect was directly observed during real gameplay. It does not imply that every
> title received the same level of instrumentation or independent frame-content
> validation.

## Quick start

1. Download **`SmoothMotionSM86-Setup.exe`** from the [latest release](https://github.com/xikarioz/Smooth-Motion-RTX30/releases/latest).
2. Run it (no administrator rights, no Python, no terminal).
3. Open **Smooth Motion SM86**.
4. Turn **SMOOTH MOTION** on.
5. Pick a game and press **PLAY**.

Full guide: [INSTALL.md](INSTALL.md) · Problems: [TROUBLESHOOTING.md](TROUBLESHOOTING.md)

## What you get

A gamer-first manager that does the hard part for you:

- **Automatic GPU + driver detection** with a plain-language compatibility status.
- **One-click master switch** and **per-game switches**.
- **Live ON/OFF** for a supported running game — flip it mid-game (Manager button,
  the optional global hotkey, or the **system tray**) for a same-scene A/B/A
  comparison, no restart. Results appear as a normal Windows notification.
- **System tray** controls (status, current game, toggle, open Manager, exit);
  the Manager can be closed to the tray.
- **Game library** scanning Steam, Epic and Game Pass — pick a game and Play.
- **Fail-closed**: if your driver binary isn't recognized, nothing is modified.
- **Reversible**: rollback and uninstall are built in. The DriverStore is never
  touched and no NVIDIA binary is redistributed.

## How is this different from DLSS-G mods?

Neutral, one line each:

- **Smooth Motion SM86**: game → NVIDIA presentation path → **NvPresent / Smooth Motion** → generated frames.
- **DLSS Frame Generation mods**: game with DLSS-FG integration → Streamline / NGX → **DLSS-G** → generated frames.

Different integration layer, different adaptation point. This project works with
the driver's presentation backend, not the game's DLSS-FG integration.

## Compatibility

**Current policy (v0.5.0-rc.1 and later): driver version alone no longer decides
whether the app may be installed.** Setup and the Manager run on unknown drivers;
Smooth Motion activation stays **fail-closed** until the installed NvPresent binary
is recognized and validated.

| Configuration | Status | Manager | Smooth Motion |
|---|---|---|---|
| RTX 3090 + driver 616.64 (golden) | **Live validated** | Yes | Yes |
| Exact recognized NvPresent build from driver 591.86 | **Statically validated / experimental** | Yes | Experimental (not yet live-validated) |
| Unknown / unvalidated NvPresent | Unvalidated | Yes | No — fail-closed |
| Non-SM86 GPU (RTX 40/50, RTX 20, GTX 10, AMD/Intel) | Not supported by the engine | Yes | No |
| Multi-GPU systems | Device selection not implemented | Yes | No |

Three separate dimensions, kept distinct on purpose:

- **Hardware compatibility:** Ampere **SM86 / RTX 30-series** is the target architecture.
- **Physical/live validation:** only the **RTX 3090 + driver 616.64** is physically validated.
- **Other single-GPU SM86 RTX 30 boards** are **experimental** once the exact
  driver/profile is recognized (not "unsupported").
- **D3D11** dynamic-engine live path: **instrumentally validated**. **D3D12**: observed
  working in real games (active-engine instrumentation currently inconclusive).
- **32-bit titles and anti-cheat protected titles** are not supported.

> Historical note: v0.4.x releases were restricted to the validated 616.64 profile.
> That restriction was removed in v0.5.0-rc.1; see the release notes.

Details and tiers: [SUPPORT.md](SUPPORT.md) · [COMPATIBILITY.md](COMPATIBILITY.md) · [VALIDATION.md](VALIDATION.md)

## Validation

The compatibility engine is proprietary, so the evidence is documented publicly
instead. **[VALIDATION.md](VALIDATION.md)** covers the golden system, the compact
adaptation, runtime validation and the project's evidence tiers.

Summary: on the validated **RTX 3090 / driver 616.64** golden build the adaptation
is **41 modified sites / 61 bytes total** — 20 compatible non-FP8 module targets
adapted, **17 FP8-targeted modules deliberately excluded**, and no tested non-FP8
SASS instruction rewriting was required. The current research engine reproduces that
golden configuration at runtime, including transform parity, transactional rollback
and repeated live state transitions (300 transitions, 0 state mismatches).

- **D3D11** — the live ON/OFF/ON path is **instrumentally validated** on the golden
  configuration.
- **D3D12** — Smooth Motion is **observed working in real D3D12 games**, but current
  active dynamic-engine runtime instrumentation is **inconclusive** (no target
  module-load traffic was observed in the latest active-engine validation window).
  This is not classified as a regression.

## Safety & trust

- **No NVIDIA binary redistribution** — it derives what it needs from your own
  installed driver.
- **DriverStore untouched** — the original driver files are never modified.
- **Fail-closed** — unknown driver/layout → no patch, and you're told why.
- **Reversible** — per-version install, rollback, uninstall.
- **Privacy** — offline, no telemetry, no accounts; see [PRIVACY.md](PRIVACY.md).
- **Checksums published** — verify the download against `SHA256SUMS.txt`.
- **Unsigned Consumer Preview** — SmartScreen may prompt; the SHA-256 is the
  integrity anchor.

## Known limitations

- Unsigned Consumer Preview — SmartScreen may prompt; verify the SHA-256.
- Closing the window (title-bar **X**) keeps Smooth Motion SM86 in the **system tray**
  so background monitoring continues. Use the tray icon's **Exit** to quit completely.
- Storefront titles that relaunch into a new process (some Game Pass / Epic) are
  not reliably followed yet.
- Windows Vulkan is experimental; no in-game toggle there.
- **Multi-GPU systems: the current Consumer Preview expects a single CUDA/NVIDIA
  target device. Explicit rendering-GPU selection is planned for a later release.**
  This is a manager device-selection limitation, **not** a hardware
  incompatibility.
- Higher base FPS is strongly recommended; very low base FPS increases artifacts
  and perceived latency.

## Screenshots

The real **Smooth Motion SM86 Manager** on the validated system (RTX 3090 + driver
616.64): automatic GPU/driver detection, compatibility status, the master switch and
the live **NOW PLAYING** control.

![Smooth Motion SM86 Manager](assets/manager-top.png)

The **installer** detects your GPU, NVIDIA driver and compatibility before anything
is installed:

![Smooth Motion SM86 installer compatibility page](assets/setup-compat.png)

*A real v0.4.3 Setup run on the validated RTX 3090 + driver 616.64.*

## Roadmap

More RTX 30 physical validation · more driver profiles · Game Pass / Epic seamless
launch · Vulkan productization · multi-GPU targeting · signed releases. See
[ROADMAP.md](ROADMAP.md).

## Help validate more RTX 30 GPUs

Own an **RTX 3050 / 3060 / 3060 Ti / 3070 / 3070 Ti / 3080 / 3080 Ti** (or another
single-GPU SM86 board)? Community validation on additional Ampere SM86 systems is
especially useful.

If Smooth Motion works on your system, submit the structured
**[Hardware Validation Report](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)**
with:

- GPU model (+ PCI ID if the diagnostics show it) and driver version
- Windows version
- game (and build if practical)
- storefront and launch method (the same game can differ per launch environment)
- graphics API if known
- approximate **base FPS**, resolution and refresh
- Smooth Motion requested vs applied state, and interpolation observed
- crash / artifact severity
- the exported diagnostics (**Export Diagnostics** in the Manager, or `sm86.exe report`)
- whether you tried a live toggle, and what you saw

Discussion and results live in **Discussions**; use **Issues** for reproducible
product bugs. Full schema and the evidence-tier model:
[docs/COMMUNITY_VALIDATION.md](docs/COMMUNITY_VALIDATION.md).

Reports never promote a configuration to `PROJECT_VALIDATED` by themselves. See the
tier model in [COMPATIBILITY.md](COMPATIBILITY.md): `PROJECT_VALIDATED` (project,
reference board) · `COMMUNITY_CONFIRMED` (high-quality external report) ·
`COMMUNITY_REPORTED` (plausible, incomplete instrumentation) · `EXPERIMENTAL`
(architecture-compatible, not yet validated) · `UNTESTED`.

If the project was useful, consider **starring it**.

## License

Proprietary, source-not-published. Personal use permitted; no redistribution or
repackaging. See [EULA.txt](EULA.txt).

NVIDIA Smooth Motion, NvPresent and CUDA are NVIDIA technologies, not included
here. This is an independent project, not affiliated with or endorsed by NVIDIA.
