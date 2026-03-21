# Config and Bootstrap Templates

## 1. Codex `config.toml` template

```toml
profile = "<PROFILE_NAME>"
model = "<DEFAULT_MODEL>"
model_reasoning_effort = "<REASONING_LEVEL>"
web_search = "<WEB_SEARCH_MODE>"

[profiles.<PROFILE_NAME>]
model = "<MODEL>"
approval_policy = "<APPROVAL_POLICY>"
sandbox_mode = "<SANDBOX_MODE>"
personality = "<PERSONALITY>"
trusted-workspace = true
# Optional:
model_instructions_file = "<CONFIG_PATH>/bootstrap-overview.md"

[projects."<PROJECT_ROOT>"]
trust_level = "trusted"

[features]
multi_agent = true

[mcp_servers.playwright]
command = "npx"
args = ["-y", "@playwright/mcp@latest", "--headless"]
startup_timeout_sec = 120
tool_timeout_sec = 180

[mcp_servers.context7]
url = "<CONTEXT7_MCP_URL>"
http_headers = { "CONTEXT7_API_KEY" = "<CONTEXT7_API_KEY>" }

[mcp_servers.serena]
command = "uvx"
args = ["--from", "git+https://github.com/oraios/serena", "serena", "start-mcp-server", "--context", "codex"]

[mcp_servers.<MCP_SERVER_NAME>]
command = "<COMMAND>"
args = ["<ARG1>", "<ARG2>"]

[mcp_servers.<MCP_SERVER_NAME>.env]
<ENV_VAR_NAME> = "<VALUE>"
```

## Baseline MCP install commands

These commands were verified against the audited local Codex CLI command surface:

```bash
codex mcp add playwright -- npx -y @playwright/mcp@latest --headless
codex mcp add serena -- uvx --from git+https://github.com/oraios/serena serena start-mcp-server --context codex
codex mcp add context7 --url https://mcp.context7.com/mcp
```

If Context7 needs custom headers, edit `~/.codex/config.toml` after adding it.

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

## MCPs
- playwright: rendered-page and browser automation
- serena: semantic code navigation and project activation
- context7: library/framework documentation lookup
- <MCP_SERVER_NAME>: <purpose>

## Required local runtimes
- Node / npm / npx
- Python / uv / uvx
- Browser dependencies if using Playwright

## Repo-local instructions
- `AGENTS.md`
- bootstrap overview
- repo-local skills

## Validation checklist
- [ ] Codex starts with expected profile
- [ ] Playwright, Serena, and Context7 are installed and enabled
- [ ] required MCPs respond
- [ ] Serena activates for the project
- [ ] key skills are discoverable
- [ ] test browser automation works if enabled
```

## 4. Serena project config starter

```yaml
project_name: <REPO_NAME>
language: <PRIMARY_LANGUAGE>
read_only: false
tools:
  execute_shell_command: true
```
