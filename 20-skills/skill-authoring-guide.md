# Skill Authoring Guide

Source basis: distilled primarily from the installed `skill-creator` skill, with supporting patterns from other installed skills.

## Core principles

### Keep the trigger metadata strong

The `name` and `description` in `SKILL.md` are the main trigger surface.

The description should say:

- what the skill does
- when it should be used
- what common request shapes should trigger it

### Keep the body concise

Assume Codex is already capable.

Only include:

- task-specific workflow
- non-obvious constraints
- resource-selection guidance
- validation requirements

Move details into references, scripts, and assets.

### Use progressive disclosure

Recommended loading pattern:

1. metadata always visible
2. `SKILL.md` body loaded when triggered
3. `references/`, `scripts/`, and `assets/` used only when needed

### Match the degree of freedom to the task

- High freedom: heuristics and general workflow
- Medium freedom: preferred patterns and parameterized scripts
- Low freedom: exact sequences for fragile operations

## Recommended skill anatomy

```text
<skill-name>/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
├── scripts/
└── assets/
```

## What to put where

### `SKILL.md`

Put:

- purpose
- scope
- when to use / not use
- workflow
- reference map
- validation checklist

### `references/`

Put:

- schema notes
- API docs excerpts
- policy notes
- long checklists
- playbooks by variant

### `scripts/`

Put:

- repeatable commands
- installation helpers
- deterministic transforms
- fragile operational helpers

### `assets/`

Put:

- icons
- templates
- boilerplate starter files
- artifacts used in output, not agent reasoning

## Naming rules

- use lowercase letters, digits, and hyphens
- keep the name short and descriptive
- name the folder exactly after the skill name

## Recommended creation flow

1. Understand the task family with concrete examples.
2. Identify reusable references, scripts, and assets.
3. Create the skill scaffold.
4. Write `SKILL.md`.
5. Add resources.
6. Validate.
7. Forward-test on real tasks when appropriate.

## Validation checklist

- frontmatter is valid
- description is trigger-oriented
- instructions are imperative and concise
- reference files are linked from `SKILL.md`
- scripts are actually runnable
- no secret material is embedded
- repo-specific assumptions are explicit

## `agents/openai.yaml` guidance

Useful fields observed in installed skills:

- `interface.display_name`
- `interface.short_description`
- `interface.default_prompt`
- optional icons
- optional `dependencies`
- optional policy flags such as implicit invocation

Only include dependency declarations you intend to maintain.
