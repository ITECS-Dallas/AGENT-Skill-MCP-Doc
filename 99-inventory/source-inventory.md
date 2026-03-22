# Source Inventory

This repo is no longer meant to preserve one audited environment. It keeps only the durable guidance that is useful for bootstrapping Codex CLI installations and repo-local instructions.

## Current Evidence Basis

| Source | Used for | Handling rule |
|---|---|---|
| `codex --help`, `codex mcp --help`, `codex mcp add --help`, `codex mcp get --help`, `codex mcp list` | current CLI command surface and install examples | summarize, do not treat as a permanent product spec |
| local `~/.codex/config.toml` patterns | starter config templates | rewrite into placeholders; never copy live values |
| installed system skills such as `skill-creator` and `skill-installer` | skill-authoring guidance | distill patterns, not verbatim copies |
| local Serena config patterns | Serena integration guidance | summarize only the reusable setup ideas |
| official OpenAI docs and guidance | claims about Codex instruction layering and product behavior | prefer official docs over local inference when updating vendor-specific guidance |

## Canonical Doc Set Kept

| Path | Why it stays |
|---|---|
| `00-overview/instruction-layering.md` | durable split between config, global guidance, repo guidance, skills, and tool config |
| `10-agents/*` | practical guidance for repo `AGENTS.md` files |
| `20-skills/skill-authoring-guide.md` | durable skill-authoring guidance |
| `30-mcp/*` | MCP setup and usage guidance that new installs still need |
| `40-instructions/*` | bootstrap overview and Serena integration patterns |
| `50-workflows/safety-and-portability-rules.md` | stable safety rules that are not tied to one tool version |
| `60-templates/*` | the highest-value reusable outputs in the repo |
| `99-inventory/source-inventory.md` | maintenance and provenance control point |

## Removed from Canonical Scope

These topics were intentionally trimmed because they were too snapshot-heavy, redundant, or installation-specific:

- audited-environment method notes
- discovered model catalogs
- local filesystem layout summaries
- environment-specific MCP inventories
- generic operator playbooks that mainly restated built-in Codex behavior
- skill catalog summaries that did not add much beyond the template and guide

## Maintenance Rules

1. If you add Codex CLI commands, verify them against the current CLI help first.
2. If you add vendor-specific guidance, verify it against current official docs first.
3. If you derive examples from a real machine, rewrite them into placeholders before committing.
4. If you change canonical scope, update `README.md`, `AGENTS.md`, templates, and this inventory together.
