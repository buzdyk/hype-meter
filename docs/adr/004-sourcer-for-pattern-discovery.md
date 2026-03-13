---
type: adr
status: accepted
date: 2026-03-14
---
# ADR-004: Add a sourcer component to iterate on pattern discovery

## Status
Accepted

## Context
The skill's ~60 patterns are a hand-curated first iteration — rigid preset keywords. To evolve the pattern list beyond what a human would think to add, we need a way to systematically discover new patterns from real data. Where and how to source them is TBD, but the need for a dedicated component is clear.

## Decision
Add a sourcer component to the project. Its job is to iterate on the pattern list: analyze corpora of AI-written vs human-written text and surface candidate patterns for inclusion in the skill. This makes the repository a monorepo with two distinct concerns — detection (skill) and discovery (sourcer).

## Consequences
- The pattern list becomes a living artifact fed by research, not just a static checklist
- Justifies the monorepo structure: sourcer produces patterns, skill consumes them
- The sourcer's methods (TBD — probes, stylometrics, frequency analysis) are independent of the skill's execution model
- Separates "what to look for" (hard problem, needs ML) from "how to look" (simple, stays in SKILL.md)
- Adds real project scope — this is no longer just a one-file gag
