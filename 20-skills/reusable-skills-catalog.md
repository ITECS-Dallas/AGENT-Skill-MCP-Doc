# Reusable Skills Catalog

## Directly reusable concepts discovered

| Skill / pattern | Best reusable idea | What to customize |
|---|---|---|
| `openai-docs` | docs-first vendor support skill | MCP dependency, reference files, vendor scope |
| `skill-creator` | concise skill-authoring workflow | your scaffolding scripts and validation tools |
| `skill-installer` | deterministic install/list flow | source repo, auth method, destination path |

## Indirectly reusable blueprints derived from repo skills

| Blueprint | Derived from | Best reusable idea |
|---|---|---|
| audit skill | site health + SEO skills | orchestrate first, triage second |
| runtime-ops skill | stack/runtime ops skills | classify request type and prefer read-only inspection first |
| domain-ops skill | forms/chatbot/content skills | keep subsystem references, guardrails, and validation close together |

## Recommendation

When bootstrapping a new installation:

1. install or create only a few high-value global skills
2. keep repo-bound skills inside the repo
3. document dependencies explicitly
4. prefer blueprints over direct copies when the source skill knows too much about one product or company
