# Support status

Smooth Motion SM86 supports a deliberately narrow, validated configuration. Other
combinations are refused rather than guessed.

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
| Other Ampere SM86 GPUs (RTX 3080 / 3080 Ti / 3060 Ti / 3060) with driver 616.64 | Same architecture; not physically validated. May work; no promise. |
| Windows Vulkan | Research path demonstrated; packaged activation is experimental and may not survive storefront process relaunches. |
| In-game toggling on the Vulkan path | Not implemented. |

## Not supported

- Other driver versions (refused; no guessing).
- Non-SM86 GPUs (RTX 40/50, RTX 20, GTX 10, AMD/Intel).
- Multi-GPU / hybrid systems.
- 32-bit titles.
- Anti-cheat protected or competitive multiplayer titles.
- Automated updates (none; download new releases manually).

## How compatibility is decided

The tool verifies, in order: a reviewed profile for your driver's NvPresent
binary, the exact binary hash, the exact Windows driver version, exactly one CUDA
device, and exact SM86 compute capability. Any mismatch stops the process with a
clear reason.

## Reporting results

Community reports are welcome via the issue tracker. Include GPU, driver, Windows
version, game, API and the exported diagnostics. Reports never promote a
configuration to "validated" by themselves.
