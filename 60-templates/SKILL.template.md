```text
<skill-name>/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
├── scripts/
└── assets/
```

## `SKILL.md` template

```md
---
name: <skill-name>
description: <what the skill does and when to use it>
---

# <Skill Title>

## Purpose
State what this skill owns.

## When To Use
- <trigger example>
- <trigger example>

## When NOT To Use
- <other skill or general workflow>

## Core Workflow
1. Classify the request.
2. Read the canonical references.
3. Apply the right implementation path.
4. Validate before finalizing.

## Reference Map
- `references/<file>.md` - <when to read it>
- `references/<file>.md` - <when to read it>

## Guardrails
- <security / data / workflow rule>
- <safety rule>

## Validation Checklist
- [ ] <validation item>
- [ ] <validation item>
```

## `agents/openai.yaml` template

```yaml
interface:
  display_name: "<Display Name>"
  short_description: "<One-line user-facing summary>"
  default_prompt: "Use $<skill-name> to <do the task family>."

# Optional
dependencies:
  tools:
    - type: "mcp"
      value: "<MCP_SERVER_NAME>"
      description: "<Why this dependency matters>"

# Optional
policy:
  allow_implicit_invocation: true
```

## Skill authoring reminders

- Keep frontmatter minimal.
- Put trigger information in `description`.
- Keep `SKILL.md` concise.
- Move detail into references.
- Use scripts for deterministic repeated tasks.
- Do not use a skill to restate general Codex behavior.
- Do not store secrets in the skill.
