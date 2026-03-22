# Project Bootstrap Overview Pattern

A bootstrap overview is optional. Use it when `AGENTS.md` is no longer enough to orient a new operator or coding agent.

## When to Create One

Create a bootstrap overview when a project has:

- multiple runtimes or services
- infrastructure and app coupling
- non-trivial deployment or rollback workflows
- recurring operational risks
- enough topology that a concise `AGENTS.md` would become bloated

You can reference this file from `model_instructions_file` or point to it from repo-local docs.

## Recommended Outline

1. High-level stack and purpose
2. Runtime and hosting topology
3. Source tree and key entry points
4. Data contracts and integrations
5. Deployment and maintenance workflows
6. Testing and QA expectations
7. Logs, backups, and diagnostics
8. Risks and outstanding issues

## What Belongs Here

- service map
- release model
- ownership boundaries
- canonical scripts
- operational risks
- high-level test expectations

## What Does Not Belong Here

- secrets
- low-level coding style rules
- every command variant
- long policy prose better suited for skills or `AGENTS.md`

## Good Properties

- easy to skim
- stable enough to age well
- specific enough to orient a new contributor
- separate from secret material

Use `../60-templates/config-and-bootstrap.templates.md` for a reusable skeleton.
