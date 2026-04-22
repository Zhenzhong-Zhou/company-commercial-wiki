# E2 — TERM-* page normalization

## Purpose

Normalize one or more term pages to schema and consistent frontmatter.

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

Update only these files:
- [exact TERM-* file list]
- log.md

Goals:
- normalize these TERM-* pages to the relevant schema
- resolve the page_type rule consistently across all listed TERM-* pages
- fix related frontmatter/status/review flag inconsistencies only where needed
- preserve existing meaning, bilingual structure, and source traceability
- append one short entry to `log.md` if meaningful

Rules:
- do not modify any other files
- do not invent missing facts
- preserve existing IDs, filenames, and valid wikilinks
```