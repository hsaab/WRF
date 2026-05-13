---
name: wrf-modernization-demo-e2e
description: Orchestrate an end-to-end WRF modernization demo for a selected routine or behavior. Use when the user wants the full flow: architecture, routine trace, Fortran fixture, Python/service recomposition, visible inputs and outputs, and final Fortran-vs-Python accuracy comparison.
---

# WRF Modernization Demo E2E

## Goal

Show a complete modernization loop for one selected WRF behavior. The final proof is inspectable: the same visible inputs go through the original Fortran routine and the Python or service implementation, both raw outputs are preserved, and every comparable output field is checked against the Fortran reference.

## Required User Context

Confirm the target routine or behavior. If unspecified, propose saturation vapor pressure via `phys/module_gfs_funcphys.F` and `fpvs`.

## Workflow

1. Map relevant WRF architecture and call path using `wrf-codebase-map`.
2. Trace the selected routine with `wrf-routine-trace`.
3. Explain the Fortran implementation in modern engineering terms.
4. Optionally run or show a small idealized WRF case as context that the model builds/runs.
5. Optionally inspect NetCDF outputs when useful for context.
6. Build a small visible Fortran fixture using the real WRF routine.
7. Produce readable shared inputs, Fortran raw outputs, and a short variable/unit map.
8. Recompose the selected logic into Python or a small Python service.
9. Run the Python/service implementation on the exact same inputs.
10. Preserve Python/service raw outputs. For a service, also preserve the request body and response body.
11. Compare Python/service output against Fortran output with `wrf-output-parity-compare`.
12. End with a parity report: pass/fail, per-row/per-field deltas, max/mean deltas, tolerance failures, coverage limits, and risks.

## Evidence Requirements

Make the demo easy to audit without trusting the narrative.

- Keep the canonical input fixture in a human-readable format such as CSV or JSON.
- Preserve raw Fortran output and raw Python/service output as separate files.
- Include every input field, every compared output field, units, and precision/format notes.
- Include a side-by-side comparison artifact with one row per case and one delta per compared numeric field.
- If the Python target is a service, show the service contract: endpoint, request schema, response schema, sample request, and sample response.
- In the final explanation, cite the Fortran source routine, explain the translated calculation in plain engineering terms, and link to the generated input/output artifacts.

## Final Output Requirements

Include clickable links to the evidence files so a reviewer can open them directly.

- Link the shared input fixture.
- Link the Fortran reference driver and raw Fortran output.
- Link the Python module or service code and raw Python/service output.
- Link service request/response examples when present.
- Link the side-by-side comparison artifact and final parity report.
- State whether artifacts are ignored demo files or intended source changes.

## Defaults

- Routine: saturation vapor pressure, `fpvs`.
- Fixture style: CSV input and CSV output.
- Service style: JSON request/response plus CSV or JSON parity artifacts.
- Idealized case: `em_b_wave`.
- Output inspection: NetCDF header, time records, and selected variable samples.

## Guardrails

- Ask before long builds, MPI runs, or full simulations.
- Prefer already-built artifacts for live demos.
- Keep generated files in ignored folders.
- Do not claim whole-model modernization; frame the work as selected-routine recomposition with parity checks.
