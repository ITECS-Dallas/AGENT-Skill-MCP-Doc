# Required Local MCP Setup

This repo does not assume one universal MCP stack.

For most software-oriented Codex CLI environments, start by evaluating three high-value MCPs:

- `serena`
- `context7`
- `playwright`

Install only the tools your workflows actually need.

## Why These Three Are Good Defaults

### Serena

Use for:

- project activation
- symbol-aware code navigation
- reference tracing
- precise edits in supported languages

### Context7

Use for:

- current library and framework documentation
- version-sensitive API behavior
- implementation choices that should be grounded in official docs

### Playwright

Use for:

- rendered-page verification
- browser-only failures
- DOM and console inspection
- client-side checks that raw HTTP cannot validate

## Verify the CLI Surface First

Before documenting install steps, verify the local Codex CLI command surface:

```bash
codex mcp --help
codex mcp add --help
codex mcp get --help
codex mcp list
```

At minimum, you should be able to add, inspect, list, and remove MCP entries.

## Example Install Commands

These examples match a current Codex CLI command surface that supports stdio MCPs, URL MCPs, and stdio env injection. Adjust versions and auth details to match the current vendor instructions.

### Install Playwright

```bash
codex mcp add playwright -- npx -y @playwright/mcp@latest --headless
```

### Install Serena

```bash
codex mcp add serena -- uvx --from git+https://github.com/oraios/serena serena start-mcp-server --context codex
```

### Install Context7 using a stdio package

```bash
export CONTEXT7_API_KEY="<CONTEXT7_API_KEY>"
codex mcp add context7 --env CONTEXT7_API_KEY="$CONTEXT7_API_KEY" -- npx -y @upstash/context7-mcp@latest
```

### Optional: install a hosted MCP by URL

```bash
codex mcp add <mcp-name> --url https://<HOST>/mcp
```

If the hosted MCP supports bearer-token auth, prefer:

```bash
codex mcp add <mcp-name> --url https://<HOST>/mcp --bearer-token-env-var <TOKEN_ENV_VAR>
```

If an MCP requires custom headers beyond the `codex mcp add` flags, add the entry and then edit `~/.codex/config.toml` manually.

## Recommended Local Prerequisites

Install or verify:

- Node.js with `npx`
- Python tooling with `uv` and `uvx`
- browser dependencies if using Playwright
- network access for any hosted MCP endpoint

## Post-Install Checks

Run:

```bash
codex mcp list
codex mcp get serena
codex mcp get context7
codex mcp get playwright
```

Then do one real smoke check per tool:

- activate a repo with Serena
- resolve one library lookup with Context7
- run one rendered-page or DOM check with Playwright

Restart Codex after adding or changing MCPs so the updated configuration is picked up cleanly.

## What to Put in `AGENTS.md`

Only document MCP requirements in a repo if the repo truly depends on them.

Useful wording fragments:

- `Serena should be activated before code navigation or symbol-aware edits.`
- `Context7 should be used before making framework- or library-dependent changes.`
- `Playwright should be used when rendered browser behavior must be validated.`
