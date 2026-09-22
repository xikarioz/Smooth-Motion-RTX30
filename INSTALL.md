English | [简体中文](INSTALL.zh-CN.md) | [Español](INSTALL.es-419.md)

# Install

## Requirements

- Windows 10/11 x64 (64-bit)
- Target architecture: **RTX 30-series / Ampere SM86**
- Physically validated golden configuration: **NVIDIA RTX 3090 + driver 616.64**
  (`32.0.16.1664`), single active display adapter
- Other single-GPU SM86 RTX 30 boards: **experimental** where the exact
  driver/profile is accepted — architecture-compatible, not physically validated
- No administrator rights required

Installation is **not** tied to one exact driver version: Setup and the Manager run
on unknown drivers too. Smooth Motion activation is **fail-closed** until your
installed NvPresent binary is recognized and validated. Non-SM86 GPUs are not
supported by the engine. See [SUPPORT.md](SUPPORT.md) and [COMPATIBILITY.md](COMPATIBILITY.md).

## Steps

1. Download **`SmoothMotionSM86-Setup.exe`** from the
   [v0.5.0-rc.1 prerelease](https://github.com/xikarioz/Smooth-Motion-RTX30/releases/tag/v0.5.0-rc.1).
2. Verify its SHA-256 against `SHA256SUMS.txt` on the release page.
3. Run the installer. It performs a read-only **System Compatibility** check first
   and shows your GPU, NVIDIA driver, architecture and a plain-language status:
   `Compatible`, `Experimental`, `Driver not yet supported`, `Multiple GPUs` or
   `Not supported`.
4. Open **Smooth Motion SM86** (Start Menu or desktop shortcut).
5. Turn **SMOOTH MOTION** on.
6. Pick a game from the library and press **PLAY**.

No Python. No terminal. Windows SmartScreen may prompt because this preview is
unsigned — the SHA-256 is the integrity anchor.

### What the manager does

- **Automatic GPU + driver detection** with a plain-language compatibility status.
- **One-click master switch** and **per-game switches**.
- **Live ON/OFF** for a supported running game (Manager button, optional global
  hotkey, or the system tray) — same-scene A/B/A without restart.
- **Game library** scanning Steam, Epic and Game Pass.
- **Fail-closed**: an unrecognised driver or layout is refused; nothing is modified.

## Repair, rollback and uninstall

- **Repair:** run the installer again.
- **Rollback:** removes the generated runtime copies (Manager/tray option, or
  `sm86.exe rollback`).
- **Uninstall:** Settings → Apps → *Smooth Motion SM86* (installed build), or
  `Uninstall.cmd` (portable build).

Nothing outside `%LOCALAPPDATA%\SmoothMotionSM86` is touched. Your NVIDIA driver
and your games are never modified, and the DriverStore is never changed.

## Advanced / portable installation (legacy)

The `Setup.exe` above is the normal consumer path. A portable ZIP build is also
published for advanced users and offline machines:

1. Download `SmoothMotionSM86-<version>-win64.zip` from the release page.
2. Verify its SHA-256 against `SHA256SUMS.txt`.
3. Extract it anywhere (e.g. `%USERPROFILE%\Downloads\SmoothMotionSM86`).
4. Run `Instalar.cmd` — it runs a read-only compatibility check first, then
   prepares the local runtime state from your own driver and creates the Start Menu
   shortcut, or stops without changing anything.
5. Open **Smooth Motion SM86** from the Start Menu.

The portable ZIP is the same runtime as the installer; only the delivery and
install method differ.

### Command line (advanced)

The bundled `sm86.exe` exposes the same operations for advanced users:

```
sm86.exe doctor          # read-only GPU / active-driver / compatibility diagnosis
sm86.exe dashboard       # consumer-language system summary
sm86.exe prepare         # build the local runtime state from your installed driver
sm86.exe status | state  # requested / applied runtime state
sm86.exe on | off        # live toggle for the injected game
sm86.exe rollback        # remove project-owned generated artifacts
sm86.exe report          # privacy-reviewed diagnostic .zip (safe to attach to an issue)
```
