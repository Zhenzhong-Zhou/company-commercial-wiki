# C1 — Build or update one pricing page

## Purpose

Create or update exactly one pricing page using traceable pricing evidence.

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

Use the relevant uploaded file(s) and/or source note(s).

Create or update exactly one file:
- `wiki/06_pricing/PRICE-XXXX.md`

Rules:
- treat pricing as evidence, not timeless truth
- keep channel, currency, source_id, and date_observed explicit
- do not merge channel prices into one official price without confirmation
- preserve `pending_confirmation` and review flags where needed
- append one short entry to `log.md` if updated
```