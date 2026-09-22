English | [简体中文](SUPPORT.zh-CN.md) | [Español](SUPPORT.es-419.md)

# Support status

Smooth Motion SM86 targets a deliberately narrow, validated architecture. Installation
and the Manager run on unknown drivers too; Smooth Motion activation is refused
(fail-closed) until your installed NvPresent binary is recognized and validated.

Three separate dimensions are tracked (do not merge them):

- **Hardware compatibility** — the GPU architecture the engine can target (Ampere SM86).
- **Physical validation** — the exact board/driver combination actually tested.
- **Multi-adapter product support** — whether the current manager can *select* the
  right target device when more than one GPU is present.

## Golden configuration (physically tested)

| Item | Status |
|---|---|
| GPU | NVIDIA RTX 3090 (GA102, Ampere SM86), single active adapter |
| Driver | 616.64 (`32.0.16.1664`) |
| OS | Windows 10/11 x64 |
| D3D11 live path | **Instrumentally validated** — live ON/OFF/ON on the golden configuration |
| D3D12 real-game path | **Observed working** — active dynamic-engine runtime instrumentation currently **inconclusive** |
| Install / prepare / rollback / uninstall | Supported |

## Experimental

| Item | Notes |
|---|---|
| Other single-GPU Ampere SM86 RTX 30 boards (RTX 3080 / 3080 Ti / 3070 / 3060 / 3050, laptop included) with driver 616.64 | Same architecture; **technically admitted when the exact driver/profile is accepted**, not physically validated. May work; no promise. |
| Windows Vulkan | Research path demonstrated; packaged activation is experimental and may not survive storefront process relaunches. |
| In-game toggling on the Vulkan path | Not implemented. |

## Not supported

- Smooth Motion activation on unknown/unvalidated NvPresent builds (installation and the Manager still work; activation is fail-closed).
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

## Community tiers

| Tier | Meaning |
|---|---|
| `PROJECT_VALIDATED` | validated by the project on the reference board |
| `COMMUNITY_CONFIRMED` | multiple independent user reports with plausible evidence |
| `COMMUNITY_REPORTED` | plausible user report, instrumentation incomplete |
| `EXPERIMENTAL` | architecture-compatible, not yet validated |
| `UNTESTED` | no data yet |

A single user report never promotes a configuration to `PROJECT_VALIDATED`. See
[COMMUNITY_VALIDATION.md](docs/COMMUNITY_VALIDATION.md) for the report schema and
the storefront / launch-method / base-FPS dimensions.

## Reporting results

Submit a
**[Hardware Validation Report](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)**
with GPU, driver, Windows version, game, storefront, graphics API and the exported
diagnostics (**Export Diagnostics** in the Manager, or `sm86.exe report`). Reports
never promote a configuration to "validated" by themselves.
