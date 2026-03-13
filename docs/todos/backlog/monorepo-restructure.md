# Monorepo restructure

## Problem

ADR-004 introduces a sourcer component alongside the skill. The repo needs a top-level structure that separates the two concerns while sharing the pattern list as a common artifact.

## Approach

- Move skill files under `skill/`
- Create `sourcer/` directory
- Pattern list lives at a shared location both components reference
