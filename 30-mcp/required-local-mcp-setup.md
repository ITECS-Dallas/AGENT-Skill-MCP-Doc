# Required Local MCP Setup

This guide makes one recommendation explicit:

For a practical Codex CLI installation intended for software work, install and verify these three MCPs locally:

- Playwright
- Serena
- Context7

These were the most important general-purpose MCPs in the audited installation.

## Why these three are the baseline

### Playwright

Use for:

- rendered-page verification
- browser-only failures
- client-side schema checks
- DOM and console inspection

### Serena

Use for:

- project activation
- symbol-aware code navigation
- reference tracing
- precise code edits in supported languages

### Context7

Use for:

- library/framework documentation
- version-sensitive API behavior
- implementation decisions that should be grounded in current docs

## Verification command

Run:

```bash
codex mcp list
```

Your baseline should show enabled entries for:

- `playwright`
- `serena`
- `context7`

## Installation patterns verified from the audited CLI

The local Codex CLI on this machine supports:

- `codex mcp add`
- `codex mcp get`
- `codex mcp list`
- `codex mcp remove`

### 1. Install Playwright MCP

```bash
codex mcp add playwright -- npx -y @playwright/mcp@latest --headless
```

Verify:

```bash
codex mcp get playwright
```

Expected pattern:

- transport: `stdio`
- command: `npx`
- args similar to `-y @playwright/mcp@latest --headless`

### 2. Install Serena MCP

```bash
codex mcp add serena -- uvx --from git+https://github.com/oraios/serena serena start-mcp-server --context codex
```

Verify:

```bash
codex mcp get serena
```

Expected pattern:

- transport: `stdio`
- command: `uvx`
- args similar to `--from git+https://github.com/oraios/serena serena start-mcp-server --context codex`

### 3. Install Context7 MCP

Start with:

```bash
codex mcp add context7 --url https://mcp.context7.com/mcp
```

Then verify:

```bash
codex mcp get context7
```

Expected pattern:

- transport: `streamable_http`
- url: `https://mcp.context7.com/mcp`

## Context7 authentication note

In the audited installation, Context7 also required an auth header in Codex config.

Sanitized example:

```toml
[mcp_servers.context7]
url = "https://mcp.context7.com/mcp"
http_headers = { "CONTEXT7_API_KEY" = "<CONTEXT7_API_KEY>" }
```

If your Context7 deployment uses a bearer token instead, prefer the Codex CLI option that matches that auth model.

If the hosted MCP requires custom headers beyond what `codex mcp add` can express in one command, add the server entry and then edit `~/.codex/config.toml` directly.

## Recommended local prerequisites

Install or verify:

- Node.js with `npx`
- Python tooling with `uvx`
- network access to the remote MCP endpoint for Context7

If Playwright needs browser dependencies in your environment, install those according to the Playwright package/runtime requirements for your OS.

## Post-install smoke checks

Run:

```bash
codex mcp list
codex mcp get playwright
codex mcp get serena
codex mcp get context7
```

Then do one practical smoke check:

- use Serena on a repo activation
- use Context7 on one library query
- use Playwright on one rendered-page or DOM check

## AGENTS.md requirement to add

Project `AGENTS.md` files should explicitly require these MCPs and their usage.

Recommended wording:

```md
## Assistant Tooling Requirements
- Playwright, Serena, and Context7 MCPs must be installed in the local Codex CLI before working in this repository.
- Serena must be activated for this repository before code navigation or editing work begins.
- Context7 must be used before making changes that depend on library or framework behavior.
- Playwright must be used for rendered-page verification, browser-based audits, and client-side/runtime checks when raw HTTP inspection is insufficient.
```

Also update any repo bootstrap overview if the project depends heavily on these tools.
