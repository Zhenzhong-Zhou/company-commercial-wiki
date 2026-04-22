# B1 — Full maintenance batch

## Purpose

Run one complete vertical-slice maintenance batch for the company commercial wiki.

## Use when

- you want one repeatable maintenance cycle
- one source cluster and directly affected downstream pages should be handled together
- you want a single prompt that covers source notes, downstream pages, links, log, registry, and governance

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
Run one full maintenance batch for the current company commercial wiki.

Execute these steps in order:

1. Identify remaining meaningful raw/demo source files that do not yet have `SRC-*` source notes.
2. Draft proper source notes for them.
3. Update only the directly affected product, pricing, and term pages.
4. Improve meaningful wikilinks among the affected pages.
5. Draft the required `log.md` updates.
6. Update `source_registry.md` and other supporting navigation pages only if needed.
7. Run a lightweight governance pass on the pages touched in this batch.

Rules:
- do not invent missing facts
- do not treat marketing copy as validated fact
- do not treat undated pricing as current truth
- do not silently overwrite conflicting claims
- preserve source traceability
- preserve existing IDs, filenames, and valid wikilinks
- keep changes minimal and repository-ready

Output format:
1. uncovered source list
2. drafted `SRC-*` pages
3. affected downstream pages and exact updates
4. linking improvements
5. `log.md` append block
6. registry/index updates if needed
7. governance findings:
   - must fix now
   - should fix soon
   - okay for now
8. exact file list for the next K1 verification pass
```
