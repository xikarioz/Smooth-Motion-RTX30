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
| **COMMUNITY_CONFIRMED** | multiple independent user reports with plausible evidence |
| **EXPERIMENTAL** | architecture-compatible, not yet validated |
| **FAILED** | reported not working |
| **UNKNOWN** | no data yet |

## Windows

| GPU | Driver | API | Status |
|---|---|---|---|
| RTX 3090 | 616.64 | D3D11 / D3D12 | **PROJECT_VALIDATED** |
| RTX 3090 | 616.64 | Vulkan | PRACTICALLY_VALIDATED (research path); packaged launch EXPERIMENTAL |
| Other single-GPU RTX 30 / SM86 (3080, 3070, 3060, 3050, laptop) | 616.64 | D3D11 / D3D12 | EXPERIMENTAL (architecture-compatible; admitted when the exact driver/profile is accepted) |
| Any RTX 30 | other drivers | — | UNKNOWN (refused until validated) |
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

Open a **Hardware Validation Report** issue with your GPU, driver, Windows version,
game, storefront, API and ON/OFF observation. Do **not** upload NVIDIA DLLs or
memory dumps. Reports feed the table above after review.
