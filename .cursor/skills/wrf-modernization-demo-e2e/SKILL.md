---
name: wrf-modernization-demo-e2e
description: Orchestrate an end-to-end WRF modernization demo for a selected routine or behavior. Use when the user wants the full flow: architecture, routine trace, Fortran fixture, Python/service recomposition, and final Fortran-vs-Python accuracy comparison.
---

# WRF Modernization Demo E2E

## Goal

Show a complete modernization loop for one selected WRF behavior. The final proof is the Python or service output compared against the original Fortran reference output.

## Required User Context

Confirm the target routine or behavior. If unspecified, propose saturation vapor pressure via `phys/module_gfs_funcphys.F` and `fpvs`.

## Workflow

1. Map relevant WRF architecture and call path using `wrf-codebase-map`.
2. Trace the selected routine with `wrf-routine-trace`.
3. Explain the Fortran implementation in modern engineering terms.
4. Optionally run or show a small idealized WRF case as context that the model builds/runs.
5. Optionally inspect NetCDF outputs when useful for context.
6. Build a small visible Fortran fixture using the real WRF routine.
7. Produce readable Fortran reference inputs and outputs.
8. Recompose the selected logic into Python or a small Python service.
9. Run the Python/service implementation on the same inputs.
10. Compare Python/service output against Fortran output with `wrf-output-parity-compare`.
11. End with a parity report: pass/fail, max/mean deltas, tolerance failures, coverage limits, and risks.

## Defaults

- Routine: saturation vapor pressure, `fpvs`.
- Fixture style: CSV input and CSV output.
- Idealized case: `em_b_wave`.
- Output inspection: NetCDF header, time records, and selected variable samples.

## Guardrails

- Ask before long builds, MPI runs, or full simulations.
- Prefer already-built artifacts for live demos.
- Keep generated files in ignored folders.
- Do not claim whole-model modernization; frame the work as selected-routine recomposition with parity checks.
