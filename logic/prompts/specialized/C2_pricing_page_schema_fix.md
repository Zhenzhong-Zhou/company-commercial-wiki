# C2 — Pricing page schema fix

## Purpose

Normalize one or more existing pricing pages to schema without changing the underlying pricing meaning.

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/pricing_page.schema.yaml
- logic/schemas/common_enums.schema.yaml

Update only these files:
- [exact pricing page file list]
- log.md

Goals:
- normalize the listed pricing page(s) to schema
- add missing required frontmatter only where needed
- improve source traceability
- preserve existing meaning
- do not invent missing facts
- do not promote undated pricing to current truth

Do not modify any other files.
```