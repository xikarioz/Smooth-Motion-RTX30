# Compatibility

Tiers used by the project. A report never auto-promotes a tier; it is reviewed.

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
| Other RTX 30 / SM86 (3080, 3070, 3060, 3050, laptop) | 616.64 | D3D11 / D3D12 | EXPERIMENTAL (architecture-compatible) |
| Any RTX 30 | other drivers | — | UNKNOWN (refused until validated) |

## Linux (research only — no installer)

| GPU | Driver | Status |
|---|---|---|
| RTX 3080 | 595.91.07 | RESEARCH_VALIDATED (external handoff; not productized) |

## Report your result

Open a **Hardware Validation Report** issue with your GPU, driver, Windows version,
game, storefront, API and ON/OFF observation. Do **not** upload NVIDIA DLLs or
memory dumps. Reports feed the table above after review.
