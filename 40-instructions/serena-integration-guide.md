# Serena Integration Guide

Source basis: sanitized from `~/.serena/serena_config.yml`, project-level Serena config, and the Serena instructions surfaced during activation.

## What Serena is doing in this setup

Serena was used as a semantic coding layer on top of the repo:

- project activation
- onboarding state checks
- symbol search
- symbol-aware edits
- project memories
- language-server-backed code understanding

## Important Serena config surfaces

### Global config

Observed in `~/.serena/serena_config.yml`:

- language backend
- default modes
- tool timeout
- token-count estimator
- globally ignored paths
- registered projects
- project Serena folder location

### Project config

Observed in project-specific Serena config:

- project name
- language
- read-only mode
- tool enable/disable overrides
- ignored paths
- base/default modes
- language list

## Operational guidance

### Activate before using

If Serena is expected for a repo, activate the project first.

### Check onboarding state

If onboarding has not been performed, complete it or explicitly decide not to depend on Serena memories.

### Prefer symbolic navigation first

Good first tools:

- project activation
- symbols overview
- symbol lookup
- references lookup
- targeted pattern search

Use full file reads only when necessary.

### Use Serena for precision, not everything

Serena is best for:

- understanding code structure
- editing functions/classes/symbols precisely
- finding references

It is less relevant for:

- large non-code documents
- external websites
- generic shell operations outside the project

## Good default mode pattern

The audited Serena config defaulted to interactive + editing modes. That is a sensible default for active repo work.

Recommended default:

- `interactive` when collaboration is expected
- `editing` when code changes are allowed

Consider `read_only: true` for especially sensitive repos.

## Documentation recommendations

If Serena is a required tool for a repo, say so explicitly in `AGENTS.md`.

Also document:

- when activation is required
- whether onboarding is expected
- whether Context7 or another docs MCP must be consulted before framework-dependent changes
