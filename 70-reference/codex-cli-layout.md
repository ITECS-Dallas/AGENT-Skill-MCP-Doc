# Codex CLI Layout Reference

Source basis: discovered directory structure under `~/.codex/`, `~/.serena/`, and `~/.mcp/`.

## `~/.codex/` categories observed

| Path pattern | Meaning | Reusable? |
|---|---|---|
| `config.toml` | primary user config | yes, after sanitization |
| `version.json` | update metadata | summary only |
| `models_cache.json` | model catalog cache | summary only |
| `skills/` | installed global skills | yes, review individually |
| `auth.json` | auth and token-bearing state | no |
| `history.jsonl` | conversation history | no |
| `sessions/` | session state | no |
| `logs_*.sqlite`, `state_*.sqlite` | internal state/log DBs | no |
| `shell_snapshots/` | command snapshots | no |
| `memories/` | Codex memory storage | case-by-case |

## `~/.serena/` categories observed

| Path pattern | Meaning | Reusable? |
|---|---|---|
| `serena_config.yml` | global Serena defaults | yes, summarized |
| `project.yml`, `projects.yml` | project registrations and overrides | yes, sanitized |
| `logs/` | Serena runtime logs | no |
| `memories/` | Serena memories | case-by-case |

## `~/.mcp/` categories observed

| Path pattern | Meaning | Reusable? |
|---|---|---|
| `data/*.log` | MCP runtime logs | no |

## Useful takeaway

For portability, focus on:

- config
- skill folders
- high-level tool setup
- documented conventions

Avoid treating state, logs, or auth files as documentation sources.
