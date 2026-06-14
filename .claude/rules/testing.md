# Testing & Verification Rules

- Always verify before opening a PR — never open a PR on unverified code
- Run all available linting, validation, and tests for the project
- If linting fails, fix it — do not open the PR with lint errors
- If tests fail, fix them — do not open the PR with failing tests
- If no test tooling is available locally, document this explicitly in the PR body and confirm CI will cover it
- The verification summary in the PR body must include: what was run, the result, and confirmation each AC is met
- If verification or CI fails after the PR is open, fix and push — do not leave a PR in a failing state
