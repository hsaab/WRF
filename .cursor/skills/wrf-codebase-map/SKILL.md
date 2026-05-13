---
name: wrf-codebase-map
description: Map WRF repository architecture, execution flow, and major Fortran/C subsystems. Use when the user asks where behavior lives, how WRF starts, how dynamics calls physics, or how Registry/generated code fits in.
---

# WRF Codebase Map

## Workflow

1. Identify the executable or workflow: `wrf`, `ideal`, `real`, `ndown`, or a specific test case.
2. Trace from `main/` into `frame/`, `share/`, `dyn_em/`, and `phys/`.
3. Include Registry/configuration when namelist options, state arrays, generated includes, or package fields are involved.
4. Separate source code from generated `inc/`, build directories, installed test copies, and runtime outputs.
5. Return a concise map with file paths, subroutine/module names, and a call-chain summary.

## Common Anchors

- Forecast entrypoint: `main/wrf.F`
- Top-level run orchestration: `main/module_wrf_top.F`
- Time loop: `frame/module_integrate.F`
- Solver bridge: `share/solve_interface.F`
- ARW dynamics: `dyn_em/solve_em.F`
- Physics drivers and schemes: `phys/`
- Configuration and generated interfaces: `Registry/`, `tools/registry.c`, `inc/`
