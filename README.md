<p align="center">
  <img src="assets/banner.png" alt="Smooth Motion SM86" width="900">
</p>

# Smooth Motion SM86

**Driver-level NVIDIA Smooth Motion for RTX 30-series (Ampere SM86).**

Bring NVIDIA's NvPresent / Smooth Motion frame-interpolation path to Ampere SM86
GPUs where NVIDIA does not currently expose it — as a one-click Windows utility.

> **Not a DLSS Frame Generation mod.** It targets NVIDIA's driver-level
> NvPresent / Smooth Motion path.

**⬇ [Download for Windows — Consumer Preview](https://github.com/xikarioz/SmoothMotionSM86/releases/latest)**

RTX 30-series · SM86 · D3D11 · D3D12 · Experimental Vulkan · Windows 10/11 x64

![Latest release](https://img.shields.io/github/v/release/xikarioz/SmoothMotionSM86?label=release&color=3fae6a)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6)
![GPU](https://img.shields.io/badge/GPU-RTX%2030%20%2F%20SM86-76B900)
![Status](https://img.shields.io/badge/status-Consumer%20Preview-orange)

Validated on **RTX 3090 + driver 616.64**. Other RTX 30 / SM86 boards are
architecture-compatible and **experimental** until physically validated.

---

## Quick start

1. Download **`SmoothMotionSM86-Setup.exe`** from the [latest release](https://github.com/xikarioz/SmoothMotionSM86/releases/latest).
2. Run it (no administrator rights, no Python, no terminal).
3. Open **Smooth Motion SM86**.
4. Turn **SMOOTH MOTION** on.
5. Pick a game and press **PLAY**.

Full guide: [INSTALL.md](INSTALL.md) · Problems: [TROUBLESHOOTING.md](TROUBLESHOOTING.md)

## What you get

A gamer-first manager that does the hard part for you:

- **Automatic GPU + driver detection** with a plain-language compatibility status.
- **One-click master switch** and **per-game switches**.
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

## Why should I trust this?

- **No NVIDIA binary redistribution** — it derives what it needs from your own
  installed driver.
- **DriverStore untouched** — the original driver files are never modified.
- **Fail-closed** — unknown driver/layout → no patch, and you're told why.
- **Reversible** — per-version install, rollback, uninstall.
- **Privacy** — offline, no telemetry, no accounts; see [PRIVACY.md](PRIVACY.md).
- **Checksums published** — verify the download against `SHA256SUMS.txt`.
- **Unsigned Consumer Preview** — SmartScreen may prompt; the SHA-256 is the
  integrity anchor.

## Compatibility

| Configuration | Status |
|---|---|
| RTX 3090 + driver 616.64, D3D11 / D3D12 | Validated |
| Other RTX 30 / SM86 boards, same driver | Architecture compatible — experimental |
| Other driver versions | Not yet supported (refused) |
| 32-bit, anti-cheat, multi-GPU | Not supported |

Details and tiers: [SUPPORT.md](SUPPORT.md) · [COMPATIBILITY.md](COMPATIBILITY.md)

## Screenshots & demo

The Manager and Setup screenshots and a short ON/OFF clip are being captured —
see the capture checklist in the repository's marketing plan. Everything shown
will be a real capture; no synthesized comparisons.

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
