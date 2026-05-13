---
name: wrf-fortran-to-python-parity
description: Recompose selected WRF Fortran numerical logic into Python with visible fixtures and parity validation. Use when modernizing a small routine, helper, or calculation path from WRF into Python or a Python service.
---

# WRF Fortran To Python Parity

## Scope

Use this for selected routines or narrow calculation paths only. Do not frame it as rewriting WRF.

## Workflow

1. Identify the exact Fortran source routine and any constants or helper routines it depends on.
2. Define visible input fixtures: CSV, JSON, or sampled NetCDF values.
3. Build or run a tiny Fortran reference fixture using the original routine whenever practical.
4. Implement the Python equivalent with comments mapping formula pieces back to the Fortran.
5. Run Python on the same inputs.
6. Use `wrf-output-parity-compare` to compare outputs with explicit tolerances.
7. State coverage limits and any expected floating-point differences.

## Defaults

- Keep demo files in ignored folders.
- Prefer simple tabular fixtures before service wrappers.
- Preserve units and variable names where possible.
