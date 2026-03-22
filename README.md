# Codex CLI Bootstrap Docs

This repository is a portable documentation and template set for bootstrapping a new Codex CLI installation.

Use it to decide:

- what belongs in Codex config versus repo `AGENTS.md`
- when a project should add a bootstrap overview
- how to write useful skills without restating general Codex behavior
- which MCPs are worth standardizing and how to document them
- how to keep all of that portable, reviewable, and safe to publish

It is intentionally a docs-and-templates repo, not a runtime service.

## What This Repo Is Not

This repo is not:

- a direct mirror of one machine's `~/.codex`
- a frozen snapshot of model catalogs or internal CLI state
- a replacement for Codex's built-in behavior or official product docs
- a server that Codex automatically consumes on its own

Codex already supports config profiles, repo `AGENTS.md`, skills, and MCP registrations. This repo exists to give you a clean source of truth for the parts you still have to define yourself.

## Repository Map

| Path | What it contains |
|---|---|
| `00-overview/` | Core instruction-layering guidance |
| `10-agents/` | Guidance for writing repo-local `AGENTS.md` files |
| `20-skills/` | Skill authoring guidance |
| `30-mcp/` | MCP setup and usage guidance |
| `40-instructions/` | Bootstrap overview and Serena integration patterns |
| `50-workflows/` | Durable safety and portability rules |
| `60-templates/` | Reusable templates for config, `AGENTS.md`, and `SKILL.md` |
| `99-inventory/` | Provenance and maintenance inventory |

Top-level files:

- `README.md` - public landing page and repo orientation
- `AGENTS.md` - contributor guidance for this repo
- `LICENSE` - repository license
- `.env.example` - safe local placeholder file for optional secrets

## Recommended Reading Order

### For a new Codex CLI installation
1. `00-overview/instruction-layering.md`
2. `60-templates/config-and-bootstrap.templates.md`
3. `30-mcp/required-local-mcp-setup.md`
4. `10-agents/README.md`
5. `99-inventory/source-inventory.md`

### For writing a repo `AGENTS.md`
1. `10-agents/README.md`
2. `10-agents/global-vs-project.md`
3. `60-templates/AGENTS.template.md`
4. `40-instructions/project-bootstrap-overview-pattern.md`

### For writing a skill
1. `20-skills/skill-authoring-guide.md`
2. `60-templates/SKILL.template.md`

### For MCP standardization
1. `30-mcp/required-local-mcp-setup.md`
2. `30-mcp/usage-and-onboarding.md`
3. `60-templates/config-and-bootstrap.templates.md`

### For full-server bootstrap with Codex CLI
1. `60-templates/server-bootstrap.prompt.md`
2. `60-templates/config-and-bootstrap.templates.md`
3. `30-mcp/required-local-mcp-setup.md`
4. `10-agents/README.md`

## Core Principles

1. Keep only durable guidance here.
2. Put repo-specific rules in the repo, not in global bootstrap docs.
3. Use placeholders instead of live paths, tokens, or hostnames.
4. Require only the tools a repo actually depends on.
5. Prefer templates and examples over copied environment state.

## Recommended Baseline MCPs

For most software-oriented Codex CLI environments, start by evaluating:

- `serena` for semantic code navigation and precise edits
- `context7` for current library and framework documentation
- `playwright` for rendered-page and browser validation

These are strong defaults, not universal requirements. A markdown-only repo does not need Playwright, and a trivial script repo may not need Serena.

## Quick Start

1. Start from `60-templates/config-and-bootstrap.templates.md`.
2. Install only the MCPs your workflows actually need.
3. Create or update repo-local `AGENTS.md` using `60-templates/AGENTS.template.md`.
4. Add a bootstrap overview only when the project is too large for `AGENTS.md` alone.
5. Use `60-templates/server-bootstrap.prompt.md` when you want Codex CLI to perform a full new-server bootstrap.
6. Use `99-inventory/source-inventory.md` to keep future changes grounded and portable.

## Maintenance Rules

If this repo is used as the canonical bootstrap reference:

1. Do not commit secrets.
2. Do not reintroduce machine snapshots as source-of-truth docs.
3. Verify Codex CLI command syntax before documenting commands.
4. Verify vendor-specific guidance against current official docs before updating it.
5. Update templates and inventory together when scope changes.

## Publishing Safety

Never commit:

- secrets
- API keys
- tokens
- auth files
- logs
- cached sessions
- machine-specific runtime state
- copied internal docs that still contain sensitive details

Use `.env` for local secrets, `.env.example` for placeholders, and templates for anything environment-specific.

## License

This repository is licensed under the MIT License. See `LICENSE`.
