# Branching Rules

- Never commit directly to `main` — all work happens on a feature branch
- Branch naming: `issue-<number>-<short-description>` (e.g. `issue-2-hello-world-page`)
- Always branch from the latest `main`
- Commit message format: `<type>: <description> (refs #<issue-number>)` (e.g. `feat: add hello world page (refs #2)`)
- One concern per commit — do not bundle unrelated changes
- Remove all debug output before committing
