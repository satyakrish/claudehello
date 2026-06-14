# Coding Rules

- No placeholder or TODO code in committed files
- No hardcoded secrets, tokens, API keys, or passwords
- No direct commits to `main` — always use a feature branch
- Branch naming: `issue-<number>-<short-description>`
- Commit messages must reference the issue: `<type>: <description> (refs #N)`
- One concern per commit — do not bundle unrelated changes
- Remove all debug/console output before committing
- Every PR must include `Closes #<issue-number>` in the PR body — this links the PR to the issue and automatically closes it on merge
- Do not open a PR without `Closes #N` — the issue must be closed by the merge, not manually
