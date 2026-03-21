# Source Inventory

This inventory lists the discovered source categories, where they were found, how they were handled, and why.

| Source category | Found at | Handling | Why |
|---|---|---|---|
| Codex user config | `~/.codex/config.toml` | rewritten + templated | valuable structure, but contained machine-specific paths and credential-bearing MCP config |
| Codex MCP command help | local `codex mcp --help`, `codex mcp add --help`, `codex mcp get`, `codex mcp list` | summarized | used to verify current CLI installation syntax for the MCP setup guide |
| Codex version metadata | `~/.codex/version.json` | summarized | useful for audit context only |
| Codex model catalog | `~/.codex/models_cache.json` | summarized | useful for model guidance; too volatile to copy as canonical truth |
| Codex auth file | `~/.codex/auth.json` | excluded | secret-bearing |
| Codex history | `~/.codex/history.jsonl` | excluded | session/history state, not portable |
| Codex SQLite state/log files | `~/.codex/logs_*.sqlite`, `~/.codex/state_*.sqlite` | excluded | internal runtime state |
| Codex sessions | `~/.codex/sessions/` | excluded | session state |
| Codex shell snapshots | `~/.codex/shell_snapshots/` | excluded | environment history, not documentation |
| Global system skill: OpenAI docs | `~/.codex/skills/.system/openai-docs/` | rewritten + summarized | portable idea; dependency assumptions must be documented, not copied blindly |
| Global system skill: skill creator | `~/.codex/skills/.system/skill-creator/` | rewritten + distilled | highly reusable guidance |
| Global system skill: skill installer | `~/.codex/skills/.system/skill-installer/` | rewritten + summarized | portable pattern with script/dependency caveats |
| Global custom skill: SEO audit | `~/.codex/skills/seo-audit/` | excluded as direct copy; pattern noted | heavily site-specific |
| Repo `AGENTS.md` | `<REPO_ROOT>/AGENTS.md` | rewritten into template and guidance | structurally useful, but repo-specific verbatim |
| Repo bootstrap overview | `<REPO_ROOT>/CODEX-BOOTSTRAP-OVERVIEW.md` | converted to generic pattern | valuable outline, too environment-specific to copy |
| Repo-local skills: runtime/site/forms/chatbot/content | `<REPO_ROOT>/skills/` | converted to blueprints | useful task-family patterns, but domain/repo-specific details removed |
| Serena global config | `~/.serena/serena_config.yml` | summarized | reusable tool-setup guidance |
| Serena project config | `~/.serena/project.yml`, `~/.serena/projects.yml` | summarized | useful structure for project registration and modes |
| Serena logs | `~/.serena/logs/` | excluded | runtime logs |
| Serena global memories | `~/.serena/memories/global/` | noted as absent | nothing reusable discovered there |
| MCP logs | `~/.mcp/data/*.log` | excluded | runtime logs only |
| MCP resource catalogs | runtime query via MCP tools | summarized as empty | useful limitation note: configured MCPs did not expose resources/templates here |

## Output mapping

| Output doc(s) | Primary source basis |
|---|---|
| `00-overview/*` | config + repo instructions + skills |
| `10-agents/*` | repo `AGENTS.md` |
| `20-skills/*` | system skills + repo skill patterns |
| `30-mcp/*` | Codex config + skill dependency declarations |
| `30-mcp/required-local-mcp-setup.md` | Codex config + live Codex CLI MCP command surface |
| `40-instructions/*` | Serena config + bootstrap overview pattern |
| `50-workflows/*` | model conventions + repo guidance + skill workflows |
| `60-templates/*` | sanitized config/instruction/skill patterns |
| `70-reference/*` | directory layout + model catalog summary |

## Limitations

- No generic user-level `AGENTS.md` was found outside the repo.
- No reusable Serena global memories were present.
- MCP resources/templates were not exposed by the configured servers during this audit.
- Some system behavior is inferred from installed configs and skill docs rather than from a public Codex spec.
