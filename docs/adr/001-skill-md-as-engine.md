---
type: adr
status: accepted
date: 2026-03-14
---
# ADR-001: Implement detection engine as a single SKILL.md file

## Status
Accepted

## Context
The project needs a way to scan prose for AI writing patterns. Traditional approaches would involve writing a CLI tool, a Python script, or a browser extension with regex matching. However, the project targets Claude Code users and the irony of an LLM reading instructions to detect LLM writing is part of the appeal.

## Decision
The entire detection engine is a SKILL.md file — a Claude Code skill definition that instructs Claude to use Grep against project files for ~60 known patterns. No code, no dependencies, no build step.

## Consequences
- Zero installation friction: copy one file
- The LLM handles false-positive judgement calls that would be hard to encode in regex (e.g., "robust to noise" vs "robust solution")
- Tied to Claude Code as the runtime — won't work outside it
- Detection quality depends on the model following instructions faithfully
- The single-file constraint is a feature for the blog article narrative
