English | [简体中文](EMULATOR_TEST_PLAN.zh-CN.md) | [Español](EMULATOR_TEST_PLAN.es-419.md)

# Emulator test plan

Status: **NOT_TESTED.** Emulators are treated as a distinct compatibility class.
Emulator support is **not** claimed until real tests exist.

## Legal / scope

- Test only software **already legally installed and configured by the user**.
- Do **not** provide, request or assist with copyrighted firmware, keys, BIOS files
  or game acquisition.
- If a Switch emulator is present and legally configured on the tester's own
  machine, it may be tested like any other renderer; otherwise it is skipped.

## Initial emulator set

| Emulator | Status |
|---|---|
| RPCS3 | `NOT_TESTED` |
| DuckStation | `NOT_TESTED` |
| PCSX2 | `NOT_TESTED` |
| Cemu | `NOT_TESTED` |
| Switch emulators (if legally installed) | `NOT_TESTED` |
| Other | `NOT_TESTED` |

## Per-emulator questions

For each emulator, determine and record:

1. **Render API** — what the emulator is configured to use.
2. **Actual presentation API** — what is really presented (may differ from the render API).
3. **Layer path** — translation layers in the chain, in order.
4. **NvPresent attachment** — whether the driver presentation backend is reached.
5. **Smooth state** — requested and applied.
6. **Generated interpolation observation** — visual observation, explicitly distinct
   from instrumented content proof.
7. **Lifecycle behaviour** — process model, device/swapchain creation, resets,
   swapchain recreation.
8. **Base FPS** — approximate actual value.
9. **Artifact behaviour** — type, severity, conditions.

## Report format

```
Emulator:
Backend / API:
Game / workload:
Base FPS:
Smooth state (requested / applied):
Observed interpolation:
Artifacts:
Result:
```

## Rules

- Do **not** collapse "the emulator starts" into "Smooth Motion validated".
- An emulator is only reported here after a real, described test on a described
  (GPU, driver) configuration.
- No speculative emulator badges or support claims are added to the README before
  real results exist.
