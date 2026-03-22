# Portable `AGENTS.md` Guidance

## What `AGENTS.md` Should Do

Use repo-local `AGENTS.md` for operating rules that genuinely vary by repository:

- project layout
- canonical build, test, and dev commands
- coding style conventions
- repo-specific tool requirements
- testing expectations
- commit and review expectations
- deployment or environment caveats

`AGENTS.md` is the repo contract. Keep it direct and operational.

## What `AGENTS.md` Should Not Do

Keep these out of it:

- secrets
- large topology writeups better suited for a bootstrap overview
- copied vendor documentation
- long historical background
- full skill bodies
- generic Codex behavior that already applies everywhere

## Good Section Pattern

1. Repository purpose and structure
2. Build, test, and development commands
3. Coding style and naming conventions
4. Assistant tooling requirements
5. Testing guidance
6. Commit and review expectations
7. Environment and configuration notes
8. Repo-local skills, if any

## Tooling Rules

Only require the tools the repo actually depends on.

Examples:

- require Serena if symbol-aware navigation or edits are expected
- require Context7 if framework or library changes must be docs-backed
- require Playwright if rendered browser validation is part of the workflow

Do not force a blanket "install everything" rule on repos that do not need those tools.

## Reusable Patterns Worth Keeping

- name the canonical commands explicitly
- call out sensitive or externally managed directories
- state where secrets belong and where they must not go
- document release or deployment guardrails in one place
- name repo-local skills that should be preferred for recurring task families

Use `../60-templates/AGENTS.template.md` to start a new file.
