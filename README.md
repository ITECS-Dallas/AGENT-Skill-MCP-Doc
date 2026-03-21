# Codex CLI Master Documentation Bundle

This directory is a sanitized, portable documentation bundle derived from a live Codex CLI installation on Linux.

It is meant to help bootstrap future Codex CLI installations and unrelated projects without carrying over client-specific, repo-specific, host-specific, or secret-bearing material.

## Who this repo is for

- operators bootstrapping a new Codex CLI installation
- teams creating reusable `AGENTS.md`, skill, and MCP standards
- maintainers who want a portable reference instead of a client-bound internal runbook

## What problem this solves

Real Codex CLI installations accumulate useful operating knowledge in several places:

- user-level Codex config
- repo `AGENTS.md` files
- skills
- MCP setup
- tool-specific config such as Serena
- ad hoc bootstrap notes

That knowledge is valuable, but it is often too tied to one machine, one company, one repo, or one deployment environment to reuse directly.

This repository distills that operational knowledge into a portable documentation set.

## What this bundle contains

- Generic Codex CLI operating guidance
- AGENTS.md patterns and templates
- Reusable skill design guidance and skill blueprints
- MCP configuration and usage guidance
- required local MCP setup guidance
- Serena integration guidance
- Model-selection and reasoning-level guidance
- Safe-operating and portability rules
- Reusable templates for config, bootstrap notes, and instruction files
- An audit inventory describing what was discovered and how it was handled

## Quick start

1. Read `30-mcp/required-local-mcp-setup.md`.
2. Install and verify the baseline MCPs:
   - Playwright
   - Serena
   - Context7
3. Read `60-templates/config-and-bootstrap.templates.md`.
4. Create your local Codex config from the provided patterns.
5. Create your repo `AGENTS.md` from `60-templates/AGENTS.template.md`.
6. Create or adapt skills from `60-templates/SKILL.template.md`.
7. Review `40-instructions/serena-integration-guide.md` if Serena will be required in your repo.
8. Review `99-inventory/source-inventory.md` so you know what was derived, rewritten, or excluded.

## Required baseline MCPs

For most software-oriented Codex CLI installations, this bundle assumes these MCPs should exist locally:

- **Playwright** for rendered-page and browser automation checks
- **Serena** for semantic code navigation, activation, and symbol-aware editing
- **Context7** for documentation-backed framework and library work

This expectation is documented in:

- `30-mcp/required-local-mcp-setup.md`
- `10-agents/README.md`
- `60-templates/AGENTS.template.md`

The recommended project rule is:

- Playwright, Serena, and Context7 must be installed
- Serena must be activated before code work begins
- Context7 must be used before framework/library-dependent changes
- Playwright must be used for rendered/browser/runtime validation when raw HTTP checks are not enough

## How it was derived

This bundle was synthesized from discoverable artifacts in the audited installation, including:

- `~/.codex/config.toml`
- `~/.codex/version.json`
- `~/.codex/models_cache.json`
- installed Codex skills under `~/.codex/skills/`
- Serena configuration under `~/.serena/`
- one repo-local `AGENTS.md`
- repo-local skill folders and a repo bootstrap overview document, used only as pattern sources where they exposed generally useful structure

The result is intentionally rewritten rather than copied wholesale.

## What was intentionally excluded

- Secrets, tokens, auth files, and credential-bearing config
- Cached conversation/session state
- Logs, SQLite state files, shell snapshots, and historical artifacts
- Client/company/repo/server-specific operational details
- Absolute machine paths, except where converted into placeholders
- Live service names, proprietary identifiers, and internal URLs

## How to reuse this bundle

1. Start with `60-templates/`.
2. Customize placeholders such as:
   - `<PROJECT_ROOT>`
   - `<REPO_NAME>`
   - `<MCP_SERVER_NAME>`
   - `<CONFIG_PATH>`
   - `<SITE_URL>`
3. Configure Codex profiles and MCP servers using `60-templates/config-and-bootstrap.templates.md`.
4. Install and verify the required baseline MCPs using `30-mcp/required-local-mcp-setup.md`.
5. Create a project-local `AGENTS.md` from `60-templates/AGENTS.template.md`.
6. Create or adapt skills using `60-templates/SKILL.template.md` and `20-skills/skill-authoring-guide.md`.
7. If using Serena, adapt `40-instructions/serena-integration-guide.md`.
8. Review `99-inventory/source-inventory.md` before assuming any behavior is universal.

## Suggested setup flow for a fresh Codex CLI install

### 1. Install local prerequisites

At minimum, verify:

- Git
- Node.js / `npx`
- Python tooling / `uvx`
- network access for any hosted MCP endpoints

### 2. Configure baseline MCPs

Use:

- `30-mcp/required-local-mcp-setup.md`
- `60-templates/config-and-bootstrap.templates.md`

### 3. Create a sane user-level Codex config

Document:

- default profile
- model choice
- reasoning effort
- trusted project paths
- MCP server registrations
- optional project bootstrap overview file

### 4. Add project instructions

Create:

- `AGENTS.md`
- optionally a project bootstrap overview
- any repo-local skills

### 5. Validate the installation

Confirm:

- Codex starts with the expected profile
- Playwright, Serena, and Context7 are enabled
- Serena can activate the project
- docs lookup works
- browser checks work
- required skills are discoverable

## What still requires manual review

- Actual MCP package names, URLs, commands, and credentials
- Trusted project paths
- Which model and reasoning effort should be the default in your environment
- Repo-specific build, test, deploy, and rollback workflows
- Whether Serena should be mandatory for a given project
- Whether any skill should be installed globally or only repo-locally
- Whether optional MCP dependencies referenced by skills are actually installed

## Folder guide

- `00-overview/` - scope, method, and instruction-layering guidance
- `10-agents/` - portable AGENTS.md guidance
- `20-skills/` - reusable skill guidance and blueprints
- `30-mcp/` - MCP configuration and usage guidance
- `30-mcp/required-local-mcp-setup.md` - baseline MCP setup and verification for a fresh Codex CLI install
- `40-instructions/` - Serena and bootstrap instruction patterns
- `50-workflows/` - operator playbooks, safety, and model usage
- `60-templates/` - reusable templates
- `70-reference/` - reference notes about installation layout and model catalog
- `99-inventory/` - audited source inventory and handling decisions

## Recommended reading order

If you are brand new to this repo:

1. `README.md`
2. `30-mcp/required-local-mcp-setup.md`
3. `60-templates/config-and-bootstrap.templates.md`
4. `60-templates/AGENTS.template.md`
5. `20-skills/skill-authoring-guide.md`
6. `40-instructions/serena-integration-guide.md`
7. `99-inventory/source-inventory.md`

## Repo function summary

This repo functions as:

- a **portable Codex CLI bootstrap kit**
- a **sanitized documentation archive**
- a **template source** for AGENTS, skills, and MCP setup
- a **reference pack** for operating conventions, model usage, and tool integration
- an **audit artifact** showing what kinds of source material were found and how they were transformed

## Maintenance guidance

When updating this repo:

- preserve sanitization
- avoid adding secrets or local tokens
- prefer templates over environment-specific instructions
- update the inventory when adding new source-derived material
- keep AGENTS / MCP / skill guidance aligned when expectations change

## Notes

- This bundle reflects what was discoverable on the audited installation as of 2026-03-21.
- Some behaviors come from installed skills and config rather than from Codex itself; treat those as patterns, not guarantees.
- Where a source was useful but too specific, this bundle provides a template or blueprint instead of a copy.
