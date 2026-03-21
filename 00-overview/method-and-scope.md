# Method and Scope

## Purpose

This bundle captures portable Codex CLI operating knowledge while removing installation-specific and project-specific baggage.

## Audit method used

The source installation was inspected for:

- user-level Codex config
- installed Codex skills
- Serena config and integration points
- repo-local instruction files
- repo-local skill patterns
- model catalog metadata
- MCP server configuration

Only discoverable artifacts were used. No undocumented behavior was invented.

## Classification rubric

### Reusable as-is

Content that is generic by nature and does not expose secrets or local assumptions.

Examples:

- general skill-authoring principles
- Serena config concepts
- model family descriptions

### Rewritten / sanitized

Content with real operational value that was too tied to one machine, one repo, or one organization to copy directly.

Examples:

- AGENTS.md structure
- bootstrap overviews
- runtime-ops skills
- audit workflows

### Templated

Content where the structure matters more than the original values.

Examples:

- `config.toml` patterns
- `AGENTS.md`
- `SKILL.md`
- `agents/openai.yaml`
- bootstrap notes

### Excluded

Content that should not be reused or redistributed.

Examples:

- auth files
- tokens
- logs
- cached sessions
- repo-specific release IDs
- host-specific service paths

## Portability rules used while writing

1. Preserve intent, not literal wording.
2. Replace real values with placeholders.
3. Remove company, client, product, and hostname references unless presented as generic examples.
4. Prefer patterns over one-off procedures.
5. Mark uncertainty explicitly.
6. Treat state files and logs as non-documentation unless they reveal a reusable category.

## Main themes discovered

- Codex installs often combine global config, repo instructions, skills, and MCP dependencies.
- Serena is most useful when treated as a first-class code-navigation layer, not an optional afterthought.
- Good AGENTS files separate stable global rules from repo-local commands and deployment realities.
- Good skills stay concise and push details into references, scripts, and assets.
- MCP usage works best when each server has a sharply defined purpose.
- Model choice and reasoning effort deserve explicit documentation instead of ad hoc defaults.

## Non-goals

This bundle does not try to:

- recreate the audited environment exactly
- preserve organization-specific workflows verbatim
- export live credentials or configuration values
- replace project onboarding for a new repository
