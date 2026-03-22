# Global vs Project Guidance

## Put Cross-Repo Rules in Global Guidance

Global guidance is the right home for stable defaults such as:

- secret-handling rules
- safe git behavior
- default docs lookup policy
- default MCP expectations across many repos
- communication or review style preferences

Good homes:

- user-level Codex config
- a home-level `AGENTS.md`
- a profile instructions file
- a shared bootstrap repo like this one

## Put Repo Rules in Project `AGENTS.md`

Project `AGENTS.md` should answer questions that change from repo to repo:

- what commands to run
- what directories matter
- what test and review gates apply
- what release or deployment warnings matter
- what repo-local skills should be preferred

Rule of thumb:

If the rule changes per repository, it does not belong in global guidance.

## Put Large Topology in a Bootstrap Overview

When the system is too large for a concise `AGENTS.md`, move high-level topology into a separate bootstrap overview:

- service map
- runtime and deployment model
- logs and diagnostics
- ownership boundaries
- major risks

Keep the overview high-level. Keep the repo contract in `AGENTS.md`.
