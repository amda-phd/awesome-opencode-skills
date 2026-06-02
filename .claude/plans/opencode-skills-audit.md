# OpenCode Skills Audit & Update Plan

## Branch: `feat/opencode-skills-audit`

## Summary of Findings

After cloning, rebasing, and auditing the repository, here are the issues found:

### 1. Remaining Claude/Anthropic References (BRANDING — Replace All)

| File | Line(s) | Issue |
|------|---------|-------|
| `artifacts-builder/SKILL.md` | L3 (description) | Says "claude.ai HTML artifacts" → should be "opencode.ai HTML artifacts" |
| `artifacts-builder/SKILL.md` | L9 | Says "claude.ai artifacts" → "opencode.ai artifacts" |
| `developer-growth-analysis/SKILL.md` | L65 | References `~/.claude/history.jsonl` → should use `~/.config/opencode/history.jsonl` or equivalent |
| `document-skills/docx/ooxml.md` | L16, L559, L572, L581 | Uses `w:author="Claude"` in tracked changes examples → change to `"OpenCode"` |
| `mcp-builder/reference/evaluation.md` | L392, L398, L557 | References `pip install anthropic` and `ANTHROPIC_API_KEY` → update to OpenCode equivalents |
| `README.md` | L541 | Links to "Lenny's Newsletter" article about "claude-code" |
| `README.md` | L542 | Links to "Notion Skills for Claude" |

### 2. Incomplete skills.json Registry

`.opencode/skills.json` only registers **9 of 30** skills. Missing skills:
- developer-growth-analysis
- competitive-ads-extractor
- content-research-writer
- domain-name-brainstormer
- internal-comms
- lead-research-assistant
- meeting-insights-analyzer
- file-organizer
- invoice-organizer
- raffle-winner-picker
- skill-creator
- skill-share
- slack-gif-creator
- staff-engineer-review
- theme-factory
- video-downloader
- image-enhancer
- canvas-design
- code-security-auditor

### 3. Description Format Issues

- `document-skills/docx/SKILL.md` — description wrapped in quotes
- `document-skills/pptx/SKILL.md` — description wrapped in quotes
- `document-skills/xlsx/SKILL.md` — description wrapped in quotes
- `artifacts-builder/SKILL.md` — description still says "claude.ai"
- `internal-comms/SKILL.md` — description uses first-person ("help me write") instead of third-person

### 4. Path Convention Inconsistency

The repo documents `.opencode/skill/` (singular) but OpenCode officially uses `.opencode/skills/` (plural). Per user decision: **support both paths** in documentation.

### 5. Missing README Entries

- `developer-growth-analysis` — exists as a skill directory but isn't listed in the README's Skills section
- `skill-share` — exists as a skill directory but isn't listed in the README's Skills section

### 6. Minor Issues

- `mcp-builder/reference/evaluation.md` references `anthropic` SDK as the evaluation client — needs replacement with OpenCode-compatible evaluation approach
- `skill-creator/SKILL.md` says "AI capabilities" where it should say "OpenCode capabilities"

---

## Implementation Plan

### Step 1: Create feature branch from master
```
git checkout master
git checkout -b feat/opencode-skills-audit
```

### Step 2: Fix Claude/Anthropic branding references in all SKILL.md files

**2a.** `artifacts-builder/SKILL.md`
- Replace "claude.ai" with "opencode.ai" in description and body

**2b.** `developer-growth-analysis/SKILL.md`
- Replace `~/.claude/history.jsonl` with `~/.config/opencode/history.jsonl` (or the OpenCode equivalent path)
- Update any other Claude-specific references in the body

**2c.** `document-skills/docx/ooxml.md`
- Replace `w:author="Claude"` with `w:author="OpenCode"` in tracked change examples

**2d.** `mcp-builder/reference/evaluation.md`
- Replace `pip install anthropic mcp` with OpenCode-compatible evaluation instructions
- Replace `ANTHROPIC_API_KEY` environment variable references with `OPENCODE_API_KEY` or equivalent
- Update evaluation scripts to use OpenCode client instead of Anthropic SDK

**2e.** `skill-creator/SKILL.md`
- Replace "AI capabilities" with "OpenCode capabilities"

### Step 3: Fix description format issues

