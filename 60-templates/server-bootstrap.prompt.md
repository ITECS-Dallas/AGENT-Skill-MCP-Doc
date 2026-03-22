# Codex CLI Server Bootstrap Prompt Template

Use this prompt when Codex CLI is already installed well enough to run one session on a fresh Linux server, and you want Codex to perform the rest of the machine and project bootstrap.

This prompt tells Codex to:

- clone and use this docs repo as the local bootstrap source
- install missing system and language prerequisites
- configure `~/.codex`
- install the required MCPs
- clone and prepare the target project
- create repo-local `AGENTS.md`
- add an optional bootstrap overview when the project is complex
- validate the resulting setup

## Template Prompt

```text
You are bootstrapping a fresh Linux server for Codex CLI-driven development.

Operate directly in the shell and complete the setup end to end. Do not stop at analysis or a proposed plan. Execute the work.

Use this repository as the bootstrap source of truth:
- Docs repo URL: <DOCS_REPO_URL>
- Docs repo branch or ref: <DOCS_REPO_REF>
- Local docs checkout path: <DOCS_CHECKOUT_PATH>

Bootstrap this target project:
- Project repo URL: <PROJECT_REPO_URL>
- Project repo branch or ref: <PROJECT_REPO_REF>
- Local project checkout path: <PROJECT_CHECKOUT_PATH>
- Primary language or stack: <PRIMARY_STACK>
- Project complexity: <simple|moderate|complex>

Operator choices for this machine:
- Codex profile name: <CODEX_PROFILE_NAME>
- Default model: <DEFAULT_MODEL>
- Reasoning effort: <REASONING_LEVEL>
- Approval policy: <APPROVAL_POLICY or never for max autonomy>
- Sandbox mode: <SANDBOX_MODE or danger-full-access for max autonomy>
- Enable web search: <yes|no>
- Enable multi_agent feature: <yes|no>
- Enable Serena: <yes|no>
- Enable Context7: <yes|no>
- Enable Playwright: <yes|no>
- Additional MCPs to install: <NONE or list>

Credentials or env vars that may already be present:
- CONTEXT7_API_KEY: <present|missing>
- Other MCP env vars: <list or NONE>

Rules:
1. Treat the docs repo as a bootstrap reference, not as a runtime repo to embed inside the project.
2. Create the live Codex artifacts Codex actually uses:
   - `~/.codex/config.toml`
   - global skills only if truly reusable across repos
   - project-root `AGENTS.md`
   - optional project bootstrap overview if the repo is complex
   - repo-local skills only if they are justified by recurring project-specific workflows
3. Use these docs from the bootstrap repo as the canonical reference set:
   - `00-overview/instruction-layering.md`
   - `10-agents/README.md`
   - `10-agents/global-vs-project.md`
   - `20-skills/skill-authoring-guide.md`
   - `30-mcp/required-local-mcp-setup.md`
   - `30-mcp/usage-and-onboarding.md`
   - `40-instructions/project-bootstrap-overview-pattern.md`
   - `40-instructions/serena-integration-guide.md`
   - `50-workflows/safety-and-portability-rules.md`
   - `60-templates/config-and-bootstrap.templates.md`
   - `60-templates/AGENTS.template.md`
   - `60-templates/SKILL.template.md`
4. Install only the MCPs and dependencies this machine and project actually need.
5. Keep secrets out of committed files. Use env vars or local config where appropriate.
6. If a command needs elevation and the session can request it, do so. If elevation is impossible, stop only for that blocker and report the exact command and reason.
7. Before writing repo-local guidance, inspect the actual project structure and commands. Do not invent stack-specific commands or workflows.
8. Keep changes concise and operational. Do not generate bloated documentation.

Execution phases:

Phase 1: Bootstrap source and environment discovery
- Ensure the docs repo exists locally at `<DOCS_CHECKOUT_PATH>`. Clone it if missing; if present, fetch and checkout `<DOCS_REPO_REF>`.
- Detect the Linux distribution and package manager.
- Inspect the current machine for required tools such as `git`, `rg`, `curl`, `node`, `npm`, `npx`, `python3`, `pip`, `uv`, and `uvx`.
- Verify whether Codex CLI is already installed and callable. If it is not callable, stop immediately and print the minimal manual steps required to get Codex CLI installed so this bootstrap prompt can be rerun.

Phase 2: Install machine prerequisites
- Install missing system prerequisites using the distro-appropriate package manager.
- Install missing language/runtime prerequisites needed for the selected MCPs and project workflows.
- If Playwright is enabled, install any browser or OS dependencies required for headless use.

Phase 3: Configure Codex home
- Create `~/.codex` if missing.
- Build `~/.codex/config.toml` using the docs repo template as the base, adapted to the chosen profile, model, reasoning level, approval policy, sandbox mode, web search setting, multi-agent setting, and MCP set.
- Register the project path under `[projects]` with trusted settings if appropriate for the requested workflow.
- Do not copy placeholders from the template when real values are available from this prompt.
- If the operator is asking for maximum Codex CLI autonomy and access, use:
  - `approval_policy = "never"`
  - `sandbox_mode = "danger-full-access"`
  - `trusted-workspace = true`
  - `web_search = "live"`
  - `[features].multi_agent = true`

Phase 4: Install and verify MCPs
- Verify the live Codex CLI MCP command surface before documenting or using it.
- Install Serena, Context7, and Playwright only if enabled.
- Install any additional MCPs requested in the prompt.
- Use env-based auth for MCPs where applicable.
- Restart or refresh Codex only if needed by the local setup.
- Verify installation with `codex mcp list` and targeted `codex mcp get <name>` checks.

Phase 5: Clone and inspect the target project
- Ensure the target project exists locally at `<PROJECT_CHECKOUT_PATH>`. Clone it if missing; if present, fetch and checkout `<PROJECT_REPO_REF>`.
- Inspect the repo structure, existing docs, package manifests, build files, test files, and any existing `AGENTS.md` or equivalent.
- Determine the canonical build, test, lint, and development commands from the project itself.
- Determine whether the repo is large enough to justify a separate bootstrap overview.
- Determine whether repo-local skills are actually warranted.

Phase 6: Materialize repo-local guidance
- Create or update the project-root `AGENTS.md` using the template and the project’s real commands and rules.
- Keep only repo-local rules in `AGENTS.md`.
- If the repo complexity is `complex`, or if the project inspection shows enough topology to justify it, create a concise bootstrap overview document in the project root and reference it from config or docs if useful.
- Only create repo-local skills if inspection shows recurring, project-specific workflows that deserve them.

Phase 7: Validate end to end
- Validate the resulting `~/.codex/config.toml`.
- Validate MCP availability and auth where applicable.
- Validate that the project has a coherent `AGENTS.md`.
- If Serena is enabled, activate the project and confirm the workflow is viable.
- If Context7 is enabled, perform one safe docs lookup.
- If Playwright is enabled, perform one safe smoke check relevant to the machine.
- Run the narrowest relevant project validation command that proves the repo-local guidance is grounded in reality.

Phase 8: Final reporting
- Report exactly what was installed, created, or updated.
- Report any blockers, skipped items, or assumptions.
- Report the final paths for:
  - docs repo checkout
  - project checkout
  - `~/.codex/config.toml`
  - project `AGENTS.md`
  - optional bootstrap overview
  - any created skills
- Keep the summary concise and operational.

Success criteria:
- The Linux server has the required prerequisites for the requested workflow.
- Codex home is configured for the chosen profile and project.
- Required MCPs are installed and verified.
- The target project is checked out and inspected.
- The project has a grounded `AGENTS.md` based on real repo facts.
- Optional overview and skills are created only if justified.
- A short validation summary confirms the environment is ready for use.
```

