# USER_WORKFLOWS.md

## Purpose

This file is the operator guide for using the commercial LLM Wiki.

It explains:
- the default operator path
- when to use specialized workflows instead
- which files are usually touched
- what to review after each run
- which prompt templates match each workflow

This is the human-facing workflow guide.

It is not the same as:
- `SYSTEM_PROMPT.md`
- `AGENTS.md`
- `RULES.md`
- `LINT.md`
- `PROMPT_LIBRARY.md`

Exact prompt bodies live under:
- `logic/prompts/core/`
- `logic/prompts/specialized/`
- `logic/prompts/demo/`
- `logic/prompts/refactor/`

---

# 1. Default operator path

Most normal work should follow this path:

1. **B1 — Full maintenance batch**
2. **F1 — Targeted fix pass** if blockers are found
3. **K1 — Final verification pass**

This is the default vertical-slice workflow.

Use it for:
- one source cluster
- directly affected product / pricing / term pages
- meaningful wikilink improvement
- log update
- registry/index update if needed
- lightweight governance review
- final commit/demo check

---

# 2. Default workflow details

## Workflow B1 — Full maintenance batch

### Use when
- you want one complete vertical-slice pass
- you want one repeatable maintenance cycle
- one source cluster and its downstream pages should be handled together

### Covers
1. source intake coverage
2. downstream page updates
3. linking
4. log update
5. registry/index consistency
6. lightweight governance check

### Typical outputs
- new or updated `SRC-*` pages
- updated `PROD-*`, `PRICE-*`, `TERM-*` pages
- updated `source_registry.md` and sometimes `index.md`
- one concise `log.md` block
- governance findings
- exact file list for final verification

### Why use this workflow
This is the main maintenance loop for the vault.

---

## Workflow F1 — Targeted fix pass

### Use when
- a review pass already identified blockers
- only a small set of files need cleanup
- you do not want to rerun a full batch

### Typical outputs
- small schema/traceability/link fixes
- preserved meaning
- one concise `log.md` note if meaningful

### Why use this workflow
This is the safest way to resolve remaining blockers after review.

---

## Workflow K1 — Final verification pass

### Use when
- a batch or fix pass is finished
- you want a go/no-go check before demo or commit

### Typical outputs
- compliant file list
- remaining blockers if any
- demo-ready / commit-ready decision

### Why use this workflow
This gives the operator a clean stopping point.

---

# 3. Specialized maintenance workflows

Use these only when the default path is too broad for the task.

## Source-only
- A1 — create one new source note
- A2 — create missing source files only

## Product-only
- B2 — fix one or more product pages to schema

## Pricing-only
- C1 — build or update one pricing page
- C2 — pricing page schema fix
- C3 — pricing freshness review

## Term-only
- E1 — create term registry entries
- E2 — normalize TERM-* pages

## Schema / governance
- G1 — review-only schema QA
- H1 — targeted schema normalization
- H2 — schema bootstrap/fix

## Graph / link
- I1 — strengthen source/product/pricing/term links
- I2 — review graph quality after link improvement

## Recovery
- J1 — create only missing files

---

# 4. Refactor workflows

Use these only for structural maintenance of the workflow / prompt system itself.
They are not part of the normal maintenance loop.

- R1 — rename or reorganize prompt-library references
- R2 — workflow / prompt integrity review (review only)
- R3 — workflow / prompt alignment cleanup

---

# 5. Demo and proof workflows

Use these to prove the wiki is working, not to modify it.

## D1 — Product retrieval + traceability
Checks whether one product can be answered with source-backed structure.

## D2 — Fact vs marketing copy
Checks whether product facts and marketing wording are separated cleanly.

## D3 — Pricing governance test
Checks whether pricing is treated as evidence, not timeless truth.

## D4 — Term registry test
Checks bilingual terminology consistency.

## D5 — Cross-page linking test
Checks whether the vault behaves like a connected wiki.

## Q1 — Maintenance-readiness test
Checks whether linked pages are operationally maintainable.

---

# 6. Recommended usage order

## Default path
1. B1
2. F1 if needed
3. K1

## If only a few blockers remain
1. F1
2. K1

## If proving the system to others
1. D5
2. D1
3. D2
4. D3
5. D4
6. Q1

## If the batch is schema-heavy or structurally messy
1. G1 — review-only schema QA
2. H1 or H2 — targeted schema fix / schema bootstrap
3. K1 — final verification pass

## After a large prompt / workflow refactor
1. R1 or R3 — rename / cleanup passes that write changes
2. R2 — workflow / prompt integrity review (review only)
3. F1 — targeted fix pass if R2 flags residual issues
4. K1 only if the refactor also touched real batch files or workflow outputs
5. D1 / D3 / D5 as a proof check if you want to confirm the system still behaves correctly

---

# 7. What to review after each run

## After B1
- were source notes created or updated first?
- were only directly affected downstream pages changed?
- are links meaningful?
- was `log.md` updated?
- was `source_registry.md` updated if needed?
- are governance findings clear?

## After F1
- were only flagged files touched?
- were schema/enum/traceability fixes minimal?
- was uncertainty preserved?

## After K1
- are there any blockers left?
- is the batch demo-ready?
- is the batch commit-ready?

---

# 8. Minimal operator rules

- Do not start from product pages if no source note exists yet.
- Do not treat marketing copy as validated fact.
- Do not treat undated pricing as current truth.
- Do not publish high-risk customer-facing English without review.
- Do not invent missing facts.
- Preserve existing IDs, filenames, and valid wikilinks.
- Prefer small scoped runs over giant prompts.
- Prefer review-first when a batch already exists.
