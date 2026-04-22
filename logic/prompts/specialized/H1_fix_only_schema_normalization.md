# H1 — Fix-only schema normalization

## Purpose

Apply targeted schema cleanup only to files already flagged by review.

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/source_note.schema.yaml
- logic/schemas/product_page.schema.yaml
- logic/schemas/pricing_page.schema.yaml
- logic/schemas/term_entry.schema.yaml
- logic/schemas/common_enums.schema.yaml

Update only these files:
- [paste only the files that need fixing from the review]
- log.md

Goals:
- normalize to the relevant schema(s)
- add missing required frontmatter only where needed
- add missing required sections if clearly needed
- improve wikilinks between source, product, pricing, and term pages only where needed
- improve source traceability
- preserve existing meaning
- preserve existing IDs, filenames, and valid wikilinks
- do not invent missing facts
- do not rewrite strong existing content unless needed for compliance, traceability, or link improvement

Also:
- append one short entry to `log.md` if meaningful

Do not modify any other files.
```