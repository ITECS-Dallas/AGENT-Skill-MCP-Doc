# Instruction Layering

Codex already has built-in behavior. Your docs should supply the missing local decisions, not restate the whole product.

Use layers, and keep each layer narrow.

## Recommended Layers

### 1. Built-in Codex behavior

This is the model and product behavior you do not maintain here.

Do not copy generic rules like:

- be concise
- avoid destructive git commands
- inspect before editing
- use current docs when the question is version-sensitive

Only document local rules that materially change how work should be done.

### 2. User or profile-level Codex config

Use `~/.codex/config.toml` for machine-level defaults such as:

- default profile
- default model
- reasoning level
- sandbox and approval defaults
- trusted projects
- MCP registrations
- optional `model_instructions_file`

This layer answers: "How should this installation default?"

### 3. Optional global guidance

If you maintain cross-repo guidance, keep it in one place such as:

- a home-level `AGENTS.md`
- a profile `model_instructions_file`
- a shared bootstrap doc

Use it for stable cross-repo rules:

- secret handling
- default docs lookup policy
- default tool expectations
- communication or review preferences

This layer answers: "What should be true across many repos?"

### 4. Project `AGENTS.md`

Use repo-local `AGENTS.md` for rules that actually vary by repo:

- structure and important paths
- build, test, and dev commands
- coding conventions
- repo-specific tool requirements
- release or review guardrails
- environment caveats that affect daily work

This layer answers: "How should work be done in this repo?"

### 5. Project bootstrap overview

Add a separate overview only when the project is too large for `AGENTS.md` alone.

Good content:

- stack summary
- runtime topology
- source tree landmarks
- deployment model
- key diagnostics and risks

This layer answers: "How is this system arranged?"

### 6. Skills

Use skills for repeatable task families, not for general repo policy.

Good candidates:

- docs lookup
- install/bootstrap tasks
- audit workflows
- runtime operations
- domain-specific workflows

This layer answers: "How should this recurring task type be handled?"

### 7. Tool-specific config

Keep integration wiring in the tool layer itself:

- MCP server registrations
- Serena project config
- auth env vars
- tool timeouts and modes

This layer answers: "How is this tool wired?"

## Practical Split

| Put it in | If it answers |
|---|---|
| Codex config | "What should this installation default to?" |
| Global guidance | "What rules should apply across many repos?" |
| Project `AGENTS.md` | "How should work be done in this repo?" |
| Bootstrap overview | "How is this system arranged?" |
| Skill | "How should this recurring task family be handled?" |
| Tool config | "How does this integration get wired?" |

## Anti-Patterns

- putting secrets in any instruction layer
- treating one machine snapshot as canonical truth
- turning `AGENTS.md` into a full architecture manual
- writing skills that duplicate large reference docs inline
- requiring every repo to use every MCP
