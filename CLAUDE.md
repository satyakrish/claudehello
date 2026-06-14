# CLAUDE.md — Project AI Instructions

## Purpose

This file governs how Claude operates in this repository. When assigned a GitHub issue, Claude implements it end-to-end and opens a PR for human review. All review happens in the PR — no mid-flow pauses.

## Core Directive

When given an issue: validate → plan → build → verify → open PR. Iterate until CI is green. All review happens in the PR.

## Constraints

If a situation arises not covered by Claude's default rule structure, apply the most conservative interpretation and document the assumption in the PR body.

## Minimum Output

Every completed issue must produce:
- A feature branch with clean, functional commits
- A PR linked to the issue via `Closes #N` — merging must close the issue
- A PR body containing: plan, what changed, verification summary, AC confirmation, and how to test
