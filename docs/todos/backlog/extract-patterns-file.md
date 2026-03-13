# Extract patterns into a separate file

## Problem

The ~60 patterns are hardcoded in SKILL.md as part of the prompt text. Adding or tweaking patterns means editing the skill logic itself.

## Approach

- Pull markers out into a structured file (e.g., `patterns.yml` or `markers.txt`), organized by category
- Skill instructions just say "read the patterns file and scan for each one"
- Users can edit the list without touching the skill logic
- Open question: false positive context (like "robust to noise" being legitimate) is currently handled by Claude's judgment — a flat file would need per-pattern context or still rely on Claude's common sense
