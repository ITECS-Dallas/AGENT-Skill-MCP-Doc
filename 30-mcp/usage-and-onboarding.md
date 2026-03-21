# MCP Usage and Onboarding

## Onboarding checklist for a fresh installation

1. Install the baseline MCP trio: Playwright, Serena, and Context7.
2. Decide which additional MCPs are globally useful versus project-specific.
3. Install or make available the local runtimes they need (`npx`, `uvx`, browser dependencies, etc.).
4. Add MCP entries to Codex config with placeholders, not hard-coded secrets.
5. Restart Codex after adding or changing MCPs.
6. Validate each MCP with one safe smoke query.
7. Document each MCP’s purpose and trigger conditions in project instructions or skills.

## When to use which MCP

### Serena

Use for:

- codebase navigation
- symbol lookup
- reference tracing
- narrow code edits

Prefer Serena before broad file reads when working inside a supported codebase.
For repos that depend on Serena, require activation in `AGENTS.md`.

### Context7

Use for:

- framework/library behavior
- API usage questions
- version-sensitive code guidance

If the query depends on library behavior, resolve the library first and query official docs before coding.
For repos that depend on framework-heavy work, make this an explicit `AGENTS.md` rule.

### Playwright

Use for:

- rendered-page verification
- client-side schema checks
- DOM-level smoke tests
- browser-only regressions

Prefer browser-based validation over raw HTTP when client rendering matters.
For UI-heavy repos, make this an explicit `AGENTS.md` rule for rendered verification.

### Jira

Use for:

- issue lookup
- project metadata
- workflow state
- comments/worklogs/transitions

Prefer narrow queries and filtered fields to reduce noise and token cost.

## Best practices

- Give each MCP a single clear job.
- Avoid overlapping doc sources unless you need corroboration.
- Keep auth outside committed files.
- Record dependency expectations in skills when a skill assumes an MCP exists.
- Use read-only queries first when touching live systems.

## Common failure modes

- MCP installed but not restarted
- missing local runtime (`npx`, `uvx`, browser package)
- invalid token/header/env
- skill assumes an MCP that has not been configured
- remote MCP accessible but not returning browseable resources

## Documentation rule

For every MCP you enable, document:

- name
- purpose
- transport style
- auth method
- validation step
- which tasks should trigger it
