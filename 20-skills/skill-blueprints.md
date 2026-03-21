# Skill Blueprints

This file extracts reusable patterns from installed skills that were too specific to copy directly.

## 1. Docs Lookup Skill Blueprint

Use when a task needs current official docs for a vendor or framework.

### Structure

- trigger on “latest/current/how to use”
- prefer authoritative docs MCP
- keep a small local reference pack for helper context
- explicitly describe fallback behavior when MCP is unavailable

### Best practices

- treat live docs as source of truth
- cite the source
- keep fallback browsing restricted to official domains
- separate stable helper notes from volatile live guidance

## 2. Installer Skill Blueprint

Use when the task is to list or install packaged skills or templates.

### Structure

- bundled scripts for listing/installing
- explicit destination path rules
- explicit restart instructions after installation
- explicit auth/network fallback behavior

### Best practices

- default to deterministic scripts
- document overwrite behavior
- treat repo credentials and tokens as external dependencies

## 3. Audit Skill Blueprint

Use when the task is to scan a system, site, or fleet for health issues.

### Structure

- start with one orchestration command
- document produced artifacts
- distinguish benign noise from actionable issues
- provide a triage order

### Good sections

- primary command
- outputs
- triage flow
- noise filters
- fix priority

## 4. Runtime-Ops Skill Blueprint

Use when the task is to inspect, build, activate, restart, or roll back runtime state.

### Structure

- classify request type first
- read topology and secret/guardrail references first
- start with read-only inspection
- prefer repo-managed scripts over ad hoc shell sequences
- keep cutover order explicit

### Good request classes

- inspect
- no-restart prep
- build artifact
- activate
- rollback
- troubleshoot

## 5. Domain-Ops Skill Blueprint

Use when a repo has a complex subsystem with its own schema, workflows, and security rules.

### Structure

- classify subtype of work
- identify canonical reference files
- document guardrails before implementation
- name required validations

### Good sections

- when to use / not use
- subsystem inventory
- required decisions
- security guardrails
- implementation sequence
- validation checklist

## 6. Content / SEO Skill Blueprint

Use when content quality, metadata, schema, or publishing standards must be enforced repeatedly.

### Structure

- identify source-of-truth files
- define pass/fail checklist
- name output artifacts or required edits
- separate content rules from publishing mechanics

### Warning

These skills become brittle if they encode one brand or one site too deeply. Prefer templates and checklists over brand-locked wording.
