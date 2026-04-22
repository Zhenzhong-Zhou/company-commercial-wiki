# PROMPT_LIBRARY.md

## Purpose

This file is the index page for reusable prompt templates used by the commercial LLM Wiki.

This file explains:
- how prompts are organized
- which prompt family to use
- where prompt bodies are stored
- which prompts are the default operator path
- which prompts are specialized, demo-only, or one-time refactor prompts

This file is not the full prompt-body warehouse.

Exact prompt bodies live under:
- `logic/prompts/core/`
- `logic/prompts/specialized/`
- `logic/prompts/demo/`
- `logic/prompts/refactor/`

For workflow-level guidance (when to use each prompt, what to review after each run), see `logic/USER_WORKFLOWS.md`.

---

# 1. Naming rule

Use this naming rule consistently:

- workflow / prompt id comes first
- a short English slug comes second
- filenames stay English-first and repository-safe

Examples:
- `B1_full_maintenance_batch.md`
- `F1_targeted_fix_pass.md`
- `K1_final_verification_pass.md`
- `D3_pricing_governance_test.md`

---

# 2. Default operator prompts

These are the main prompts most operators should use.

## B1 — Full maintenance batch
Path:
- `logic/prompts/core/B1_full_maintenance_batch.md`

Use when:
- you want one complete vertical-slice maintenance cycle
- one source cluster and directly affected downstream pages should be handled together

---

## F1 — Targeted fix pass
Path:
- `logic/prompts/core/F1_targeted_fix_pass.md`

Use when:
- a review pass already identified blockers
- only a small set of files need cleanup

---

## K1 — Final verification pass
Path:
- `logic/prompts/core/K1_final_verification_pass.md`

Use when:
- a batch or fix pass is finished
- you want a go / no-go check before demo or commit

---

# 3. Specialized maintenance prompts

Use these only when the default operator path is too broad.

## Source-only
- `logic/prompts/specialized/A1_create_one_source_note.md`
- `logic/prompts/specialized/A2_create_missing_source_files_only.md`

## Product-only
- `logic/prompts/specialized/B2_product_page_schema_fix.md`

## Pricing-only
- `logic/prompts/specialized/C1_build_or_update_one_pricing_page.md`
- `logic/prompts/specialized/C2_pricing_page_schema_fix.md`
- `logic/prompts/specialized/C3_pricing_freshness_review.md`

## Term-only
- `logic/prompts/specialized/E1_create_term_registry_entries.md`
- `logic/prompts/specialized/E2_term_page_normalization.md`

## Schema / governance
- `logic/prompts/specialized/G1_review_only_schema_qa.md`
- `logic/prompts/specialized/H1_fix_only_schema_normalization.md`
- `logic/prompts/specialized/H2_schema_bootstrap_fix.md`

## Graph / link
- `logic/prompts/specialized/I1_graph_link_improvement.md`
- `logic/prompts/specialized/I2_review_after_graph_improvement.md`

## Recovery
- `logic/prompts/specialized/J1_create_missing_files_only.md`

---

# 4. Demo and proof prompts

These prompts are for proving the wiki works.
They should not modify files.

- `logic/prompts/demo/D1_product_traceability_test.md`
- `logic/prompts/demo/D2_fact_vs_marketing_test.md`
- `logic/prompts/demo/D3_pricing_governance_test.md`
- `logic/prompts/demo/D4_term_registry_test.md`
- `logic/prompts/demo/D5_cross_page_linking_test.md`
- `logic/prompts/demo/Q1_maintenance_readiness_test.md`

---

# 5. One-time refactor prompts

Use these for structural maintenance of the prompt / workflow system itself.
They are not part of the normal maintenance loop.

- `logic/prompts/refactor/R1_rename_prompt_library_references.md`
- `logic/prompts/refactor/R2_workflow_prompt_integrity_review.md`
- `logic/prompts/refactor/R3_workflow_prompt_alignment_cleanup.md`

---

# 6. Recommended usage order

## Default path
1. B1 — full maintenance batch
2. F1 — targeted fix pass, only if needed
3. K1 — final verification pass

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

---

# 7. Minimal operator rules

- Do not start from product pages if no source note exists yet.
- Do not treat marketing copy as validated fact.
- Do not treat undated pricing as current truth.
- Do not publish high-risk customer-facing English without review.
- Do not invent missing facts.
- Preserve existing IDs, filenames, and valid wikilinks.
- Prefer small scoped runs over giant prompts.
- Prefer review-first when a batch already exists.

---

# 8. Prompt-writing rules

- use exact file lists where possible
- clearly say `create`, `update`, or `review only`
- keep scope small
- preserve source traceability
- do not invent missing facts
- do not modify files outside the listed scope
- preserve IDs, filenames, and valid wikilinks

---

# 9. Lean recommended set

## Must-have
- B1 — Full maintenance batch
- F1 — Targeted fix pass
- K1 — Final verification pass

## Strongly recommended
- D1 — Product retrieval + traceability
- D2 — Fact vs marketing copy
- D3 — Pricing governance test
- D4 — Term registry test
- D5 — Cross-page linking test
- Q1 — Maintenance-readiness test
