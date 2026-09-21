English | [简体中文](VALIDATION.zh-CN.md) | [Español](VALIDATION.es-419.md)

# Validation

This project's compatibility engine is proprietary, so this document publishes the
**evidence** rather than the method. It contains no offsets, addresses, signatures,
hook internals, classifier internals or NVIDIA binaries — only high-level,
public-safe results.

This is the **canonical source** for the project's evidence-tier wording. Other
documents link here instead of restating nuanced claims.

## Golden system

| Item | Value |
|---|---|
| GPU | NVIDIA GeForce RTX 3090 (GA102, Ampere SM86), single active adapter |
| Driver | 616.64 (`32.0.16.1664`) |
| OS | Windows 10/11 x64 |
| Graphics APIs | Native D3D11 and D3D12 (packaged product); experimental Vulkan |
| Install / prepare / rollback / uninstall | Supported |

Other single-GPU SM86 RTX 30 boards are architecture-compatible and **experimental**
until physically validated. Other driver versions are refused (nothing is modified).

## Compatibility adaptation

On the validated golden build the required adaptation is compact and
metadata-scoped:

- **41 modified sites / 61 bytes total**
- 1 host architecture-eligibility byte
- 60 bytes of GPU-module metadata
- **20 compatible non-FP8 module targets** adapted
- **17 FP8-targeted modules deliberately excluded** — Ampere SM86 lacks the native
  FP8 Tensor Core execution path those modules target
- **No tested non-FP8 SASS instruction rewriting was required** on the validated
  golden configuration

"Compact" describes the validated result; it is not a mathematical minimality
claim. No patch offsets, signatures or address tables are published here.

## Runtime validation

Evidence was gathered at the runtime level, described only at a high level:

- **Real runtime CUDA-module observation** — the CUDA modules a real session
  actually loads are observed and reconciled against the static population.
- **Shadow transform parity** — an independent derivation is byte-compared against
  the validated build before any runtime authority is granted.
- **Active dynamic-engine validation** — the engine drove real sessions and produced
  the expected transforms with zero nonzero CUDA results.
- **Exact rollback checks** — every activation is reversible, with read-back
  verified to return to the original state.
- **ON/OFF/ON controls** — live requested/applied transitions tracked across held
  phases on the D3D11 path.
- **Lifecycle testing** — repeated attach/init cycles with no leaked authority and no
  double hooking.

The current research engine has also been validated against the known-good
RTX 3090 / 616.64 configuration at runtime, including transform parity,
transactional rollback and repeated live state transitions.

## Golden engine result

| Result | Value |
|---|---|
| Live authority transitions | **300** |
| State mismatches | **0** |
| Rollback | exact |
| Lifecycle | pass |
| D3D11 A/B/A | pass |
| D3D12 | inconclusive — no runtime module-load traffic observed in the test window; not claimed as runtime-validated |

## Evidence tiers

The project never conflates these states:

- *requested* ≠ *applied / active* ≠ *backend executing* ≠ *output validated*
- "Observed working" (direct user observation in a real game) is not
  "instrumentally validated" (automated frame-content evidence).
- A validated (GPU, driver, API, launch method, game) combination is not generalised
  to untested combinations.
- Community tiers: `PROJECT_VALIDATED` · `COMMUNITY_CONFIRMED` · `EXPERIMENTAL` ·
  `UNTESTED`. A single user report never promotes a configuration to
  `PROJECT_VALIDATED`.

See [SUPPORT.md](SUPPORT.md), [COMPATIBILITY.md](COMPATIBILITY.md) and
[RELEASE_NOTES.md](RELEASE_NOTES.md) for product tiers.

## What is deliberately not published

The compatibility engine's implementation is private. This document intentionally
omits hook implementation, addresses, offsets, signatures, classifier internals and
any raw NVIDIA binary content. No NVIDIA binary is redistributed.