**3a.** `document-skills/docx/SKILL.md` — remove quotes around description value
**3b.** `document-skills/pptx/SKILL.md` — remove quotes around description value
**3c.** `document-skills/xlsx/SKILL.md` — remove quotes around description value
**3d.** `internal-comms/SKILL.md` — rewrite description in third-person

### Step 4: Update `.opencode/skills.json`

Add all 21 missing skill entries with proper categories:
- Development: developer-growth-analysis, staff-engineer-review, skill-creator
- Business & Marketing: competitive-ads-extractor, domain-name-brainstormer, lead-research-assistant
- Communication & Writing: content-research-writer, meeting-insights-analyzer, internal-comms
- Creative & Media: canvas-design, image-enhancer, slack-gif-creator, theme-factory, video-downloader
- Productivity & Organization: file-organizer, invoice-organizer, raffle-winner-picker
- Development: skill-share, code-security-auditor, mcp-builder

### Step 5: Update README.md

**5a.** Add missing skills to the appropriate categories:
- `developer-growth-analysis` → Data & Analysis (or Development & Code Tools)
- `skill-share` → Collaboration & Project Management

**5b.** Update "Resources" links:
- Replace the Lenny's Newsletter link (claude-code reference) with an OpenCode equivalent or remove
- Update Notion Skills link reference from "for Claude" to "for OpenCode" or remove

### Step 6: Update path convention documentation

In `README.md`, `OPENCODE_SKILLS.md`, and `MIGRATION.md`, document that OpenCode discovers skills from:
- `.opencode/skills/` (official plural form)
- `.opencode/skill/` (also supported, singular)
- `~/.config/opencode/skills/` (global)
- `~/.config/opencode/skill/` (global, also supported)
- Backward compatible: `.claude/skills/` (for migration)

### Step 7: Commit with clear messages

Each logical group gets its own commit:
1. `fix: replace remaining Claude/Anthropic branding references`
2. `fix: clean up SKILL.md description format issues`
3. `feat: add missing skills to .opencode/skills.json registry`
4. `docs: add missing skills to README and update resource links`
5. `docs: document both .opencode/skill/ and .opencode/skills/ paths`

---

## Skills to Update (Full Checklist)

| # | Skill | Changes Required |
|---|-------|-----------------|
| 1 | artifacts-builder | Replace "claude.ai" in description + body |
| 2 | brand-guidelines | ✅ No changes needed |
| 3 | canvas-design | ✅ No changes needed |
| 4 | changelog-generator | ✅ No changes needed |
| 5 | code-security-auditor | ✅ No changes needed |
| 6 | competitive-ads-extractor | ✅ No changes needed |
| 7 | content-research-writer | ✅ No changes needed |
| 8 | developer-growth-analysis | Replace `~/.claude/` path reference |
| 9 | document-skills/docx | Remove quotes from description, fix ooxml.md author |
| 10 | document-skills/pdf | ✅ No changes needed |
| 11 | document-skills/pptx | Remove quotes from description |
| 12 | document-skills/xlsx | Remove quotes from description |
| 13 | domain-name-brainstormer | ✅ No changes needed |
| 14 | file-organizer | ✅ No changes needed |
| 15 | image-enhancer | ✅ No changes needed |
| 16 | internal-comms | Rewrite description in third-person |
| 17 | invoice-organizer | ✅ No changes needed |
| 18 | lead-research-assistant | ✅ No changes needed |
| 19 | mcp-builder | Update evaluation.md: replace anthropic SDK references |
| 20 | meeting-insights-analyzer | ✅ No changes needed |
| 21 | raffle-winner-picker | ✅ No changes needed |
| 22 | skill-creator | Replace "AI capabilities" with "OpenCode capabilities" |
| 23 | skill-share | ✅ No changes needed |
| 24 | slack-gif-creator | ✅ No changes needed |
| 25 | staff-engineer-review | ✅ No changes needed |
| 26 | template-skill | ✅ No changes needed (placeholder) |
| 27 | theme-factory | ✅ No changes needed |
| 28 | video-downloader | ✅ No changes needed |
| 29 | webapp-testing | ✅ No changes needed |

## Files Outside Skills That Need Changes

| File | Changes |
|------|---------|
| `.opencode/skills.json` | Add 21 missing skill entries |
| `README.md` | Add missing skills, update resource links |
| `OPENCODE_SKILLS.md` | Document both path conventions |
| `MIGRATION.md` | Document both path conventions |
