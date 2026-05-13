---
name: wrf-idealized-run
description: Configure, build, run, and inspect a small WRF idealized case without WPS or real-weather data. Use when the user wants a local WRF smoke test, idealized run, or build/run troubleshooting.
---

# WRF Idealized Run

## Workflow

1. Confirm the case and runtime target. Prefer `em_b_wave`, `em_grav2d_x`, or `em_quarter_ss` for quick proof.
2. Check toolchain: `gfortran`, `cmake`, `nc-config`, `nf-config`; check `mpif90` only for MPI builds.
3. Use ignored build/install folders, for example `_build_<case>` and `install_<case>`.
4. Configure with the narrowest viable options; avoid MPI/OpenMP unless requested.
5. Build and install `ideal` and `wrf`.
6. Shorten `namelist.input` in the installed/ignored test copy for smoke runs.
7. Run `./ideal`, then `./wrf`.
8. Inspect outputs with `ncdump`, not by opening NetCDF binaries directly.

## Safety

- Ask before long builds or multi-hour simulations.
- Do not edit source test-case namelists unless requested.
- Do not stage generated files such as `_build*`, `install*`, `wrfinput*`, `wrfout*`, `rsl.*`, binaries, `.o`, or `.mod`.
