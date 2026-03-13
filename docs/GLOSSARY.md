# Glossary

## Services

| Term | Definition |
|------|------------|
| Claude Code | Anthropic's CLI for Claude, provides the skill execution runtime |
| hype-check | The skill itself — a SKILL.md file that instructs Claude to grep for AI writing tics |

## Data Entities

| Term | Definition |
|------|------------|
| Hype marker | One of ~60 phrasing patterns across 6 categories that indicate AI-generated prose |
| Hype density | Total hype matches divided by total files scanned — the core metric |
| Pattern category | One of 6 groups: dramatic framers, filler authority, corporate buzzwords, AI reviewer voice, fake-casual, breathless structure |
| Hall of Shame | The 5-8 most egregious matched quotes in a scan report |

## Infrastructure

| Term | Definition |
|------|------------|
| SKILL.md | A Claude Code skill definition file — the entire detection engine lives in this single markdown file |
| Grep | The primary tool used by the skill to match patterns against project prose |
