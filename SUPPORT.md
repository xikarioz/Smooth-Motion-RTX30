# Support status

Smooth Motion SM86 supports a deliberately narrow, validated configuration. Other
combinations are refused rather than guessed.

Three separate dimensions are tracked (do not merge them):

- **Hardware compatibility** — the GPU architecture the engine can target (Ampere SM86).
- **Physical validation** — the exact board/driver combination actually tested.
- **Multi-adapter product support** — whether the current manager can *select* the
  right target device when more than one GPU is present.

## Validated

| Item | Status |
|---|---|
| GPU | NVIDIA RTX 3090 (GA102, Ampere SM86), single active adapter |
| Driver | 616.64 (`32.0.16.1664`) |
| OS | Windows 10/11 x64 |
| Graphics API | Native D3D11 and D3D12, 64-bit, direct EXE launch |
| Install / prepare / rollback / uninstall | Supported |

## Experimental

| Item | Notes |
|---|---|
| Other single-GPU Ampere SM86 RTX 30 boards (RTX 3080 / 3080 Ti / 3070 / 3060 / 3050, laptop included) with driver 616.64 | Same architecture; **technically admitted when the exact driver/profile is accepted**, not physically validated. May work; no promise. |
| Windows Vulkan | Research path demonstrated; packaged activation is experimental and may not survive storefront process relaunches. |
| In-game toggling on the Vulkan path | Not implemented. |

## Not supported

- Other driver versions (refused; no guessing).
- Non-SM86 GPUs (RTX 40/50, RTX 20, GTX 10, AMD/Intel).
- 32-bit titles.
- Anti-cheat protected or competitive multiplayer titles.
- Automated updates (none; download new releases manually).

## Device selection (not a hardware limitation)

Multi-GPU systems: the current Consumer Preview expects a single CUDA/NVIDIA target
device. Explicit rendering-GPU selection is planned for a later release.

This is a **manager device-selection limitation**, not evidence that those GPUs are
incompatible. The engine's architecture admission is independent of how many
adapters are installed.

## How compatibility is decided

The tool verifies, in order: a reviewed profile for your driver's NvPresent
binary, the exact binary hash, the exact Windows driver version, exactly one CUDA
device, and exact SM86 compute capability. Any mismatch stops the process with a
clear reason.

## Reporting results

Community reports are welcome via the issue tracker. Include GPU, driver, Windows
version, game, API and the exported diagnostics. Reports never promote a
configuration to "validated" by themselves.
