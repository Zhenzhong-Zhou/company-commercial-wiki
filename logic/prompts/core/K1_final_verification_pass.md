# K1 — Final verification pass

## Purpose

Run a final go / no-go verification pass for a defined batch before demo or commit.

## Use when

- one or more fix passes already ran
- you want to confirm the batch is stable enough to stop editing
- you want a clear demo-ready / commit-ready decision

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
- [exact file list]

Check:
- whether wikilinks meaningfully improved
- whether source traceability improved
- whether schema compliance was preserved
- whether tags/frontmatter remain consistent
- whether any important pages are still isolated or weakly connected
- whether review flags remain appropriate
- whether the batch is demo-ready or commit-ready

Output:
1. compliant / well-linked files
2. files still needing fixes
3. exact remaining fixes
4. whether this batch is demo-ready / commit-ready
```
