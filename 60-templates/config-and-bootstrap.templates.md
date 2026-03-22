# Config and Bootstrap Templates

## 1. Codex `config.toml` template

This template is intentionally written as a full-access, high-autonomy Codex CLI profile.

For the current CLI surface, the highest persistent autonomy exposed through `config.toml` is:

- `approval_policy = "never"`
- `sandbox_mode = "danger-full-access"`
- trusted workspace and project paths
- `web_search = "live"`
- `features.multi_agent = true`

The CLI also exposes `--dangerously-bypass-approvals-and-sandbox` for one-off runs. That is a command-line flag, not a persisted `config.toml` key.

Verify keys against the current Codex CLI help and official docs before treating this as canonical. Use it as a starter, not as a frozen spec.

```toml
profile = "<PROFILE_NAME>"
model = "<DEFAULT_MODEL>"
model_reasoning_effort = "<REASONING_LEVEL>"
web_search = "live"

[profiles.<PROFILE_NAME>]
model = "<DEFAULT_MODEL>"
approval_policy = "never"
sandbox_mode = "danger-full-access"
trusted-workspace = true
personality = "pragmatic"
model_reasoning_effort = "<REASONING_LEVEL>"
web_search = "live"
# Optional:
# model_instructions_file = "<CONFIG_PATH>/bootstrap-overview.md"

[projects."<PROJECT_ROOT>"]
trust_level = "trusted"

[features]
multi_agent = true

[mcp_servers.serena]
command = "uvx"
args = ["--from", "git+https://github.com/oraios/serena", "serena", "start-mcp-server", "--context", "codex"]
startup_timeout_sec = 30

[mcp_servers.context7]
command = "npx"
args = ["-y", "@upstash/context7-mcp@latest"]

[mcp_servers.context7.env]
CONTEXT7_API_KEY = "<CONTEXT7_API_KEY>"

[mcp_servers.playwright]
command = "npx"
args = ["-y", "@playwright/mcp@latest", "--headless"]
startup_timeout_sec = 120
tool_timeout_sec = 180

[mcp_servers.<MCP_SERVER_NAME>]
command = "<COMMAND>"
args = ["<ARG1>", "<ARG2>"]

[mcp_servers.<MCP_SERVER_NAME>.env]
<ENV_VAR_NAME> = "<VALUE>"

# Alternative hosted MCP pattern:
# [mcp_servers.<REMOTE_MCP_NAME>]
# url = "https://<HOST>/mcp"
```

If you want the closest one-off equivalent to "everything unlocked" for a single run, invoke Codex with:

```bash
codex exec --dangerously-bypass-approvals-and-sandbox -C <PROJECT_ROOT> "<PROMPT>"
```

## Baseline MCP install commands

These commands match a current Codex CLI command surface with `codex mcp add` support for stdio servers, hosted URL servers, and stdio env injection:

```bash
codex mcp add playwright -- npx -y @playwright/mcp@latest --headless
codex mcp add serena -- uvx --from git+https://github.com/oraios/serena serena start-mcp-server --context codex
codex mcp add context7 --env CONTEXT7_API_KEY="$CONTEXT7_API_KEY" -- npx -y @upstash/context7-mcp@latest
```

If a hosted MCP needs bearer auth, prefer `--bearer-token-env-var`. If it needs custom headers beyond the CLI flags, edit `~/.codex/config.toml` after adding it.

## 2. Bootstrap overview template

```md
# Codex Bootstrap Overview — <REPO_NAME>

## 1. High-Level Stack & Purpose
## 2. Runtime & Hosting Topology
## 3. Source Tree & Key Entry Points
## 4. Data Contracts & Integrations
## 5. Deployment, Maintenance, and Utility Scripts
## 6. Testing & QA Expectations
## 7. Logs, Backups, and Diagnostics
## 8. Risks & Outstanding Issues
```

## 3. New-installation bootstrap notes template

```md
# Environment Bootstrap Notes

## Core paths
- Codex home: <CODEX_HOME>
- Project root: <PROJECT_ROOT>

## Default profile
- name: <PROFILE_NAME>
- model: <DEFAULT_MODEL>
- reasoning: <REASONING_LEVEL>
- approval policy: never
- sandbox mode: danger-full-access
- trusted workspace: true
- web search: live
- multi-agent feature: true

## Global guidance
- optional home-level `AGENTS.md` or profile instructions file
- default approval and sandbox policy
- default docs lookup expectations

## MCPs
- serena: semantic code navigation and project activation
- context7: library/framework documentation lookup
- playwright: rendered-page and browser automation
- <MCP_SERVER_NAME>: <purpose>

## Required local runtimes
- Node / npm / npx
- Python / uv / uvx
- Browser dependencies if using Playwright

## Repo-local instructions
- `AGENTS.md`
- optional bootstrap overview
- repo-local skills

## Validation checklist
- [ ] Codex starts with expected profile
- [ ] required MCPs are installed and enabled
- [ ] required MCPs respond
- [ ] Serena activates for the project if the repo depends on it
- [ ] key skills are discoverable
- [ ] browser automation works if Playwright is required
```

## 4. Serena project config starter

```yaml
project_name: <REPO_NAME>
language: <PRIMARY_LANGUAGE>
read_only: false
tools:
  execute_shell_command: true
```
