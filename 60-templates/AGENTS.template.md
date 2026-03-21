# Repository Guidelines

## Project Structure & Module Organization
Describe:

- main application directories
- where shared components/utilities live
- where scripts, tests, and assets live
- which directories are sensitive or externally owned

## Build, Test, and Development Commands
- `<DEV_COMMAND>` — start local development
- `<BUILD_COMMAND>` — build production artifacts
- `<TEST_COMMAND>` — run core tests
- `<LINT_COMMAND>` — run linting/format checks

## Coding Style & Naming Conventions
Document:

- languages in use
- indentation and quoting conventions
- naming conventions
- import/path alias rules
- formatting tools or linters

## Assistant Tooling Requirements
- State whether Playwright, Serena, and Context7 are required.
- State whether Serena must be activated before work begins.
- State whether Context7 is required before framework-dependent changes.
- State whether Playwright is required for rendered/browser-based verification.
- State any deployment/release guardrails.
- State whether skills should be preferred for specific task families.

Recommended baseline wording:

- Playwright, Serena, and Context7 MCPs must be installed in the local Codex CLI before working in this repository.
- Serena must be activated for this repository before code navigation or editing work begins.
- Context7 must be used before making changes that depend on library or framework behavior.
- Playwright must be used for rendered-page verification, browser-based audits, and client-side/runtime checks when raw HTTP inspection is insufficient.

## Testing Guidelines
Document:

- test locations
- naming conventions
- required smoke/integration checks
- any required pre-review validation

## Commit & Pull Request Guidelines
Document:

- commit style
- required review notes
- testing evidence expectations
- screenshot or rollout evidence expectations

## Environment & Configuration
- where secrets belong
- which files must never be committed
- any environment coordination requirements
- any config files that need companion documentation updates

## Skills
List repo-local skills that should be preferred, for example:

- `<SKILL_NAME>`: `<what it handles>`
- `<SKILL_NAME>`: `<what it handles>`
