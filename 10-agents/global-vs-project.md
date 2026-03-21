# Global vs Project Guidance for AGENTS

## Use global guidance for stable cross-project rules

Examples:

- how the agent should communicate
- safe git behavior
- secret-handling rules
- when live docs must be consulted
- default MCP or Serena expectations across many repos

Good homes:

- user-level config
- a shared operator guide
- reusable documentation bundle like this one

## Use project `AGENTS.md` for repo-local operating rules

Examples:

- actual build/test commands
- actual directory structure
- actual review expectations
- actual release workflow warnings
- repo-local skills

Good rule of thumb:

If the rule changes from repo to repo, it belongs in `AGENTS.md`.

## Use a bootstrap overview for high-level system topology

Examples:

- service map
- deployment model
- logs and diagnostics locations
- release architecture
- risk register

If the material is too big or too architectural for `AGENTS.md`, move it into a bootstrap overview.

## Specific recommendation for MCP-dependent repos

Keep the actual install/run details in:

- a setup guide
- a bootstrap overview
- a config template

But put the behavioral requirement in `AGENTS.md`, for example:

- which MCPs must be installed
- which MCPs must be activated
- which tasks must use which MCPs
