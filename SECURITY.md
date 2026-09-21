English | [简体中文](SECURITY.zh-CN.md) | [Español](SECURITY.es-419.md)

# Security

## Intended use

Single-player / offline only. Do **not** use with anti-cheat protected or
competitive multiplayer titles. The tool performs a filename heuristic and
refuses obvious anti-cheat components, but no heuristic is a guarantee.

## What the tool does

- Reads your installed NVIDIA driver to verify GPU, driver version and binary
  hash.
- Prepares adapted runtime state under `%LOCALAPPDATA%\SmoothMotionSM86` from your
  own driver. The original driver files are untouched.
- Loads the prepared state into a game process at launch, or (experimental Vulkan)
  adapts the already-loaded signed backend in memory only.

## What the tool does not do

- No NVIDIA binary redistribution.
- No DriverStore modification.
- No administrator rights required.
- No telemetry, no network access, no accounts.
- No modification of NVIDIA App or `nvdrsdb`.

## Fail-closed behavior

Unknown driver, unknown hash, unexpected layout, unsupported GPU or ambiguous
profile data: the operation stops with a clear reason and no partial state. There
is no "best effort" mode.

## Backup and rollback

- Versioned app copies; no overwrite of a working install.
- `Uninstall.cmd` removes only project-owned files (path-guarded).
- Rollback does not touch your NVIDIA driver — it was never modified.

## Diagnostics

`sm86.exe report` produces a local ZIP with safe metadata only. It never includes
NVIDIA binaries, memory dumps or credentials, and it redacts personal paths.
Nothing is uploaded automatically.

## Reporting a vulnerability

Please report security issues privately through the repository's GitHub Security
Advisories rather than a public issue. Include version, steps to reproduce, and
whether any DriverStore or vendor file was modified.

## Known boundaries

- Unsigned build; verify the release SHA-256. SmartScreen may prompt.
- The anti-cheat scan is a heuristic, not a guarantee.
- Third-party repacks are not trusted; download only from the official Releases.
