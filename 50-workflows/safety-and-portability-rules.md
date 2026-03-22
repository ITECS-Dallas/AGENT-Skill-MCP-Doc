# Safety and Portability Rules

These rules are meant to stay stable even when the surrounding toolchain evolves.

## Safety rules

1. Do not expose secrets in config, skills, docs, or examples.
2. Avoid destructive git commands unless explicitly requested.
3. Do not revert unrelated user changes.
4. Prefer read-only inspection before restart, activation, or rollback.
5. Use the narrowest tool that answers the question.
6. Validate after meaningful changes.

## Portability rules

1. Replace machine paths with placeholders.
2. Replace hostnames and repo names with placeholders unless needed as examples.
3. Convert environment-specific runbooks into templates or blueprints.
4. Treat logs and cached state as evidence, not reusable documentation.
5. Separate secrets from reusable config examples.

## Documentation rules

1. Keep global guidance separate from repo-local guidance.
2. Put recurring task families into skills, not into `AGENTS.md`.
3. Put high-level topology into a bootstrap overview, not into a skill.
4. Document MCP dependencies explicitly when a skill relies on them.
5. Mark optional dependencies as optional.

## Operational rules worth carrying forward

- prefer `rg`-style search for text/file discovery
- use parallel tool calls for independent reads
- keep git commands non-interactive where possible
- use browser automation when rendered state matters
- consult live docs before framework-dependent changes

## Release / ship rule to generalize

Before committing or shipping from a shared working tree, inspect the whole tree rather than assuming only your touched files matter.
