# AGENT / Skill / MCP Documentation Source of Truth

A public, GitHub-friendly source-of-truth repository for **AI agent CLI operating standards**.

This repository documents how to structure and govern an agent-centric working environment, especially around:

- layered instructions
- `AGENTS.md` standards
- reusable skills
- MCP setup and usage
- Serena integration
- operator workflows
- reusable templates
- provenance and portability rules

It is intentionally a **documentation-first repo** rather than an application or framework project.

---

## Why this repo exists

Operational knowledge for AI agent CLI setups usually ends up scattered across:

- local config
- repo-level instructions
- MCP registrations
- skills
- tool-specific notes
- onboarding docs
- team habits that never become formal documentation

That makes reuse difficult.

This repo exists to turn that scattered knowledge into a **portable, sanitized, versioned reference set** that can serve as a long-term source of truth in GitHub.

---

## What this repo is

This repo is a maintained documentation bundle for teams who want consistent standards for:

- how instructions are layered
- what belongs in global config vs project files
- how to author and organize skills
- which MCPs should be treated as baseline tooling
- how Serena fits into code-navigation workflows
- how to package templates for reuse
- how to keep guidance portable and safe to publish

---

## Who should use it

This repository is intended for:

- teams bootstrapping a new AI agent CLI environment
- maintainers writing or standardizing `AGENTS.md`
- operators defining MCP expectations and onboarding rules
- skill authors creating reusable task-family guidance
- documentation owners building an internal or public source-of-truth repo

---

## Repository map

| Path | What it contains |
|---|---|
| `00-overview/` | Scope, audit method, and instruction-layering guidance |
| `10-agents/` | Reusable guidance for project `AGENTS.md` files |
| `20-skills/` | Skill design guidance, catalogs, and blueprints |
| `30-mcp/` | MCP discovery, setup, and onboarding guidance |
| `40-instructions/` | Bootstrap overview and Serena integration patterns |
| `50-workflows/` | Operator playbooks, safety rules, and model usage guidance |
| `60-templates/` | Reusable starter templates for `AGENTS.md`, `SKILL.md`, and config |
| `70-reference/` | Supporting reference notes about installation layout and model catalogs |
| `99-inventory/` | Source provenance, handling decisions, and limitations |

Top-level files:
- `README.md` - public landing page and repo orientation
- `AGENTS.md` - repo-local guidance for contributors and coding agents
- `LICENSE` - repository license
- `.env.example` - safe local config example

---

## What is inside

### 1. Instruction architecture
Guidance for separating:
- base behavior
- user/profile config
- bootstrap overviews
- project `AGENTS.md`
- skills
- tool-specific configuration

### 2. `AGENTS.md` standards
Guidance for writing repo-local rules that are:
- concise
- operationally useful
- specific to the repo
- not overloaded with secrets or large architecture narratives

### 3. Skills
Guidance for designing skills that:
- trigger cleanly
- stay concise
- use progressive disclosure
- keep references/scripts/assets separate from top-level instructions

### 4. MCP guidance
Standards for:
- documenting MCP purpose
- installing required MCPs
- describing trigger conditions
- handling auth safely
- keeping tool expectations explicit

### 5. Serena guidance
Guidance for treating Serena as a first-class semantic navigation layer rather than an afterthought.

### 6. Workflows and safety rules
Playbooks for discovery, docs-backed implementation, audits, runtime operations, and new-environment bootstrap.

### 7. Templates and provenance
Reusable templates plus a clear inventory of where the bundled guidance came from and how it was transformed.

---

## Recommended baseline MCP set

For most software-oriented AI agent CLI environments, this repo recommends a baseline trio:

- **Playwright** - rendered-page and browser automation validation
- **Serena** - semantic code navigation and precise edits
- **Context7** - current official library/framework documentation lookup

See:
- `30-mcp/required-local-mcp-setup.md`
- `30-mcp/usage-and-onboarding.md`
- `60-templates/config-and-bootstrap.templates.md`
- `10-agents/README.md`

---

## Suggested reading order

### If you are new here
1. `README.md`
2. `00-overview/method-and-scope.md`
3. `00-overview/instruction-layering.md`
4. `30-mcp/required-local-mcp-setup.md`
5. `60-templates/config-and-bootstrap.templates.md`
6. `99-inventory/source-inventory.md`

### If you want to write or improve an `AGENTS.md`
1. `10-agents/README.md`
2. `10-agents/global-vs-project.md`
3. `60-templates/AGENTS.template.md`
4. `40-instructions/project-bootstrap-overview-pattern.md`

### If you want to build or standardize skills
1. `20-skills/README.md`
2. `20-skills/skill-authoring-guide.md`
3. `20-skills/skill-blueprints.md`
4. `60-templates/SKILL.template.md`

### If you want to standardize MCP setup
1. `30-mcp/configured-mcps.md`
2. `30-mcp/required-local-mcp-setup.md`
3. `30-mcp/usage-and-onboarding.md`
4. `60-templates/config-and-bootstrap.templates.md`

---

## Quick start

1. Read `00-overview/instruction-layering.md` to understand the intended document hierarchy.
2. Use `30-mcp/required-local-mcp-setup.md` to establish baseline MCP tooling.
3. Start from `60-templates/config-and-bootstrap.templates.md` when creating or standardizing a local setup.
4. Use `60-templates/AGENTS.template.md` and `60-templates/SKILL.template.md` to create project-local guidance.
5. Review `99-inventory/source-inventory.md` before assuming every pattern should be copied literally.

---

## Public source-of-truth maintenance rules

If this repository is used as the canonical GitHub source of truth, keep these rules in force:

1. **Do not commit secrets**  
   Keep credentials only in ignored local files.

2. **Prefer templates and patterns over raw environment copies**  
   Rewrite or generalize machine-specific material before committing it.

3. **Keep provenance clear**  
   Update `99-inventory/source-inventory.md` when new source-derived docs are added.

4. **Keep related guidance aligned**  
   If MCP expectations or skill conventions change, update the corresponding templates and overview docs too.

5. **Preserve portability**  
   Replace hostnames, tokens, customer details, and machine paths with placeholders unless there is a compelling reason not to.

6. **Keep the landing page current**  
   The README should always accurately describe the repo’s purpose, structure, and maintenance expectations.

---

## What should never be committed here

This repo should stay safe to publish.

Never commit:
- secrets
- API keys
- tokens
- auth files
- logs
- cached sessions
- machine-specific runtime state
- unreviewed raw copies of sensitive internal documentation

Use:
- `.env` for local secrets only
- `.env.example` for safe placeholders
- templates and placeholders for anything environment-specific

---

## Contributing guidance

When contributing:
- keep markdown concise and skimmable
- prefer reusable patterns over narrow one-off instructions
- update README and inventory docs when repository scope changes
- keep numbered folders and taxonomy coherent
- maintain consistency between overview docs, templates, and reference docs

For repo-local operating guidance, see `AGENTS.md`.

---

## License

This repository is licensed under the MIT License. See `LICENSE`.

---

## Provenance and limitations

This documentation bundle was derived from a real audited environment and rewritten into a portable form.

That means:
- some guidance is summarized from observed config and tool usage
- some material is generalized from a single environment
- some model/tool references are snapshots, not permanent truths
- not every behavior described here should be treated as a public product guarantee

For provenance and handling decisions, see:
- `00-overview/method-and-scope.md`
- `99-inventory/source-inventory.md`

---

## One-line summary

This repository is a portable, GitHub-hosted **source of truth for AI agent CLI documentation standards** covering **instructions, `AGENTS.md`, skills, MCPs, Serena usage, workflows, templates, and provenance**.
