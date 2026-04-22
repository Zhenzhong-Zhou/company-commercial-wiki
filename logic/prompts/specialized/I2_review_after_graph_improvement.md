# I2 — Review after graph improvement

## Purpose

Verify whether a link-improvement pass actually produced meaningful graph improvements.

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

Review only.
Do not modify files.

Review only these files:
- [same file list you just updated]

Check:
- whether wikilinks meaningfully improved
- whether source traceability improved
- whether each file now links to the right related page types
- whether any important pages are still isolated
- whether backlinks / outgoing-link quality is still weak
- whether schema compliance was preserved

Output:
1. files now well-linked
2. files still weakly linked or isolated
3. exact remaining link gaps
4. top 3 next pages to update for graph improvement
5. whether the batch is now graph-ready enough for demo
```