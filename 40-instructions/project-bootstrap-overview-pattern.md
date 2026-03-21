# Project Bootstrap Overview Pattern

Source basis: a repo-local bootstrap overview document referenced from Codex profile config. The original document was heavily project-specific, so this file captures only the reusable structure.

## When to create one

Create a bootstrap overview when a project has enough moving parts that a short `AGENTS.md` is not enough.

Typical triggers:

- multiple runtimes or services
- CMS + app combinations
- release and rollback workflows
- infra and app coupling
- recurring operational risks

## Recommended outline

1. High-level stack and purpose
2. Runtime and hosting topology
3. Source tree and key entry points
4. Data contracts and integrations
5. Deployment and maintenance workflows
6. Testing and QA expectations
7. Logs, backups, and diagnostics
8. Risks and outstanding issues

## What belongs here

- service map
- release model
- ownership boundaries
- canonical scripts
- operational risks
- test expectations

## What does not belong here

- secrets
- low-level coding style rules
- every single command variant
- long policy prose better suited for skills or references

## Good properties

- easy to skim
- stable enough to age well
- specific enough to orient a new operator
- separate from secret material

Use `../60-templates/config-and-bootstrap.templates.md` for a reusable skeleton.
