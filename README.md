# Agent Skills

A curated set of reusable skills for AI coding agents.

Each skill is a self-contained folder with:

- `SKILL.md` (core instructions and trigger definition)
- `agents/openai.yaml` (UI metadata)
- optional `references/`, `scripts/`, and `assets/`

## Available Skills

| Skill | Focus | Path |
|---|---|---|
| `dioxus` | Practical Dioxus 0.7 web/fullstack development and debugging workflows | `dioxus/` |

## Quick Start

1. Open the skill folder.
2. Review `SKILL.md` for usage and routing rules.
3. Invoke the skill in your prompt with its trigger name (example: `$dioxus`).

## Repository Structure

```text
agent-skills/
└── dioxus/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    ├── references/
    ├── LICENSE-MIT
    └── LICENSE-APACHE
```

## Quality Bar

- Keep skill instructions concise and operational.
- Prefer routing to reference files over duplicating documentation.
- Validate structural correctness after edits.

## Licensing

Each skill can include its own licensing details.
For `dioxus`, upstream documentation attribution and dual-license files are included in the skill folder.
