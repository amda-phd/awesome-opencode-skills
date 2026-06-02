# Release Notes — v1.1.0

**Released**: June 2, 2026

## Highlights

This release completes a thorough audit of the entire skill collection, eliminating all remaining Claude/Anthropic branding references, fixing description format issues, and ensuring every skill is properly registered and documented.

## New Skills

### Staff Engineer Review
Performs deep code review of pull requests as a Staff+ level engineer, evaluating alignment with plans, architecture decisions, code quality, correctness, performance, and test coverage. Provides actionable, prioritized feedback.

### Code Security Auditor
Performs pre-execution security audits of untrusted codebases through static analysis. Identifies supply chain risks, detects potentially malicious patterns, and flags security vulnerabilities before code is run locally.

## Branding Cleanup

All remaining Claude/Anthropic references have been replaced with OpenCode equivalents across the entire collection:

- **artifacts-builder** — "claude.ai HTML artifacts" → "OpenCode HTML artifacts"
- **developer-growth-analysis** — `~/.claude/history.jsonl` → `~/.config/opencode/history.jsonl`
- **document-skills/docx** — `w:author="Claude"` → `w:author="OpenCode"` in tracked change examples
- **mcp-builder** — Replaced `anthropic` SDK references, `ANTHROPIC_API_KEY`, and Claude model names
- **skill-creator** — "AI capabilities" → "OpenCode capabilities"

## Skills Registry

The `.opencode/skills.json` registry has been expanded from **9 to 30 skills**, adding all missing entries across every category:

| Category | Skills Added |
|----------|-------------|
| Development | developer-growth-analysis, mcp-builder, skill-creator, staff-engineer-review |
| Business & Marketing | competitive-ads-extractor, domain-name-brainstormer, internal-comms, lead-research-assistant |
| Communication & Writing | content-research-writer, meeting-insights-analyzer |
| Creative & Media | canvas-design, image-enhancer, slack-gif-creator, video-downloader |
| Productivity & Organization | file-organizer, invoice-organizer, raffle-winner-picker |
| Collaboration | skill-share |
| Security & Systems | code-security-auditor |

## Description Format Fixes

- Removed unnecessary quotes around description values in docx, pptx, xlsx SKILL.md files
- Rewrote internal-comms description from first-person ("help me write") to third-person ("help users write")

## Path Convention Documentation

Updated all documentation to reflect that OpenCode discovers skills from both:
- `.opencode/skills/` (official, recommended) and `.opencode/skill/` (also supported)
- `~/.config/opencode/skills/` (global, recommended) and `~/.config/opencode/skill/` (global, also supported)
- `.claude/skills/` (backward compatible for migration)

## Full Changelog

See [CHANGELOG.md](./CHANGELOG.md) for complete details.
