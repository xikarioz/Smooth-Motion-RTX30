# Install

## Requirements

- Windows 10/11 x64
- NVIDIA RTX 3090 (SM86) as the single active display adapter
- NVIDIA driver **616.64** (`32.0.16.1664`)
- No administrator rights required

Other configurations are refused by design (fail closed).

## Steps

1. Download `SmoothMotionSM86-<version>-win64.zip` from the official Releases page.
2. Verify the SHA-256 (see `SHA256SUMS.txt` next to the download).
3. Extract the ZIP anywhere (e.g. `%USERPROFILE%\Downloads\SmoothMotionSM86`).
4. Run `Instalar.cmd`.
   - It runs a read-only compatibility check first.
   - If your GPU/driver is supported, it prepares the local runtime state from
     your own driver and creates the Start Menu shortcut.
   - If not, it stops without changing anything.
5. Open **Smooth Motion SM86** from the Start Menu.

Check-only mode: `powershell -ExecutionPolicy Bypass -File Install-Frozen.ps1 -CheckOnly`
verifies compatibility without preparing anything.

## Using the app

1. Click **Check PC** — shows GPU, driver, compatibility.
2. Click **Prepare** — builds the local runtime state (hash-verified).
3. Pick your game's real executable / full game folder, click **Check game**.
4. Click **Launch game**.
5. While playing, use **Smooth ON / OFF** to compare, and **State** to see whether
   the feature is requested/applied.

The command-line interface `sm86.exe` (same folder) exposes the same operations
for advanced users:

```
sm86.exe doctor
sm86.exe prepare
sm86.exe state
sm86.exe on | off
sm86.exe report
```

## Repair / rollback / uninstall

- **Repair:** run `Instalar.cmd` again (or `sm86.exe repair`).
- **Rollback:** `sm86.exe rollback` removes the generated runtime copies.
- **Uninstall:** `Uninstall.cmd` removes the app files and the shortcut.

Nothing outside `%LOCALAPPDATA%\SmoothMotionSM86` is touched. Your NVIDIA driver
and your games are never modified.
