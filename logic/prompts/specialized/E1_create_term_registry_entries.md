# E1 — Create term registry entries

## Purpose

Create one or more reusable term pages for repeated business terminology.

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/term_entry.schema.yaml
- logic/schemas/common_enums.schema.yaml

Use the existing source notes and uploaded files as evidence.

Create exactly these term pages:
- [exact TERM-* file list]

Rules:
- canonical English term first
- preferred Chinese translation explicit
- aliases and discouraged variants separated
- distinguish literal translation from business-ready wording
- preserve source traceability
```