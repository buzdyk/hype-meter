---
description: Scan project docs, specs, and prose for AI-flavoured writing tics and report a hype level
allowed-tools: Bash, Read, Glob, Grep
---

# Hype Check

Scan the project for AI-generated writing patterns — the kind of phrasing that screams "an LLM wrote this." Report an overall hype level with categorized examples.

## Step 0: Find scannable content

Before searching for patterns, determine what to scan. Look for written prose in the project directory:

1. Documentation files: `.md`, `.txt`, `.rst`, `.adoc` (anywhere in the project tree)
2. Doc directories: `docs/`, `doc/`, `wiki/`, `specifications/`, `specs/`
3. Extensive code comments: if no standalone doc files exist, scan source files for block comments and docstrings

Use Glob to discover what's available. Exclude `node_modules/`, `vendor/`, `.git/`, `dist/`, `build/`, and other dependency/generated directories.

**If fewer than 3 files with prose content are found**, report early:

```
## Hype Check: Skipped

Not enough written content to scan. Found N file(s) with prose.
This skill needs documentation files (.md, .txt, .rst, .adoc), spec documents,
or source files with extensive comments to work with.
```

Otherwise, proceed with the discovered files as the scan target.

## Step 1: Search for hype patterns

Use Grep against the discovered files for each pattern category below. Run searches in parallel where possible.

### Pattern categories

**Dramatic framers** — phrases that manufacture tension or revelation:
- `fundamentally`, `the key insight`, `the killer feature`
- `this is where it gets (interesting|tricky|complicated)`
- `it turns out`, `the (uncomfortable|inconvenient|hard|honest|real) truth`
- `here's the (thing|deal|kicker|catch|rub)`
- `let that sink in`, `read that again`
- `make no mistake`, `to be clear`
- `spoiler:`, `plot twist`, `hot take`, `reality check`

**Filler authority** — words that sound authoritative but add nothing:
- `fundamentally`, `crucially`, `importantly`, `notably`, `essentially`
- `in essence`, `at the end of the day`, `the bottom line`
- `it's worth noting`, `worth (mentioning|highlighting|emphasizing|calling out)`
- `I cannot stress this enough`, `this cannot be overstated`

**Corporate buzzwords** — words fine in moderation, suspicious in quantity:
- `leverage`, `robust`, `scalable`, `seamless`, `streamline`
- `ecosystem`, `unlock`, `empower`, `harness`
- `paradigm`, `synerg(y|ies|istic)`, `holistic`
- `north star`, `low-hanging fruit`, `move the needle`

**AI reviewer voice** — the "thoughtful analysis" tell:
- `shows someone thinking`, `well-motivated`, `correctly drawn`, `the right call`
- `not just X, (but|it) Y` (the classic AI contrast frame)
- `the strongest area`, `this is (huge|critical|a game)`
- `elegantly`, `beautifully`, `brilliantly`

**Fake-casual** — forced conversational tone:
- `let's be (honest|real|clear|frank)`
- `bear with me`, `what if I told you`
- `real talk`, `unpopular opinion`, `won't lie`
- `and that's (okay|ok|fine|the point|exactly)`

**Breathless structure** — AI's favourite rhetorical moves:
- `deep dive`, `a (concrete|real|practical|simple) example`
- `sweet spot`, `battle-tested`, `game-changer`
- `the elephant in the room`, `double-edged sword`, `silver bullet`
- `tip of the iceberg`, `rabbit hole`, `wake-up call`

## Step 2: Tally and categorize

For each pattern category:
1. Count total matches across all files
2. Note which files have the most hits
3. Collect 2-3 representative quotes (with file path and line number)

Ignore legitimate technical uses — "robust to crops" in a hashing doc is fine, "robust solution" as generic praise is hype. Use judgement.

## Step 3: Compute hype level

Calculate a hype density: `total_hype_matches / total_doc_files_scanned`.

Rate the project:

| Density | Level | Verdict |
|---------|-------|---------|
| < 0.5 | **Clean** | Reads like a human wrote it |
| 0.5–1.5 | **Mild** | A few tells, mostly fine |
| 1.5–3.0 | **Sus** | AI ghostwriter energy |
| 3.0–5.0 | **Cooked** | Corporate keynote cosplay |
| > 5.0 | **Terminal** | The docs have achieved sentience |

## Step 4: Report

Print the report in this format:

```
## Hype Check: <Level>

Scanned N files. Found M hype markers (density: X.X per file).

### Breakdown

| Category | Hits | Worst offenders |
|----------|------|-----------------|
| Dramatic framers | N | file.md, file.md |
| Filler authority | N | ... |
| Corporate buzzwords | N | ... |
| AI reviewer voice | N | ... |
| Fake-casual | N | ... |
| Breathless structure | N | ... |

### Hall of Shame

> "quote here"
> — `path/to/file.md:42`

> "quote here"
> — `path/to/file.md:17`

(list the 5-8 most egregious examples)

### Cleanest files

List 3-5 doc files that had zero or minimal hits — credit where it's due.
```

## Rules

- Scan documentation files and prose content — not raw source code logic, configs, or vendor/dependency files
- If scanning source files for comments, only match within comment blocks, not code
- Don't count the same line twice across overlapping patterns
- Use judgement on false positives — technical terms used correctly aren't hype
- Keep the tone dry and slightly amused, not preachy
- No suggestions for fixes — this is a diagnostic, not a rewrite
