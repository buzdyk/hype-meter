---
type: adr
status: accepted
date: 2026-03-14
---
# ADR-002: Position as a style linter, not an AI detector

## Status
Accepted

## Context
The space of "AI content detection" is crowded with statistical classifiers (GPTZero, etc.) that try to guess authorship via perplexity and burstiness. These tools are controversial, often inaccurate, and frame the problem as binary (human vs AI).

## Decision
hype-check is a linter, not a classifier. It doesn't try to determine authorship. It greps for ~60 known phrasing tics and reports a density score. The framing is closer to a style checker (like a prose linter) than an AI detector.

## Consequences
- Avoids the accuracy debates around statistical AI detection
- The output is actionable — you can find and fix specific phrases
- Doesn't make claims about who wrote what, just flags patterns
- Fresh framing for HN / blog audience who've seen plenty of GPTZero-style tools
- Won't catch AI text that avoids these specific tics (by design — it's not trying to)
