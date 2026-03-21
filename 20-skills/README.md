# Skills Overview

## What was discovered

### Portable system skills

- `openai-docs`
- `skill-creator`
- `skill-installer`

### Project-local skills used as pattern sources

- site audit
- runtime operations
- forms operations
- chatbot operations
- SEO and content workflows

Most repo-local skills were too specific to copy directly, but they exposed reusable design patterns.

## Portable skill summaries

### `openai-docs`

Reusable role:

- look up current official vendor docs
- answer with citations
- prefer authoritative docs tooling over generic browsing
- keep small helper references for upgrade/model-selection contexts

Portability note:

- safe to reuse as a pattern
- verify the required docs MCP is actually installed

### `skill-creator`

Reusable role:

- design concise skills
- choose what belongs in `SKILL.md` versus references/scripts/assets
- enforce progressive disclosure
- validate trigger descriptions and structure

Portability note:

- this was the strongest reusable skill source in the installation

### `skill-installer`

Reusable role:

- list installable skills
- install curated or repo-hosted skills
- rely on helper scripts instead of ad hoc manual copying

Portability note:

- useful pattern, but depends on network, package tooling, and destination-path conventions

## Main skill patterns found

### 1. Documentation lookup skill

Pattern: trigger on “latest/current/how do I use X” requests, prefer authoritative docs tooling, fall back to web only when needed.

### 2. Skill authoring skill

Pattern: teach how to build concise skills with progressive disclosure and validation.

### 3. Installer skill

Pattern: use bundled scripts for deterministic installation and keep network/auth handling explicit.

### 4. Audit skill

Pattern: start from an orchestration wrapper, produce outputs, classify noise vs actionable issues, then triage.

### 5. Runtime-ops skill

Pattern: classify the request first, read topology and guardrails, prefer read-only inspection first, then use deterministic scripts.

### 6. Domain-ops skill

Pattern: classify task subtype, identify canonical references, enforce security guardrails, and validate after each change.

## Reuse recommendations

- Reuse the portable system skill ideas directly.
- Rebuild project skills from blueprints rather than copying them.
- Keep global skills in `~/.codex/skills`.
- Keep repo-specific skills under `<PROJECT_ROOT>/skills` when they depend on repo code, schema, or deployment details.

## Important dependency note

One portable system skill referenced an optional MCP dependency that was not present in the audited global config. Treat skill-declared dependencies as requirements to verify, not assumptions to trust.
