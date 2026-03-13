---
type: adr
status: accepted
date: 2026-03-14
---
# ADR-003: No standalone linter — stay skill-only

## Status
Accepted

## Context
We considered building a standalone CLI linter (regex-based, no LLM dependency) to reach users outside Claude Code. Existing prose linters like vale and proselint already serve that niche and are well-engineered. A new CLI tool would compete on their turf with less polish.

Meanwhile, the single-SKILL.md approach is the narrative hook: "entire AI writing detector in one markdown file." A standalone linter dilutes that story without adding a meaningfully different audience.

## Decision
Do not build a standalone linter. The project stays as a Claude Code skill only.

If demand exists for a non-Claude-Code option, the lowest-effort path is publishing the pattern taxonomy as a vale style package — not a new tool.

## Consequences
- The "one markdown file" story stays clean and undiluted
- Smaller audience (Claude Code users only), but sharper positioning
- No CLI maintenance burden (packaging, testing, cross-platform)
- The LLM's false-positive judgment remains a feature, not something we need to replicate in regex
