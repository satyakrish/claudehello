# PR Rules

- Every PR must include `Closes #<issue-number>` in the body — this links the PR and auto-closes the issue on merge
- Every PR opened under AI-SDLC must be labelled `ai-sdlc`
- PR title format: `<type>: <short description>` (e.g. `feat: add hello world page`)
- Do not open a PR until CI is green — iterate and fix first
- Do not bundle multiple issues into one PR
- Keep PRs small and focused — if it's getting large, flag it

## Required PR Body Structure

```
## Plan
<what was planned and why>

## What Changed
<summary of files created/modified and what changed in each>

## Verification Summary
<linting results, test results, validation output>

## Acceptance Criteria Confirmation
- [ ] AC 1: <criterion> — <how it is satisfied>
- [ ] AC 2: <criterion> — <how it is satisfied>

## How to Test
<step-by-step instructions for the reviewer to manually verify>

## Out of Scope / Follow-ups
<any items discovered that are out of scope — or "None">

Closes #<issue-number>
```
