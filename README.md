# AGENT / Skill / MCP Documentation Source of Truth

This repository is a **GitHub-ready source-of-truth documentation bundle** for running and standardizing an AI agent CLI environment—especially Codex CLI style setups that rely on:

- layered instructions
- project `AGENTS.md` guidance
- reusable skills
- MCP integrations
- Serena-based code navigation
- bootstrap overview documents
- model/workflow conventions
- reusable templates and patterns

It is intentionally a **documentation-first repo**, not an application codebase.
Its job is to preserve the *portable operating knowledge* needed to stand up, govern, and reuse an AI-agent workflow across projects without carrying over secrets, machine-specific paths, or one-off client details.

---

## What this repository is for

Use this repo as the canonical reference for:

- how AI agent CLI instructions should be layered
- what belongs in global config vs project `AGENTS.md`
- how to design, organize, and validate skills
- which MCPs are required and how they should be used
- how Serena should fit into repo workflows
- how to write bootstrap overviews for complex projects
- how to choose models and reasoning levels pragmatically
- how to keep reusable operator documentation portable and sanitized

In short: this repo is meant to be the **source of truth for agent-operating documentation** covering **agents, skills, MCPs, instructions, workflows, templates, and supporting references**.

---

## Who this repo is for

This repository is useful for:

- operators bootstrapping a fresh AI agent CLI environment
- teams defining standards for `AGENTS.md`, skills, and MCP usage
- maintainers building internal source-of-truth docs for agent workflows
- repo owners who want reusable templates instead of copy-pasting from one project to another
- skill authors who need a clean blueprint for packaging repeatable task families

---

## What problem this solves

Real AI-agent CLI installations accumulate useful knowledge in scattered places:

- user-level config
- repo-local `AGENTS.md` files
- system and repo-local skills
- MCP registrations
- Serena config
- bootstrap notes
- model defaults and reasoning conventions
- operator habits that never make it into official docs

That knowledge is valuable, but it is usually tied to:

- one machine
- one organization
- one repository
- one deployment topology
- one set of credentials or local paths

This repo distills that knowledge into a **portable, sanitized, reusable documentation set** that can be versioned in GitHub and reused across environments.

---

## Core principles behind this repo

This documentation set is designed around a few strong rules:

1. **Portable over literal**  
   Preserve intent and structure, not environment-specific wording.

2. **Sanitized by default**  
   No secrets, tokens, auth state, host-specific paths, or internal-only identifiers should live here.

3. **Layered instructions**  
   Global behavior, Codex config, bootstrap overviews, `AGENTS.md`, skills, and MCP config each have different jobs.

4. **Templates over fragile copies**  
   When structure matters more than values, provide a template.

5. **Blueprints over overfitting**  
   Repo-specific skills or runbooks should become generalized blueprints, not transplanted blindly.

6. **Explicit tool expectations**  
   If a workflow depends on Playwright, Serena, or Context7, say so clearly.

7. **Documentation with provenance**  
   The repo explains where guidance came from and what was intentionally excluded.

---

## Repository layout

| Path | Purpose |
|---|---|
| `00-overview/` | Why this bundle exists, how the audit was done, and how instruction layers should be separated |
| `10-agents/` | Portable guidance for writing repo-level `AGENTS.md` files |
| `20-skills/` | Skill design guidance, reusable skill concepts, and generalized blueprints |
| `30-mcp/` | MCP inventory, setup expectations, and onboarding/usage guidance |
| `40-instructions/` | Guidance for bootstrap overview docs and Serena integration |
| `50-workflows/` | Operator playbooks, safety rules, model usage guidance, and portability rules |
| `60-templates/` | Reusable starter templates for `AGENTS.md`, `SKILL.md`, config, and bootstrap docs |
| `70-reference/` | Supporting reference notes about discovered installation layout and model catalog patterns |
| `99-inventory/` | Provenance, source inventory, and handling decisions for derived materials |

---

## Document index

### `00-overview/`

- `00-overview/method-and-scope.md`  
  Explains the audit method, reuse rules, classification rubric, and non-goals.
- `00-overview/instruction-layering.md`  
  Defines the recommended split between base behavior, config, bootstrap overviews, `AGENTS.md`, skills, and tool config.

### `10-agents/`

- `10-agents/README.md`  
  Explains what a portable `AGENTS.md` should own and what it should leave elsewhere.
