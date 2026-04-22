# H2 — Schema bootstrap / fix

## Purpose

Repair or bootstrap the schema layer itself when schema files are missing, empty, or inconsistent.

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Update only these files:
1. logic/schemas/knowledge_object.schema.yaml
2. logic/schemas/source_note.schema.yaml
3. logic/schemas/product_page.schema.yaml
4. logic/schemas/pricing_page.schema.yaml
5. logic/schemas/term_entry.schema.yaml
6. logic/schemas/common_enums.schema.yaml
7. log.md

Goals:
- ensure each listed schema file exists at the exact path
- ensure each schema file is non-empty and usable
- ensure enum/status definitions are consistent across the schema set
- preserve existing schema intent where already valid
- do not invent business facts
- append one short entry to `log.md` if meaningful

Rules:
- do not modify any other files
- keep file names and paths exactly as listed
- if a schema already exists and is valid, only normalize minimally
- prefer consistency over expansion
```
