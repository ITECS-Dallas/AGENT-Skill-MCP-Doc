# Serena Integration Guide

Serena is a semantic coding layer. It is useful when you want symbol-aware navigation and precise edits, but it is not required for every repository.

## What Serena Is Good At

Use Serena for:

- project activation
- onboarding state checks
- symbol search
- reference tracing
- symbol-aware edits
- language-server-backed code understanding

It adds the most value in medium or large codebases.

## Important Serena Config Surfaces

### Global config

Useful global settings usually include:

- default modes
- tool timeout
- globally ignored paths
- registered projects

### Project config

Useful project-level settings usually include:

- project name
- primary language
- read-only mode
- ignored paths
- tool overrides

## Operational Guidance

### Activate before use

If a repo expects Serena, activate the project first.

### Check onboarding state

If onboarding has not been performed, either complete it or avoid assuming Serena memories exist.

### Prefer symbolic navigation first

Good first actions:

- project activation
- symbols overview
- symbol lookup
- references lookup
- targeted pattern search

Use broad file reads only when needed.

### Use Serena where it adds value

Serena is strongest for:

- understanding code structure
- finding references precisely
- editing functions, classes, and symbols safely

It is less useful for:

- large non-code documents
- external websites
- generic shell operations outside the project

## Documentation Recommendations

If Serena is required for a repo, say so in `AGENTS.md`.

Document:

- when activation is required
- whether onboarding is expected
- whether another docs source must be consulted before framework-dependent changes
