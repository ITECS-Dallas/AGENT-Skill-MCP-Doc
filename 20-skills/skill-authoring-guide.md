# Skill Authoring Guide

Skills are for recurring task families that need extra workflow guidance, local references, or deterministic helpers.

Do not create a skill just to restate general Codex behavior.

## When a Skill Is Worth Creating

Create a skill when at least one of these is true:

- the task family has a repeatable multi-step workflow
- local references or schemas matter
- deterministic scripts are better than ad hoc shell sequences
- there are important guardrails or validations that Codex would not otherwise know

If a short repo `AGENTS.md` section is enough, do not add a skill.

## Core Principles

### Keep the trigger metadata strong

The `name` and `description` in `SKILL.md` are the main trigger surface.

The description should clearly say:

- what the skill does
- when it should be used
- what request shapes should trigger it

### Keep the body concise

Assume Codex is already capable.

Put only the high-value material in `SKILL.md`:

- task-specific workflow
- non-obvious constraints
- reference-selection guidance
- validation requirements

Move detail into references, scripts, and assets.

### Use progressive disclosure

Recommended loading pattern:

1. metadata is always visible
2. `SKILL.md` body loads when the skill triggers
3. `references/`, `scripts/`, and `assets/` are used only when needed

### Match the degree of freedom to the task

- high freedom for heuristic workflows
- medium freedom for preferred patterns with some variation
- low freedom for fragile or security-sensitive operations

## Recommended Skill Anatomy

```text
<skill-name>/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
├── scripts/
└── assets/
```

## What to Put Where

### `SKILL.md`

Put:

- purpose
- when to use and not use it
- core workflow
- reference map
- guardrails
- validation checklist

### `references/`

Put:

- schema notes
- API or policy notes
- long checklists
- variant-specific guidance

### `scripts/`

Put:

- repeatable commands
- installation helpers
- deterministic transforms
- fragile operational helpers

### `assets/`

Put:

- templates
- boilerplate starter files
- files used in final output rather than in reasoning

## Good Skill Categories

Common high-value skill types:

- docs lookup
- install or bootstrap
- audit
- runtime operations
- domain-specific implementation workflows

## Naming Rules

- use lowercase letters, digits, and hyphens
- keep the name short and descriptive
- name the folder exactly after the skill name

## Creation Flow

1. Understand the task family with concrete examples.
2. Identify reusable references, scripts, and assets.
3. Create the scaffold.
4. Write `SKILL.md`.
5. Add supporting resources.
6. Validate.

## Validation Checklist

- frontmatter is valid
- description is trigger-oriented
- instructions are imperative and concise
- reference files are linked from `SKILL.md`
- scripts are actually runnable
- no secret material is embedded
- repo-specific assumptions are explicit

## `agents/openai.yaml` Guidance

Useful fields:

- `interface.display_name`
- `interface.short_description`
- `interface.default_prompt`
- optional `dependencies`
- optional policy flags such as implicit invocation

Only declare dependencies you are prepared to maintain.
