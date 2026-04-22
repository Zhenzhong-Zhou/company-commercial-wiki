# G1 — Review-only schema QA

## Purpose

Run a schema-focused review over a defined file batch without modifying files.

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

Check only these files:
- [exact file list]

For each file, report:
1. schema used
2. missing required frontmatter fields
3. invalid enum/status values
4. missing required sections
5. weak or missing source traceability
6. bilingual structure issues
7. customer-facing review flag issues
8. whether the file is schema-compliant, partially compliant, or non-compliant

Also report:
- which pages are now linked
- which pages are still isolated
- the next 3 pages that would improve graph view most

Output concise review notes only.
```