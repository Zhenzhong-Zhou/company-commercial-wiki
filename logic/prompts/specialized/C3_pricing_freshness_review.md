# C3 — Pricing freshness review

## Purpose

Review pricing pages for freshness, risk, and current-seeming wording.

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

Review only.
Do not modify files.

Review only these files:
- [exact pricing page file list]

Check:
- whether pricing is treated as evidence, not timeless truth
- whether channel and currency are explicit where needed
- whether source traceability is present
- whether undated pricing is clearly non-current or pending confirmation
- whether review flags are appropriate

Output:
1. compliant files
2. files needing fixes
3. exact pricing freshness fixes
```
