# F1 — Targeted fix pass

## Purpose

Apply a focused cleanup pass only to files already identified as needing fixes.

## Use when

- a review pass already identified blockers
- only a small batch of files needs cleanup
- you do not want to rerun a full maintenance batch

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

Task:
Apply a targeted fix pass only for the files and issues already identified by the latest review.

Modify only these files:
- [exact file list]
- log.md

Goals:
- resolve only the listed blockers
- normalize to the relevant schema(s)
- add missing required fields or sections only where clearly needed
- improve source traceability only where needed
- preserve existing meaning
- preserve existing IDs, filenames, and valid wikilinks
- do not invent missing facts
- do not strengthen marketing claims
- do not promote undated pricing to current truth
- do not silently remove uncertainty

Also:
- append one concise `log.md` entry if the cleanup is meaningful

Output:
1. files changed
2. exact fixes applied per file
3. full revised Markdown for each changed file
4. exact `log.md` append block
5. any residual issues still left after cleanup
```
