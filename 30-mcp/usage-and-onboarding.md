# MCP Usage and Onboarding

## Onboarding Checklist

1. Decide which MCPs are global defaults versus repo-specific tools.
2. Install the local runtimes they need, such as `npx`, `uvx`, or browser dependencies.
3. Add MCP entries using placeholders or env vars, not hard-coded secrets.
4. Restart Codex after MCP changes.
5. Validate each MCP with one safe smoke query.
6. Document only the MCPs that matter to the repo or skill.

## When to Use Which MCP

### Serena

Use for:

- codebase navigation
- symbol lookup
- reference tracing
- precise, narrow code edits

Prefer Serena before broad file reads when the language and repo are supported.

### Context7

Use for:

- framework or library behavior
- current API usage questions
- version-sensitive guidance

If the question depends on library behavior, resolve the library first and use current docs before coding.

### Playwright

Use for:

- rendered-page verification
- browser-only regressions
- DOM-level checks
- client-side failures that raw HTTP will miss

Prefer browser-based validation when client rendering matters.

### Other MCPs

Examples such as Jira, database, or internal systems MCPs should be documented only when they are genuinely part of the workflow.

## Best Practices

- give each MCP a clear job
- avoid overlapping tools unless there is a reason to corroborate
- keep auth outside committed files
- document skill dependencies explicitly when a skill assumes an MCP exists
- prefer read-only actions first for live systems

## Common Failure Modes

- MCP installed but Codex not restarted
- missing local runtime such as `npx` or `uvx`
- invalid token, env var, or auth header
- a skill assumes an MCP that has not been configured
- a hosted MCP is reachable but does not expose the resources you expected

## Documentation Rule

For every MCP you standardize, document:

- name
- purpose
- install pattern
- auth method
- validation step
- which tasks should trigger it
