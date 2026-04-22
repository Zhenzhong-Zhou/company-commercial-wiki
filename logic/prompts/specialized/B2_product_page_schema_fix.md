# B2 — Product page schema fix

## Purpose

Normalize one or more existing product pages to schema without broad rewriting.

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/product_page.schema.yaml
- logic/schemas/common_enums.schema.yaml

Update only these files:
- [exact product page file list]
- log.md

Goals:
- normalize the listed product page(s) to schema
- add missing required frontmatter only where needed
- fix invalid enum/status values
- add missing required sections only where clearly needed
- preserve source traceability
- preserve existing meaning
- do not invent missing facts

Do not modify any other files.
```
