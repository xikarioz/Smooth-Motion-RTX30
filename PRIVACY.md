English | [简体中文](PRIVACY.zh-CN.md) | [Español](PRIVACY.es-419.md)

# Privacy

Smooth Motion SM86 is designed to work fully offline.

## Data the tool handles

- GPU model and driver version (read from Windows).
- The SHA-256 hash of your installed `NvPresent64.dll` (to verify compatibility).
- A local record of what the tool prepared (`local-build.json`) and a local action
  journal under `%LOCALAPPDATA%\SmoothMotionSM86`.
- A local activator log under `%TEMP%` for the experimental Vulkan path.

## Network

The application does not connect to the network. There is no telemetry, no
analytics, no update checker and no account system.

## Diagnostics you choose to export

`sm86.exe report` (or the app's Export Diagnostics) creates a local ZIP containing:

- tool version, OS version, GPU, driver, hashes, selected profile;
- diagnosis and high-level runtime status;
- no NVIDIA binaries, no memory dumps, no credentials;
- personal paths rewritten to `%USERPROFILE%`.

Nothing is uploaded automatically. You decide whether to attach it to an issue.

## Removal

`Uninstall.cmd` removes the project's own files and shortcut. Generated runtime
copies are kept unless `-IncludeGenerated` is passed (so a reinstall can reuse
them). The local journal may remain as a small record of actions; delete the
`%LOCALAPPDATA%\SmoothMotionSM86` folder to remove everything.
