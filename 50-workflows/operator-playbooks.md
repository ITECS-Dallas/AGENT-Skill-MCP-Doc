# Operator Playbooks

These are generalized workflows extracted from the audited installation.

## 1. Discovery-first workflow

Use when entering an unfamiliar repo or environment.

1. Activate code-intelligence tooling if required.
2. Read the repo `AGENTS.md`.
3. Check whether a project bootstrap overview exists.
4. Inspect Codex config dependencies relevant to the task.
5. Identify applicable skills before improvising.

## 2. Docs-backed code-change workflow

Use when code changes depend on framework or library behavior.

1. Resolve the library/docs source.
2. Query current documentation.
3. Inspect local code patterns.
4. Make changes.
5. Run the narrowest useful validation.

## 3. Skill-driven workflow

Use when the task clearly matches a known task family.

1. Trigger the right skill.
2. Read only the top-level skill guidance first.
3. Load references selectively.
4. Use bundled scripts where available.
5. Validate according to the skill checklist.

## 4. Audit workflow

Use for whole-site or whole-system health checks.

1. Start with the orchestration wrapper if one exists.
2. Review the summary report first.
3. Separate noise from actionable findings.
4. Fix by priority order.
5. Re-run the smallest confirming audit.

## 5. Runtime-ops workflow

Use for build, activate, restart, rollback, or drift investigations.

1. Start with read-only inspection.
2. Read topology and guardrails.
3. Prefer repo-managed scripts.
4. Keep cutover order explicit.
5. Validate after action.

## 6. New-installation bootstrap workflow

1. Create user-level Codex config.
2. register trusted projects
3. install required MCPs
4. add global skills
5. add repo-local `AGENTS.md`
6. add bootstrap overview if needed
7. enable Serena if desired
8. validate model, skill, and MCP setup with smoke queries
