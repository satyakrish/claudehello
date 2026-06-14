# SDLC.md — Issue Implementation Process

This document defines the end-to-end process Claude must follow when implementing any GitHub issue in this repository. Claude runs all stages autonomously in one flow — no mid-flow pauses or approvals. All review happens in the PR.

---

## Stage Sequence

```
Stage 1: Understand
    ↓
Stage 2: Plan
    ↓
Stage 3: Build
    ↓
Stage 4: Verify
    ↓
Stage 5: PR (plan + implementation included in PR body)
    ↓
Stage 6: Handoff (you review and merge)
```

---

## Stage Definitions

### Stage 1 — Understand
**Goal:** Validate the issue for AI-SDLC eligibility and fully understand it before writing any code.

**Actions:**
- **First:** Check that the issue has the label `ai-sdlc` — if not, stop immediately and inform the human; do not proceed
- Read the issue title, body, and all comments
- Understand the **intent and goal** behind the issue, not just the technical surface
- Identify: what needs to be built, acceptance criteria, out-of-scope items
- If anything is ambiguous, state the assumption clearly and continue — do not pause

**Required Output:**
- Confirmation that the `ai-sdlc` label is present
- Internal summary of what will be implemented (carried into Stage 2)
- List of files to be created or modified
- Explicit list of what is OUT of scope

---

### Stage 2 — Plan
**Goal:** Design the full approach before touching any file.

**Actions:**
- Define the branch name: `issue-<number>-<short-description>`
- List every file to create or modify and what changes go in each
- Note any new dependencies being introduced
- Identify how each acceptance criterion will be satisfied

**Required Output:**
- Written plan (included verbatim in the PR body under "## Plan")
- Branch name confirmed

---

### Stage 3 — Build
**Goal:** Implement exactly what was planned in Stage 2.

**Actions:**
- Create feature branch from `main`
- Implement changes file by file per the plan
- Follow all rules in `.claude/rules/`
- Do not add anything beyond the plan

**Required Output:**
- All planned files created/modified
- No TODOs, placeholders, or hardcoded secrets
- Code is functional and complete

---

### Stage 4 — Verify
**Goal:** Confirm the implementation works before opening the PR.

**Actions:**
- Run available tests or validation commands
- Confirm each acceptance criterion is met
- Check for lint or CI failures

**Required Output:**
- Verification summary (included in PR body under "## Verification")
- Confirmation each acceptance criterion is satisfied

---

### Stage 5 — PR
**Goal:** Open a clean, reviewable PR that includes the plan and verification.

**Actions:**
- Commit all changes with clear messages referencing the issue
- Open PR against `main` with the following body structure:

```
## Plan
<the plan from Stage 2>

## What Changed
<summary of what was implemented>

## Verification
<verification results from Stage 4>

## How to Test
<steps for the reviewer to manually verify>

Closes #<issue-number>
```

**Required Output:**
- PR opened with CI green
- PR body contains plan, implementation summary, verification, and how-to-test
- Issue linked via `Closes #N`

---

### Stage 6 — Handoff & Human Review
**Goal:** Hand off the PR cleanly, support the human review cycle, and reach a mergeable state.

**What handoff means:**
Claude's autonomous build is complete. The PR is open, CI is green, and all implementation decisions are documented in the PR body. From this point, the human drives — Claude responds to review feedback until the PR is merged or explicitly closed.

**Actions (Claude at handoff):**
- Post a PR comment summarising what was done and flagging anything the reviewer should pay attention to
- Document any post-merge manual steps (e.g. enable GitHub Pages, set env vars) in the PR body under "## Post-Merge Steps"
- Do NOT create follow-up issues unless the human explicitly asks for one

**Actions (You — the reviewer):**
- Read the plan and implementation in the PR body
- Review the code changes
- Approve and merge, or request changes

---

## Human Review & Feedback Handling

When you leave review comments on the PR, Claude must:

1. **Read every comment** before making any change
2. **Apply all in-scope feedback** within the current PR — do not defer in-scope items
3. **For each comment addressed**, post a reply on that specific comment explaining exactly what was done — if a single comment contains multiple points, address each point individually in the reply (e.g. "1. Updated `index.html` line 12 to use semantic `<main>` tag. 2. Removed inline style and moved to `style.css` line 8.")
4. **Do not create a new issue** for a feedback item unless you explicitly say so (e.g. "create an issue for this") — if you do say so, Claude creates the issue and links it in a reply to that comment
5. **If feedback is out of scope**, Claude replies on the comment explaining why it is out of scope and asks whether to create a new issue or ignore it — it does not act until you decide
6. **After all feedback is addressed**, Claude re-runs Stage 4 (Verify) to confirm nothing broke, then re-requests review

This cycle repeats until you merge or explicitly close the PR.

---

## Scope Control

- If during Build something outside the plan is needed, Claude flags it in the PR body under "## Out of Scope / Follow-ups" — it does not implement it
- New issues are only created when explicitly requested by the human — never proactively by Claude
