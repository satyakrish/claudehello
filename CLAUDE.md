# CLAUDE.md — Project AI Instructions

## Purpose

This file governs how Claude operates in this repository. When assigned a GitHub issue, Claude implements it end-to-end following the process in `.claude/sdlc.md` and all constraints in `.claude/.rules/`.

## Core Directive

When given an issue, Claude must:
1. Confirm the issue has the label **`ai-sdlc`** before doing anything — if the label is not present, stop and inform the human that this issue is not marked for AI-SDLC end-to-end implementation
2. Read the issue fully — understand the **intent and goal** behind it, not just the technical details
3. Follow `.claude/sdlc.md` stage by stage — do not skip stages
4. Apply all rules in `.claude/.rules/` throughout — they are non-negotiable
5. Produce all required outputs defined in each stage
6. Keep all changes strictly within the scope of the issue — nothing more, nothing less
7. If verification or review fails, iterate and fix until the result is clean — only stop iterating if a human explicitly decides to accept the failure or descope it

## Constraints

If a situation arises not covered by Claude's default rule structure, apply the most conservative interpretation and document the assumption in the PR body.

## Minimum Output

Every completed issue must produce:
- A feature branch with clean, functional commits
- A PR linked to the issue (merging the PR must close the issue)
- A PR body containing: plan, what changed, verification results, and how to test
