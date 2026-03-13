# Source weird phrases for pattern list

## Problem

The current ~60 patterns are greppable regex-style strings. That undermines the AI angle — if the detection is just regex, why use an LLM? The pattern list needs entries that are genuinely hard to match mechanically: semantic tics, structural patterns, tonal signatures that only make sense in context.

## Approach

- Mine LLM output at scale for phrases that are statistically overrepresented vs human writing
- Look for patterns that need context to evaluate (e.g., sentence-level rhythm, hedging-then-asserting combos)
- Pull from existing research on LLM linguistic fingerprints (stylometric studies, token frequency analysis)
- The 60 patterns are fine as a first iteration — this is about what comes next
- Goal: patterns that justify the LLM-as-detector approach because regex genuinely can't catch them
