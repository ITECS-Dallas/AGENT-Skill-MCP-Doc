# Model Usage Guidance

Source basis: the installed model catalog observed in `~/.codex/models_cache.json`.

## Families discovered

### Frontier general coding

- `gpt-5.4`
- `gpt-5.2`
- `gpt-5.1`
- `gpt-5`

Use when you want the strongest all-around reasoning and collaboration.

### Codex-optimized variants

- `gpt-5.3-codex`
- `gpt-5.2-codex`
- `gpt-5.1-codex-max`
- `gpt-5.1-codex`
- `gpt-5-codex`

Use when the task is code-heavy and tool-heavy.

### Faster / smaller variants

- `gpt-5.4-mini`
- `gpt-5.3-codex-spark`
- `gpt-5.1-codex-mini`
- `gpt-5-codex-mini`

Use for bounded subtasks, faster iteration, or cheaper helper passes.

## Reasoning effort guidance

Observed reasoning levels varied by model, but the common pattern was:

- `low` - fast, straightforward tasks
- `medium` - sensible default
- `high` - complex or ambiguous work
- `xhigh` - only for the hardest tasks on models that support it

## Practical recommendation matrix

| Task type | Suggested model class | Suggested effort |
|---|---|---|
| general repo work | frontier general coding | medium |
| complex architecture or risky refactor | frontier general coding | high or xhigh |
| code-heavy implementation | codex-optimized | medium or high |
| quick bounded helper task | mini / spark | low or medium |
| long-running multi-step execution | stronger frontier or codex model | medium or high |

## Defaulting guidance

The audited installation defaulted to a strong frontier model with a high reasoning setting. That is defensible for high-autonomy coding, but not always cost- or latency-optimal.

A reusable rule:

- start with `medium`
- raise to `high` when ambiguity or risk grows
- use smaller models only for well-scoped work

## Caution

Do not hard-code your docs to one model forever. Treat the available catalog as versioned and review it periodically.
