# I1 — Graph/link improvement

## Purpose

Strengthen meaningful wikilinks between existing source, product, pricing, and term pages.

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

Update only these existing files:
- [exact file list]

Goals:
- strengthen wikilinks between source notes, product pages, pricing pages, and term pages
- reduce isolated pages
- improve source traceability
- keep schema/frontmatter consistency intact
- preserve existing meaning
- do not invent facts
- do not modify any other files beyond the listed files

Also provide in chat only:
- which pages are now well linked
- which pages are still isolated
- next 3 pages that would improve graph view most
```