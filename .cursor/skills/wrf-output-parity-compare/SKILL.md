---
name: wrf-output-parity-compare
description: Compare Fortran/WRF reference output against recomposed Python module, script, or service output. Use when validating output accuracy, numerical parity, tolerances, CSV fixtures, service JSON, or sampled NetCDF variables.
---

# WRF Output Parity Compare

## Workflow

1. Identify the reference output and the recomposed output.
2. Map comparable fields, including units and variable names.
3. Normalize units before comparing.
4. Compute absolute error, relative error where meaningful, max error, and mean error.
5. Apply explicit tolerances. If none are supplied, propose conservative defaults and state them.
6. Produce a pass/fail summary plus rows or variables that exceed tolerance.
7. State coverage limits: fixture size, sampled dimensions, variables compared, and untested behavior.

## Output Format

```markdown
## Parity Summary
[Pass/fail and tolerance used]

## Compared Fields
- [field]: [max abs, max rel, mean abs]

## Failures
- [field/row/value if any]

## Coverage Limits
- [what this comparison does and does not prove]
```
