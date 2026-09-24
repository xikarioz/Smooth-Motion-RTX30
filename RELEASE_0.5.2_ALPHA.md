# Smooth Motion SM86 v0.5.2-alpha.1

**Prerelease / versión preliminar / 预览版.** The app displays **0.5.2 alpha**. This does not replace stable v0.5.0, and publishing it does not close the open issues.

## Changes to retest

- [#11](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/11): the Manager only hides on X when tray registration is confirmed; otherwise Retry/Exit remains visible. Exit does not terminate the game. Setup now requests a safe Manager exit when updating an idle installation; it will not force-exit an attached game.
- [#12](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/12) and [#14](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/14): Add game/Resolve executable is a real action. The selected `.exe` persists across Manager restarts, uses its full path, and can be corrected or removed. PLAY offers the executable picker instead of sending users to a dead end; Advanced opens working diagnostics.
- [#13](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/13): detected, eligible, attached and active are distinct. A running known game can show as detected even when the backend refuses activation. An attached session turned OFF can be turned ON again without restarting the game. Single-flight polling reduces duplicate scans, but the original lag report has **not** been causally attributed or ruled out.
- [#15](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/15): critical controls remain in a bottom action area; layout was exercised across English, Simplified Chinese and Spanish, several scale factors and window sizes. The reporter's display configuration still needs retesting.

## Validation and limits

- Source suite: **427 tests run** in each of normal and optimized (`-O`) modes in an isolated profile; **20 display-dependent tests were skipped** in each restricted run and the rest passed. Separate interactive source and packaged GUI smokes passed.
- The packaged CLI/Manager passed 10 executable smokes, including tray, layout, Add/PLAY persistence across processes, X/Exit lifecycle and the installer's shutdown request. The shutdown smoke refused while a controlled game state was attached, then exited when idle.
- The **exact Setup bytes below** passed clean install and uninstall in one disposable Windows Sandbox, and upgrade from v0.5.0 in a second. Settings hashes matched across upgrade; a manual library entry survived. A hidden-in-tray Manager also exited safely during a silent reinstall of the exact Setup.
- The tray icon registered with Explorer and the X/Exit behavior passed programmatic checks. The attempted overflow screenshot opened the keyboard-language menu instead, so **visual identification of the icon is not confirmed**.
- The reporters' systems and game/store combinations have **not** confirmed these fixes. Cyberpunk's original lag still needs paired ON/OFF measurements; real Game Pass/Hydra and other unsupported-store launch paths remain to be retested where available. Do not infer broad compatibility from these smokes.
- Driver authorization is unchanged: **616.64 on RTX 3090** is the live-validated golden configuration; the exact recognized **591.86** build remains static/experimental. **616.92 is not authorized** by this release: activation is refused and nothing is injected. Installing the Manager on an unknown driver does not grant backend support.

Please retest the relevant issue with this build and attach a privacy-reviewed Support Bundle. Do not close an issue solely because this prerelease exists.

## Downloads and integrity

The release assets are `SmoothMotionSM86-Setup.exe` and `SmoothMotionSM86-0.5.2-win64.zip`. Their SHA-256 hashes are in [SHA256SUMS-0.5.2-alpha.1.txt](SHA256SUMS-0.5.2-alpha.1.txt). These are distribution binaries and documentation; the private engine source, research history and NVIDIA binaries are not published here. The installer is unsigned, so Windows may show a reputation warning; verify the hash before running it.
