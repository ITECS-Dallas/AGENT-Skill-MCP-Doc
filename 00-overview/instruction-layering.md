# Instruction Layering

This installation exposed a useful pattern: keep instructions in layers, and keep each layer focused.

## Recommended layers

### 1. Base model behavior

Observed from the installed model catalog:

- concise, pragmatic communication
- preference for fast search tools such as `rg`
- preference for parallel tool calls when independent
- conservative editing behavior around dirty git trees
- avoidance of destructive git commands

Use this layer for stable, general operating conventions that should apply everywhere.

### 2. User or profile-level Codex config

Observed via `~/.codex/config.toml`:

- default profile
- default model
- reasoning effort
- sandbox/approval behavior
- trusted projects
- MCP registrations
- optional `model_instructions_file`

Use this layer for operator preferences and machine-level defaults.

### 3. Project bootstrap overview

Observed as a separate overview document referenced by the Codex profile.

Use this layer for high-level project topology:

- stack summary
- runtime topology
- key directories
- deployment model
- test expectations
- logs and risks

Do not overload it with low-level coding style or secrets.

### 4. Project `AGENTS.md`

Observed at repo root.

Use this layer for:

- repo structure
- build/test commands
- coding conventions
- project tooling requirements
- commit/review expectations
- environment caveats that truly matter to day-to-day work

### 5. Skills

Observed globally and repo-locally.

Use skills for repeatable task families:

- docs lookup
- skill installation
- site audits
- runtime operations
- domain-specific workflows

Skills should be narrower than `AGENTS.md` and should trigger only when relevant.

### 6. Tool-specific config

Observed via Serena config and MCP registrations.

Use this layer for:

- tool activation defaults
- language backends
- project trust/read-only settings
- MCP endpoints and env bindings

## Practical split

| Put it in | If it answers |
|---|---|
| Base behavior | "How should the agent generally behave?" |
| Codex config | "What should this installation default to?" |
| Bootstrap overview | "How is this project/system arranged?" |
| `AGENTS.md` | "How should work be done in this repo?" |
| Skill | "How should this recurring task family be handled?" |
| Tool config | "How does this integration get wired?" |

## Anti-patterns

- Putting secrets in any instruction layer
- Putting volatile production facts in global config
- Turning `AGENTS.md` into a full runbook for every subsystem
- Writing skills that duplicate large reference docs inline
- Using a repo-local bootstrap overview as if it were a global policy file