## Prefilled Docs-Repo Variant

Use this version if `https://github.com/ITECS-Dallas/AGENT-Skill-MCP-Doc.git` is the canonical bootstrap docs repo:

```text
You are bootstrapping a fresh Linux server for Codex CLI-driven development.

Operate directly in the shell and complete the setup end to end. Do not stop at analysis or a proposed plan. Execute the work.

Use this repository as the bootstrap source of truth:
- Docs repo URL: https://github.com/ITECS-Dallas/AGENT-Skill-MCP-Doc.git
- Docs repo branch or ref: <DOCS_REPO_REF>
- Local docs checkout path: <DOCS_CHECKOUT_PATH>

Bootstrap this target project:
- Project repo URL: <PROJECT_REPO_URL>
- Project repo branch or ref: <PROJECT_REPO_REF>
- Local project checkout path: <PROJECT_CHECKOUT_PATH>
- Primary language or stack: <PRIMARY_STACK>
- Project complexity: <simple|moderate|complex>

Operator choices for this machine:
- Codex profile name: <CODEX_PROFILE_NAME>
- Default model: <DEFAULT_MODEL>
- Reasoning effort: <REASONING_LEVEL>
- Approval policy: <APPROVAL_POLICY or never for max autonomy>
- Sandbox mode: <SANDBOX_MODE or danger-full-access for max autonomy>
- Enable web search: <yes|no>
- Enable multi_agent feature: <yes|no>
- Enable Serena: <yes|no>
- Enable Context7: <yes|no>
- Enable Playwright: <yes|no>
- Additional MCPs to install: <NONE or list>

Credentials or env vars that may already be present:
- CONTEXT7_API_KEY: <present|missing>
- Other MCP env vars: <list or NONE>

Rules:
1. Treat the docs repo as a bootstrap reference, not as a runtime repo to embed inside the project.
2. Create the live Codex artifacts Codex actually uses:
   - `~/.codex/config.toml`
   - global skills only if truly reusable across repos
   - project-root `AGENTS.md`
   - optional project bootstrap overview if the repo is complex
   - repo-local skills only if they are justified by recurring project-specific workflows
3. Use these docs from the bootstrap repo as the canonical reference set:
   - `00-overview/instruction-layering.md`
   - `10-agents/README.md`
   - `10-agents/global-vs-project.md`
   - `20-skills/skill-authoring-guide.md`
   - `30-mcp/required-local-mcp-setup.md`
   - `30-mcp/usage-and-onboarding.md`
   - `40-instructions/project-bootstrap-overview-pattern.md`
   - `40-instructions/serena-integration-guide.md`
   - `50-workflows/safety-and-portability-rules.md`
   - `60-templates/config-and-bootstrap.templates.md`
   - `60-templates/AGENTS.template.md`
   - `60-templates/SKILL.template.md`
4. Install only the MCPs and dependencies this machine and project actually need.
5. Keep secrets out of committed files. Use env vars or local config where appropriate.
6. If a command needs elevation and the session can request it, do so. If elevation is impossible, stop only for that blocker and report the exact command and reason.
7. Before writing repo-local guidance, inspect the actual project structure and commands. Do not invent stack-specific commands or workflows.
8. Keep changes concise and operational. Do not generate bloated documentation.

Execution phases:

Phase 1: Bootstrap source and environment discovery
- Ensure the docs repo exists locally at `<DOCS_CHECKOUT_PATH>`. Clone it if missing; if present, fetch and checkout `<DOCS_REPO_REF>`.
- Detect the Linux distribution and package manager.
- Inspect the current machine for required tools such as `git`, `rg`, `curl`, `node`, `npm`, `npx`, `python3`, `pip`, `uv`, and `uvx`.
- Verify whether Codex CLI is already installed and callable. If it is not callable, stop immediately and print the minimal manual steps required to get Codex CLI installed so this bootstrap prompt can be rerun.

Phase 2: Install machine prerequisites
- Install missing system prerequisites using the distro-appropriate package manager.
- Install missing language/runtime prerequisites needed for the selected MCPs and project workflows.
- If Playwright is enabled, install any browser or OS dependencies required for headless use.

Phase 3: Configure Codex home
- Create `~/.codex` if missing.
- Build `~/.codex/config.toml` using the docs repo template as the base, adapted to the chosen profile, model, reasoning level, approval policy, sandbox mode, web search setting, multi-agent setting, and MCP set.
- Register the project path under `[projects]` with trusted settings if appropriate for the requested workflow.
- Do not copy placeholders from the template when real values are available from this prompt.
- If the operator is asking for maximum Codex CLI autonomy and access, use:
  - `approval_policy = "never"`
  - `sandbox_mode = "danger-full-access"`
  - `trusted-workspace = true`
  - `web_search = "live"`
  - `[features].multi_agent = true`

Phase 4: Install and verify MCPs
- Verify the live Codex CLI MCP command surface before documenting or using it.
- Install Serena, Context7, and Playwright only if enabled.
- Install any additional MCPs requested in the prompt.
- Use env-based auth for MCPs where applicable.
- Restart or refresh Codex only if needed by the local setup.
- Verify installation with `codex mcp list` and targeted `codex mcp get <name>` checks.

Phase 5: Clone and inspect the target project
- Ensure the target project exists locally at `<PROJECT_CHECKOUT_PATH>`. Clone it if missing; if present, fetch and checkout `<PROJECT_REPO_REF>`.
- Inspect the repo structure, existing docs, package manifests, build files, test files, and any existing `AGENTS.md` or equivalent.
- Determine the canonical build, test, lint, and development commands from the project itself.
- Determine whether the repo is large enough to justify a separate bootstrap overview.
- Determine whether repo-local skills are actually warranted.

Phase 6: Materialize repo-local guidance
- Create or update the project-root `AGENTS.md` using the template and the project’s real commands and rules.
- Keep only repo-local rules in `AGENTS.md`.
- If the repo complexity is `complex`, or if the project inspection shows enough topology to justify it, create a concise bootstrap overview document in the project root and reference it from config or docs if useful.
- Only create repo-local skills if inspection shows recurring, project-specific workflows that deserve them.

Phase 7: Validate end to end
- Validate the resulting `~/.codex/config.toml`.
- Validate MCP availability and auth where applicable.
- Validate that the project has a coherent `AGENTS.md`.
- If Serena is enabled, activate the project and confirm the workflow is viable.
- If Context7 is enabled, perform one safe docs lookup.
- If Playwright is enabled, perform one safe smoke check relevant to the machine.
- Run the narrowest relevant project validation command that proves the repo-local guidance is grounded in reality.

Phase 8: Final reporting
- Report exactly what was installed, created, or updated.
- Report any blockers, skipped items, or assumptions.
- Report the final paths for:
  - docs repo checkout
  - project checkout
  - `~/.codex/config.toml`
  - project `AGENTS.md`
  - optional bootstrap overview
  - any created skills
- Keep the summary concise and operational.

Success criteria:
- The Linux server has the required prerequisites for the requested workflow.
- Codex home is configured for the chosen profile and project.
- Required MCPs are installed and verified.
- The target project is checked out and inspected.
- The project has a grounded `AGENTS.md` based on real repo facts.
- Optional overview and skills are created only if justified.
- A short validation summary confirms the environment is ready for use.
```

## Notes

- This prompt assumes Codex CLI is already installed enough to run one session. If not, Codex cannot bootstrap itself and should stop with the minimal manual install step.
- Treat `<DOCS_CHECKOUT_PATH>` as a separate admin/bootstrap checkout such as `~/codex-bootstrap-docs`, not as a folder inside the target project.
- Treat `<PROJECT_CHECKOUT_PATH>` as the real working repo path such as `~/src/<project>`.
