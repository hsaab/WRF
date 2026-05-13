# Bugbot WRF Review

When reviewing WRF changes, prioritize findings that can change numerical behavior, build portability, generated-code correctness, or model output reproducibility.

For Fortran/C scientific-code changes:

- Check whether the change affects physics, dynamics, Registry fields, generated includes, namelist options, or I/O formats.
- Verify formulas, constants, units, dimensions, and valid ranges when numerical logic changes.
- Look for unintended behavior changes from source-form preprocessing, missing `-D`/`-I` flags, generated include ordering, or CMake/configure changes.
- Require focused verification for the touched path: a unit-style fixture, idealized case smoke run, or explicit parity comparison against prior Fortran output.
- Flag generated artifacts accidentally added to a PR, including `_build*`, `install*`, `wrfout*`, `wrfinput*`, `*.o`, `*.mod`, `*.exe`, `*.nc`, and `rsl.*`.
- For recomposed Python or service logic, verify output parity against the Fortran reference with documented tolerances and coverage limits.
- Prefer findings with concrete scientific or engineering blast radius: wrong units, changed state dimensions, broken build path, altered physics option behavior, or unverified numerical drift.

For Python microservices that recompose WRF behavior:

- Verify the service uses the same source-of-truth formula, constants, phase logic, lookup-table behavior, and units as the referenced Fortran routine.
- Check for Celsius/Kelvin mistakes, pressure unit mistakes (`Pa` vs `hPa`), mixing ratio vs specific humidity confusion, and relative humidity expressed as fraction vs percent.
- Require a visible Fortran reference fixture and a parity test that runs the Python implementation on the same inputs.
- Flag tests that only assert response shape, status codes, or broad ranges without comparing against Fortran reference output.
- Flag tolerances that are too loose to catch scientific regressions, or tolerance checks that compare rounded strings instead of numeric values.
- Confirm edge cases are covered around phase transitions, saturation limits, freezing temperatures, very warm temperatures, low/high pressure, and invalid inputs.
- Check that API validation preserves scientific meaning: reject ambiguous units, require documented input units, and avoid silent default conversions.
- Do not accept a claim of parity unless the PR reports compared fields, max/mean absolute error, max relative error where meaningful, tolerances, failures, and coverage limits.
- Make demo findings concrete. A good finding points to a specific request/fixture row where Python output diverges from Fortran enough to change a humidity, saturation, or tendency calculation.
- Do not invent demo findings. If the seeded issue is not supported by the PR diff, fixture output, or tests, report that no concrete issue was found and name any remaining review gaps.
