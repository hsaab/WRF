---
name: wrf-routine-trace
description: Trace a named WRF scientific routine, physics concept, or namelist option through Fortran source, callers, drivers, and scheme-specific implementations. Use for questions like saturation vapor pressure, microphysics tendencies, radiation, PBL, or physics option routing.
---

# WRF Routine Trace

## Workflow

1. Restate the target routine or concept and likely synonyms.
2. Search for shared utilities, driver calls, and scheme-local copies.
3. Read implementations before summarizing; do not assume one canonical routine.
4. Trace callers upward to drivers or solver code, and trace inputs back to grid state, Registry fields, or namelist flags.
5. Identify units, dimensions, constants, valid ranges, and numerical approximations.
6. Report source-of-truth candidates and explain which implementation matters for the user's target path.

## Output Format

```markdown
## Target
[Routine or concept]

## Implementations
- `path`: [shared utility, driver, or scheme-local copy]

## Call Path
`caller` -> `driver` -> `routine`

## Inputs And Outputs
- [variable]: [units/dimensions/meaning]

## Notes
- [constants, approximations, caveats]
```