- `10-agents/global-vs-project.md`  
  Clarifies the split between cross-project guidance and repo-local operating rules.

### `20-skills/`

- `20-skills/README.md`  
  Summarizes discovered portable skill patterns and how to reuse them safely.
- `20-skills/reusable-skills-catalog.md`  
  Catalog of directly reusable skill ideas and generalized blueprints.
- `20-skills/skill-authoring-guide.md`  
  Practical guidance for building concise, triggerable, maintainable skills.
- `20-skills/skill-blueprints.md`  
  Blueprints for docs lookup, installer, audit, runtime-ops, domain-ops, and content/SEO skills.

### `30-mcp/`

- `30-mcp/configured-mcps.md`  
  Sanitized view of the MCPs discovered and what they mean operationally.
- `30-mcp/required-local-mcp-setup.md`  
  Baseline install and verification guidance for Playwright, Serena, and Context7.
- `30-mcp/usage-and-onboarding.md`  
  Rules for when to use which MCP and how to document MCP expectations.

### `40-instructions/`

- `40-instructions/project-bootstrap-overview-pattern.md`  
  Pattern for writing a high-level project/system bootstrap overview.
- `40-instructions/serena-integration-guide.md`  
  Guidance for using Serena as a first-class code navigation and editing layer.

### `50-workflows/`

- `50-workflows/model-usage-guidance.md`  
  Heuristics for model family selection and reasoning effort.
- `50-workflows/operator-playbooks.md`  
  Step-by-step workflows for discovery, docs-backed changes, skills, audits, runtime ops, and new installs.
- `50-workflows/safety-and-portability-rules.md`  
  Safety, portability, documentation, and release rules worth carrying forward.

### `60-templates/`

- `60-templates/AGENTS.template.md`  
  Starter template for a strong repo-level `AGENTS.md`.
- `60-templates/SKILL.template.md`  
  Starter template for a reusable skill package, including `SKILL.md` and `agents/openai.yaml`.
- `60-templates/config-and-bootstrap.templates.md`  
  Templates for `config.toml`, bootstrap overviews, environment notes, and Serena project config.

### `70-reference/`

- `70-reference/codex-cli-layout.md`  
  Reference map of what tends to exist under `~/.codex/`, `~/.serena/`, and `~/.mcp/`.
- `70-reference/discovered-model-catalog.md`  
  Snapshot-style model catalog summary with stable takeaways.

### `99-inventory/`

- `99-inventory/source-inventory.md`  
  Provenance record showing what source categories were found, how they were handled, and why.

---

## What this repo contains

This bundle covers seven major content areas:

### 1. Instruction architecture
How to separate:

- base model behavior
- user/profile config
- bootstrap overviews
- repo `AGENTS.md`
- skills
- tool-specific config

### 2. `AGENTS.md` guidance
How to write repo-local operating rules that are:

- useful
- bounded
- not overloaded with architecture or secrets
- aligned with project tooling and validation expectations

### 3. Skills
How to:

- identify repeatable task families
- package them as reusable skills
- keep `SKILL.md` concise
- move detail into references/scripts/assets
- document dependencies explicitly

### 4. MCP strategy
How to:

- define the baseline MCP set
- assign each MCP a clear purpose
- avoid hidden auth in committed files
- document trigger conditions and validation steps

### 5. Serena integration
How to:

- activate Serena intentionally
- use symbol-aware navigation first
- avoid unnecessary broad file reads
- treat onboarding and project memory deliberately

### 6. Operator workflows
How to approach:

- discovery
- docs-backed implementation
- audits
- runtime operations
- new environment bootstrap

### 7. Reusable templates
How to start new repos or environments from a stable template instead of rebuilding structure from scratch.

---

## Baseline MCP expectation

For most software-oriented AI agent CLI setups, this repo assumes the following baseline MCP trio should be installed and documented:

- **Playwright** — rendered-page and browser automation checks
- **Serena** — semantic code navigation, activation, and precise edits
- **Context7** — current library/framework documentation lookup

These expectations are documented in:

- `30-mcp/required-local-mcp-setup.md`
- `30-mcp/usage-and-onboarding.md`
- `10-agents/README.md`
- `60-templates/AGENTS.template.md`

### Recommended behavioral rule

If a repo depends on these tools, its `AGENTS.md` should say so explicitly:

- Playwright must be used when rendered/browser/runtime validation matters.
- Serena must be activated before code-navigation or code-editing work begins.
- Context7 must be used before making framework- or library-dependent changes.

