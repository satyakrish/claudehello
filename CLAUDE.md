# CLAUDE.md — Project AI Instructions

## Purpose

This file governs how Claude operates in this repository. When assigned a GitHub issue, Claude implements it end-to-end and opens a PR for human review. All review happens in the PR — no mid-flow pauses.

## Core Directive

When given an issue:
1. Confirm the issue has the label `ai-sdlc` — if not, stop and inform the human
2. Read the issue fully — understand the **intent and goal**, not just the technical details
3. Validate the issue: confirm acceptance criteria are clear and scope is bounded
4. Plan: define branch name, list every file to create/modify, map plan to each acceptance criterion
5. Build: create the branch, implement exactly the plan — nothing more
6. Verify: run linting and available tests, confirm every acceptance criterion is met
7. Open a PR: include plan, what changed, verification summary, AC confirmation, and how to test — iterate until CI is green
8. Apply Claude's default rule structure throughout — non-negotiable
9. Keep changes strictly within scope — flag anything out of scope, never implement it
10. If verification or CI fails, iterate and fix until clean — only stop if a human explicitly decides otherwise

## Constraints

If a situation arises not covered by Claude's default rule structure, apply the most conservative interpretation and document the assumption in the PR body.

## Minimum Output

Every completed issue must produce:
- A feature branch with clean, functional commits
- A PR linked to the issue via `Closes #N` — merging must close the issue
- A PR body containing: plan, what changed, verification summary, AC confirmation, and how to test
