---
name: wrf-netcdf-inspection
description: Inspect WRF NetCDF inputs and outputs such as wrfinput, wrfbdy, and wrfout files. Use when binary WRF output cannot be opened directly or the user wants dimensions, variables, units, time records, or sampled values.
---

# WRF NetCDF Inspection

## Workflow

1. Confirm the NetCDF file path and what the user wants to understand.
2. Use `ncdump -h` for dimensions, variables, attributes, and units.
3. Dump small variables such as `Times` or `XTIME` directly.
4. For large variables, create small samples or summaries rather than full dumps.
5. Explain WRF dimensions such as `Time`, `bottom_top`, `south_north`, `west_east`, and staggered dimensions.
6. Save readable `.cdl` or `.csv` outputs in ignored folders when useful.

## Notes

- Do not open binary NetCDF files as text.
- Full variable dumps can be large; sample by time, level, and spatial subset when possible.
- Be explicit whether values are perturbations, full state, staggered fields, or diagnostic fields.
