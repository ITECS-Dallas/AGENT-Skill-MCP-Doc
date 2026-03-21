# Portable AGENTS.md Guidance

## What this section is for

The audited installation had only one discoverable `AGENTS.md`, and it was repo-specific. Its value was structural, not portable verbatim.

This section extracts that structure into reusable guidance.

## Recommended `AGENTS.md` responsibilities

Use `AGENTS.md` for repo-local operating guidance such as:

- project layout
- key build/test/dev commands
- coding style conventions
- required tool usage
- testing expectations
- commit/review expectations
- environment and deployment caveats

## Keep these out of `AGENTS.md`

- secrets
- large architecture narratives better suited for a bootstrap overview
- full API docs
- long historical context
- duplicated skill instructions

## Good section pattern

1. Repository purpose and structure
2. Build, test, and dev commands
3. Coding style and naming conventions
4. Tooling requirements
5. Testing guidance
6. Commit / PR expectations
7. Environment caveats
8. Skills available in this repo

## Global vs project-local split

### Belongs in global guidance

- “Prefer concise updates.”
- “Do not expose secrets.”
- “Avoid destructive git commands.”
- “Use docs lookups for framework-dependent changes.”

### Belongs in project `AGENTS.md`

- actual commands
- actual test files
- actual deployment scripts
- actual host/runtime caveats
- actual skill list for that repo

## Derived reusable patterns

From the audited repo guidance, these patterns are worth reusing:

- explicitly require important tools, if any
- explicitly require the baseline MCP trio when the repo depends on them: Playwright, Serena, and Context7
- name the canonical build/test commands
- tell the agent which directories are sensitive or externally owned
- state deployment and release guardrails in one place
- document where secrets belong and where they must not go
- name the repo-local skills that should be preferred for specific task families

## Recommended tooling rule for modern software repos

If the repository depends on browser checks, semantic code navigation, and docs-backed framework changes, add an explicit rule that:

- Playwright must be installed and used for rendered/browser validation
- Serena must be installed and activated before code work
- Context7 must be installed and used before framework/library-dependent changes

Use `../60-templates/AGENTS.template.md` to start a new file.
