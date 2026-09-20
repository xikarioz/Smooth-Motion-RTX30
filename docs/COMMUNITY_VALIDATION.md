# Community validation

Smooth Motion SM86 is validated primarily on a single golden configuration
(RTX 3090 + driver 616.64). Broader confidence comes from structured community
reports. This document explains how to submit one, how results are classified, and
why the model is deliberately multi-dimensional.

A report never promotes a configuration to `PROJECT_VALIDATED` by itself.

## Where to post

- **Issues** — reproducible product bugs.
- **Discussions** — results, compatibility conversation and research topics.
  Recommended categories:
  - **Hardware Validation** — submit and discuss [Hardware Validation Reports](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml).
  - **Game Compatibility** — per-title and per-storefront behaviour.
  - **Research / Technical Discussion** — API paths, lifecycle behaviour, methodology.
  - **Installation / Setup Help** (optional) — getting running.

> Category setup may require a one-time manual step in
> **Settings → Features → Discussions** if the categories above are not present yet.

## Submit a report

Use the
**[Hardware Validation Report](https://github.com/xikarioz/Smooth-Motion-RTX30/issues/new?template=hardware_validation.yml)**
template. Export diagnostics from the Manager (**Export Diagnostics**) or run
`sm86.exe report`, then attach the result. Never attach NVIDIA DLLs, memory dumps
or personal paths.

## Why the dimensions matter

"Game X works" is not equivalent to "Game X works under every launch environment".
The same title can behave differently across storefronts, launch methods and
base framerates. Every result is therefore recorded as a combination:

| Dimension | Why it is recorded |
|---|---|
| GPU + driver | Compatibility is a property of a (GPU, driver) pair |
| Storefront | Steam / Epic / Game Pass / GOG / standalone / emulator launch differently |
| Launch method | Launcher process, direct EXE, child process, re-exec and store wrappers change attachment timing |
| Graphics API | D3D11 / D3D12 / Vulkan / translated paths have different lifecycles |
| Base FPS | Interpolation quality and artifact severity depend strongly on temporal spacing |
| Resolution + refresh | Presentation context |
| Requested vs applied state | `requested ≠ applied`; they must not be merged |
| Interpolation observed | Visual observation is not instrumented content proof |
| Crash / artifacts | Stability and quality signal |
| Diagnostics | Reproducibility and tiering |

No universal base-FPS threshold is asserted; the actual value is recorded so
future analysis can study artifact severity, latency and backend behaviour versus
base FPS.

## Evidence tiers

Each (GPU, driver, game, API, storefront, launch method) combination maps to one
tier:

| Tier | Meaning |
|---|---|
| `PROJECT_VALIDATED` | instrumented / reproduced by the project team on the reference configuration |
| `COMMUNITY_CONFIRMED` | high-quality external report with adequate diagnostics |
| `COMMUNITY_REPORTED` | plausible user report, instrumentation incomplete |
| `EXPERIMENTAL` | architecture / path admitted but not sufficiently tested |
| `UNTESTED` | no evidence |

The maintainers assign the tier after review. A single anecdotal result is never
promoted to `PROJECT_VALIDATED`.

## Compatibility observation schema (public-safe)

This is the public-safe record shape used to structure results. It contains no
reverse-engineering internals.

```json
{
  "gpu": "RTX 3080",
  "gpu_arch": "Ampere SM86",
  "driver": "616.64",
  "windows": "Windows 11 23H2",
  "game": "Example Game",
  "game_build": "1.0",
  "api": "D3D12",
  "storefront": "Steam",
  "launch_method": "Direct EXE",
  "base_fps": 55,
  "resolution": "2560x1440",
  "refresh_hz": 144,
  "requested_state": true,
  "applied_state": true,
  "interpolation_observed": "yes",
  "crash": false,
  "artifacts": "NONE",
  "diagnostics": "attached",
  "evidence_tier": "COMMUNITY_REPORTED",
  "reporter": "github-handle",
  "date": "2026-09-20"
}
```

One row is one combination. The same game may appear multiple times with different
storefronts, launch methods or results - that is expected, not a contradiction.

## Community compatibility table (structure)

Project-tested results and community reports are kept separate. New verified rows
are added over time; nothing is auto-promoted from this document.

| GPU | Driver | Game | Storefront | Launch | Base FPS | Result | Evidence tier |
|---|---|---|---|---|---|---|---|
| RTX 3090 | 616.64 | Cyberpunk 2077 | Steam | Direct EXE | — | Observed working | `PROJECT_VALIDATED` |

The populated project matrix lives in the [README](../README.md#tested-in-real-games).

## Emulators

Emulators are treated as a distinct compatibility class and are **not** claimed to
work. See [EMULATOR_TEST_PLAN.md](EMULATOR_TEST_PLAN.md); current status for all
tested emulators is `NOT_TESTED`.