---

## Recommended reading paths

### If you are brand new to this repo

1. `README.md`
2. `00-overview/method-and-scope.md`
3. `00-overview/instruction-layering.md`
4. `30-mcp/required-local-mcp-setup.md`
5. `60-templates/config-and-bootstrap.templates.md`
6. `99-inventory/source-inventory.md`

### If you need to write or improve an `AGENTS.md`

1. `10-agents/README.md`
2. `10-agents/global-vs-project.md`
3. `60-templates/AGENTS.template.md`
4. `40-instructions/project-bootstrap-overview-pattern.md`

### If you need to build or standardize skills

1. `20-skills/README.md`
2. `20-skills/skill-authoring-guide.md`
3. `20-skills/skill-blueprints.md`
4. `60-templates/SKILL.template.md`

### If you need to standardize MCP setup

1. `30-mcp/configured-mcps.md`
2. `30-mcp/required-local-mcp-setup.md`
3. `30-mcp/usage-and-onboarding.md`
4. `60-templates/config-and-bootstrap.templates.md`

### If you need reusable workflows and safety rules

1. `50-workflows/operator-playbooks.md`
2. `50-workflows/safety-and-portability-rules.md`
3. `50-workflows/model-usage-guidance.md`

---

## Suggested quick start

1. Read `00-overview/instruction-layering.md` to understand the intended document hierarchy.
2. Install and verify Playwright, Serena, and Context7 using `30-mcp/required-local-mcp-setup.md`.
3. Create or update your local Codex config from `60-templates/config-and-bootstrap.templates.md`.
4. Create a repo `AGENTS.md` from `60-templates/AGENTS.template.md`.
5. Create or refine skills with `20-skills/skill-authoring-guide.md` and `60-templates/SKILL.template.md`.
6. If the repo is operationally complex, add a bootstrap overview using `40-instructions/project-bootstrap-overview-pattern.md`.
7. Review `99-inventory/source-inventory.md` so you understand the provenance and limitations of the bundle.

---

## What this repo intentionally does NOT contain

This repo should not become a dumping ground for live operational state.

It intentionally excludes:

- secrets
- tokens
- auth files
- session history
- cached runtime state
- logs
- machine-specific paths unless converted to placeholders
- client-specific or environment-specific values that do not generalize
- raw copies of highly specific project runbooks that should be rewritten as templates

---

## Source-of-truth rules for maintaining this repo

If this repository is used as the GitHub source of truth, keep these rules in place:

1. **Do not commit secrets**  
   Keep credentials in `.env` or other ignored local files only.

2. **Prefer templates and patterns over literal environment copies**  
   If something only works for one machine or one repo, generalize it first.

3. **Update provenance when adding derived material**  
   If a document comes from a source artifact, reflect that in `99-inventory/source-inventory.md`.

4. **Keep instruction layers aligned**  
   If MCP expectations change, update the MCP docs, templates, and any related `AGENTS.md` guidance together.

5. **Document dependencies explicitly**  
   If a skill assumes an MCP, runtime, or auth dependency, say so clearly.

6. **Preserve portability**  
   Replace local paths, hostnames, project names, and secrets with placeholders unless a real example is essential.

7. **Keep the README current**  
   If the repo layout or intended usage changes, update this file so the GitHub landing page remains accurate.

---

## Security and secret handling

This repository should be treated as documentation that is safe to publish.

That means:

- never store API keys, tokens, passwords, or auth headers in tracked files
- use `.env` for local secrets only
- commit `.env.example`, not `.env`
- avoid embedding internal URLs, live service identities, or customer-specific operational details unless they have been intentionally generalized

---

## Provenance and limitations

This documentation bundle was derived from a real audited AI agent CLI environment and then rewritten into a portable form.

That means:

- some guidance comes from observed configuration and skill patterns
- some guidance is generalized from one specific environment
- some references, such as model catalogs, are snapshots rather than permanent truths
- some behaviors are inferred from installed tools/config rather than a public vendor spec

For exact provenance and handling decisions, see:

- `00-overview/method-and-scope.md`
- `99-inventory/source-inventory.md`

---

## In one sentence

This repository is the **source-of-truth GitHub documentation repo for AI agent CLI operating standards**, covering **instructions, `AGENTS.md`, skills, MCPs, Serena usage, workflows, templates, and supporting references** in a portable and sanitized form.
