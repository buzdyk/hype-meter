# User override patterns

## Problem

Some domains use flagged terms legitimately (e.g., "robust" in signal processing). Users can't exclude patterns without forking the whole skill.

## Approach

- Look for a local `.hype-patterns` file in the project root
- Support adding or removing markers from the default set
- Keep the default ~60 patterns as the baseline, overrides layer on top
