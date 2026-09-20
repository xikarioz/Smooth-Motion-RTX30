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

**⬇ [Download for Windows — Consumer Preview](https://github.com/xikarioz/Smooth-Motion-RTX30/releases/latest)**

RTX 30 / SM86 · D3D11 · D3D12 · Experimental Vulkan · Windows 10/11 x64

![Latest release](https://img.shields.io/github/v/release/xikarioz/Smooth-Motion-RTX30?label=release&color=3fae6a)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6)
![GPU](https://img.shields.io/badge/GPU-RTX%2030%20%2F%20SM86-76B900)
![Status](https://img.shields.io/badge/status-Consumer%20Preview-orange)

Target architecture: **RTX 30-series / Ampere SM86.** The **RTX 3090 + driver
616.64** is physically validated; other single-GPU SM86 RTX 30 boards are
**experimental** where the exact driver/profile is accepted — not "unsupported".

**Tested in 16 real games across multiple engines and launch environments —
including D3D11, D3D12 and Game Pass titles.**

---

## See it working

A real same-scene **Smooth Motion ON → OFF → ON** clip is being captured — real
footage, no synthesized comparisons and no playback-speed changes. This note will
be replaced by the clip once recorded.

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

Three separate dimensions, kept distinct on purpose:

- **Hardware compatibility:** Ampere **SM86 / RTX 30-series** is the target architecture.
- **Physical validation:** only the **RTX 3090 + driver 616.64** is physically validated.
- **Other single-GPU SM86 RTX 30 boards** are **technically admitted when the exact
  driver/profile is accepted**, and **experimental** until physically validated.

| Configuration | Status |
|---|---|
| RTX 3090 + driver 616.64, D3D11 / D3D12 | **Physically validated** |
| Other single-GPU RTX 30 / SM86 boards, same driver | **Experimental** (architecture-compatible; admitted when the exact driver/profile is accepted) |
| Other driver versions | Not yet supported (refused, nothing modified) |
| 32-bit titles, anti-cheat protected titles | Not supported |

Details and tiers: [SUPPORT.md](SUPPORT.md) · [COMPATIBILITY.md](COMPATIBILITY.md)

## Validation

The compatibility engine is proprietary, so the evidence is documented publicly
instead. **[VALIDATION.md](VALIDATION.md)** covers the golden system, the compact
adaptation, runtime validation and the project's evidence tiers.

Summary: on the validated **RTX 3090 / driver 616.64** golden build the adaptation
is **41 modified sites / 61 bytes total** — 20 compatible non-FP8 module targets
adapted, **17 FP8-targeted modules deliberately excluded**, and no tested non-FP8
SASS instruction rewriting was required. The current research engine also
reproduces that golden configuration at runtime, including transform parity,
transactional rollback and repeated live state transitions. D3D12 active-engine
runtime evidence remains inconclusive; D3D11 is the validated live path.

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

## If it works on your system

If Smooth Motion works on your RTX 30 system, consider **starring the project** and
submitting your GPU/driver result so others can see what's validated.

## License

Proprietary, source-not-published. Personal use permitted; no redistribution or
repackaging. See [EULA.txt](EULA.txt).

NVIDIA Smooth Motion, NvPresent and CUDA are NVIDIA technologies, not included
here. This is an independent project, not affiliated with or endorsed by NVIDIA.
