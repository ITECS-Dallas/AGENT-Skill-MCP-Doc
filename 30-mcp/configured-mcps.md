# Configured MCPs

Source basis: sanitized from the audited `~/.codex/config.toml`, plus observed skill dependencies.

## MCPs discovered in config

| MCP | Purpose | Transport pattern | Observed configuration pattern | Portability |
|---|---|---|---|---|
| Playwright | Browser automation and rendered-page verification | stdio via `npx` | local package invocation | portable after package review |
| Context7 | documentation lookup for libraries/frameworks | remote MCP URL + auth header | hosted endpoint with API key | portable with new key |
| Serena | semantic code navigation and editing | stdio via `uvx` | launches server from package/repo | portable after install review |
| Jira | issue/project data access | stdio via `npx` + env vars | package with API token and site/user envs | portable with new credentials |

## Required baseline MCP set for a fresh software-oriented install

Treat these as the recommended minimum baseline:

- Playwright
- Serena
- Context7

See `required-local-mcp-setup.md` for installation and AGENTS guidance.

## MCP referenced by a skill but not present in global config

| MCP | Where it appeared | Why it matters |
|---|---|---|
| `openaiDeveloperDocs` | installed `openai-docs` system skill | skill assumes this MCP can be installed and used for official docs lookup |

## Key configuration observations

- MCPs were declared globally, not per project.
- Both stdio and remote-URL MCP styles were used.
- Credential-bearing MCPs were configured through env vars or HTTP headers.
- The current environment exposed tools, but `list_mcp_resources` and `list_mcp_resource_templates` returned no resources/templates during this audit.

## Practical meaning of the empty resource listing

Do not assume every configured MCP exposes:

- resources
- resource templates
- browseable catalogs

Some MCPs are primarily tool providers rather than resource catalogs.

## Recommended generic config pattern

Use:

- stdio MCPs for local tooling and CLIs
- remote URL MCPs for hosted docs/data services
- env vars or header placeholders for secrets
- explicit timeout values for slower integrations

See `../60-templates/config-and-bootstrap.templates.md` for a reusable template.
