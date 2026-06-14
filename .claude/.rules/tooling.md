# Tooling Rules

## Tool Preference Order

When performing any action, prefer tools in this order to optimise token usage and reliability:

1. **CLI** (e.g. `gh`, `git`, `npm`) — fastest, lowest token cost, prefer always
2. **API** (e.g. GitHub REST API via curl or PowerShell) — use when CLI is unavailable or the operation is not supported by CLI
3. **MCP Server** — use only when CLI and API cannot accomplish the task

Never use a higher-cost tool when a lower-cost one can do the job.
