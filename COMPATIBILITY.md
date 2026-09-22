English | [简体中文](COMPATIBILITY.zh-CN.md) | [Español](COMPATIBILITY.es-419.md)

# Compatibility

Tiers used by the project. A report never auto-promotes a tier; it is reviewed.

Three separate dimensions (do not merge them):

- **Hardware compatibility** — target architecture (Ampere SM86 / RTX 30-series).
- **Physical validation** — the exact board/driver actually tested.
- **Multi-adapter product support** — whether the manager can select the target
  device when more than one GPU is present.

| Tier | Meaning |
|---|---|
| **PROJECT_VALIDATED** | validated by the project on the reference board |
| **COMMUNITY_CONFIRMED** | high-quality external report with adequate diagnostics |
| **COMMUNITY_REPORTED** | plausible user report, instrumentation incomplete |
| **EXPERIMENTAL** | architecture-compatible, not yet validated |
| **UNTESTED** | no data yet |
| **FAILED** | reported not working |

Results are recorded per (GPU, driver, game, API, storefront, launch method)
combination; the same game may legitimately differ across launch environments. See
[COMMUNITY_VALIDATION.md](docs/COMMUNITY_VALIDATION.md).

## Current policy (v0.5.0-rc.1 and later)

Driver version alone no longer decides whether the app may be installed. Setup and
the Manager run on unknown drivers; Smooth Motion activation is **fail-closed** until
the installed NvPresent binary is recognized and validated.

| Configuration | Status | Smooth Motion |
|---|---|---|
| RTX 3090 + driver 616.64 | **LIVE_VALIDATED** (golden) | Yes |
| Exact recognized NvPresent build from driver 591.86 | **STATICALLY_VALIDATED / experimental** | Experimental; not yet live-validated |
| Unknown / unvalidated NvPresent | Unvalidated | No — fail-closed |

## Windows

| GPU | Driver | API | Status |
|---|---|---|---|
| RTX 3090 | 616.64 | D3D11 | **PROJECT_VALIDATED** — instrumentally validated live path |
| RTX 3090 | 616.64 | D3D12 | **PROJECT_VALIDATED (real-game)** — observed working; active-engine runtime instrumentation currently inconclusive |
| RTX 3090 | 616.64 | Vulkan | PRACTICALLY_VALIDATED (research path); packaged launch EXPERIMENTAL |
| Other single-GPU RTX 30 / SM86 (3080, 3070, 3060, 3050, laptop) | 616.64 | D3D11 / D3D12 | EXPERIMENTAL (architecture-compatible; admitted when the exact driver/profile is accepted) |
| Any RTX 30 | exact recognized 591.86 NvPresent | D3D11 / D3D12 | STATICALLY_VALIDATED (experimental; not yet live-validated) |
| Any RTX 30 | unknown / unvalidated NvPresent | — | Setup + Manager run; Smooth Motion refused (fail-closed) |
| Multi-GPU systems | 616.64 | — | Device selection not implemented (see below) |

## Device selection

Multi-GPU systems: the current Consumer Preview expects a single CUDA/NVIDIA target
device. Explicit rendering-GPU selection is planned for a later release. This is a
manager device-selection limitation, **not** evidence that those GPUs are
incompatible.

## Linux (research only — no installer)

| GPU | Driver | Status |
|---|---|---|
| RTX 3080 | 595.91.07 | RESEARCH_VALIDATED (external handoff; not productized) |

## Report your result

Submit a
**[Hardware Validation Report](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)**
with your GPU, driver, Windows version, game, storefront, API and ON/OFF
observation. Attach the exported diagnostics (**Export Diagnostics** in the Manager,
or `sm86.exe report`). Do **not** upload NVIDIA DLLs or memory dumps. Reports feed
the table above after review, and a single report never promotes a configuration to
`PROJECT_VALIDATED`.
