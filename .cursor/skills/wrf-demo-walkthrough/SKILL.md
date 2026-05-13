---
name: wrf-demo-walkthrough
description: Produce a concise engineer-facing walkthrough of a WRF investigation, run, recomposition, parity comparison, or build fix. Use when preparing to explain the workflow to engineering stakeholders.
disable-model-invocation: true
---

# WRF Demo Walkthrough

## Inputs To Gather

- User goal or engineering question.
- Source files or routines investigated.
- Build/run commands or fixtures used.
- Output artifacts inspected.
- Parity comparison results, if any.
- Risks, assumptions, and coverage limits.

## Output Format

```markdown
## What We Investigated
[Two or three sentences.]

## What Cursor Helped Do
- [Comprehension, tracing, build/run, recomposition, comparison]

## Evidence
- Source: `path`
- Run/output: `path`
- Comparison: [summary]

## Talk Track
1. [Step]
2. [Step]
3. [Step]

## Limits
- [Coverage or risk]
```
