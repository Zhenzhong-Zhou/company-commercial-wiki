# USER_WORKFLOWS.md

## Purpose

This file is the operator guide for using the commercial LLM Wiki.

It explains:
- which workflow to use
- when to use it
- which files are usually touched
- what to review after each run
- which prompt template IDs match each workflow

This is a human-facing workflow guide.

It is not the same as:
- `SYSTEM_PROMPT.md`
- `AGENTS.md`
- `RULES.md`
- `LINT.md`
- `PROMPT_LIBRARY.md`

---

# 1. Quick mental model

Use this system in five stages:

1. ingest source
2. create or update source notes
3. normalize into wiki pages
4. strengthen traceability and links
5. run review / validation before demo, release, or commit

---

# 2. Workflow-to-prompt alignment rule

Use this naming rule consistently:

- workflow letter = operator stage
- prompt letter + number = reusable prompt template under that workflow

Examples:
- Workflow A uses Prompt A1 or A2
- Workflow D uses Prompt D1, D2, or D3
- Workflow H uses Prompt H1 or H2

This keeps the operator flow and the prompt library aligned.

---

# 3. Core workflows

## Workflow A — Add one new source

### Use when
- a new deck is uploaded
- a product card is uploaded
- a product sheet is uploaded
- a bilingual marketing file is uploaded

### Goal
Create source-note coverage first, before broader wiki normalization.

### Typical outputs
- one new file in `wiki/01_sources/`
- update `wiki/01_sources/source_registry.md`
- append one short entry to `log.md`

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt A1 — Create one source note
- Prompt A2 — Create missing source files only

### Why use this workflow
Every meaningful source should first become a source note.

---

## Workflow B — Build or update one product page

### Use when
- a relevant source note already exists
- you want reusable structured product knowledge
- a product page needs targeted normalization

### Goal
Create or update one normalized product page.

### Typical outputs
- one new or updated file in `wiki/02_products/`
- optional short log entry

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt B1 — Build or update one product page
- Prompt B2 — Product page schema fix

### Why use this workflow
This is how raw product content becomes reusable product knowledge.

---

## Workflow C — Build or update one pricing page

### Use when
- a source contains pricing
- pricing varies by channel
- marketing materials contain platform prices
- you need a safer pricing record

### Goal
Store pricing as traceable evidence, not timeless truth.

### Typical outputs
- one file in `wiki/06_pricing/`
- optional short log entry

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt C1 — Build or update one pricing page
- Prompt C2 — Pricing page schema fix
- Prompt C3 — Pricing freshness review

### Why use this workflow
Pricing is high-risk and should not be handled as casual product copy.

---

## Workflow D — Enrich links and graph readiness

### Use when
- pages already exist
- Obsidian graph view looks weak
- product/source/pricing pages are isolated
- you want better navigation and stronger hubs

### Goal
Improve connections without changing core facts.

### Typical outputs
- updated existing pages only
- more wikilinks
- stronger hub pages
- improved graph-readiness summary

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt D1 — Graph/link improvement
- Prompt D2 — Review after graph improvement
- Prompt D3 — Cross-link consistency fix

### Why use this workflow
Good graph view depends on meaningful links, not just folders.

---

## Workflow E — Create term registry entries

### Use when
- one term appears repeatedly
- bilingual usage is inconsistent
- customer-facing English needs normalization
- translations vary across files

### Goal
Create reusable term pages and normalize shared terminology.

### Typical outputs
- one or more files in `wiki/09_term_registry/`

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt E1 — Create term registry entries
- Prompt E2 — TERM-* page normalization

### Why use this workflow
Term pages stabilize bilingual consistency and improve graph connectivity.

---

## Workflow F — Review only

### Use when
- you want a safe check
- you do not want files modified
- you want to inspect quality before or after updates

### Goal
Return review findings only.

### Typical outputs
- no file changes
- concise review notes
- fix targets for the next pass

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt F1 — General review-only QA
- Prompt F2 — Small post-fix review
- Prompt F3 — Final verification pass

### Why use this workflow
This is the safest audit mode when you want judgment before action.

---

# 4. Maintenance and governance workflows

## Workflow G — Schema review only

### Use when
- files already exist
- you want to check schema compliance
- you want to stabilize a batch before more updates
- you want a safe QA pass after a large generation run

### Goal
Review a defined file batch against schema and governance rules without changing files.

### Typical outputs
- compliant file list
- files needing fixes
- exact recommended fixes
- priority cleanup list

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt G1 — Review-only schema QA

### Why use this workflow
After a large generation pass, schema QA is usually more useful than another broad update run.

---

## Workflow H — Fix to schema

### Use when
- a file already exists
- review notes identified schema or frontmatter issues
- schema files themselves need repair or completion
- you want targeted cleanup instead of broad regeneration

### Goal
Normalize only the flagged files or repair the schema layer itself.

### Typical outputs
- repaired frontmatter
- corrected enum/status values
- required sections added where clearly needed
- schema files repaired when necessary
- preserved meaning and traceability

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt H1 — Fix-only schema normalization
- Prompt H2 — Schema bootstrap/fix

### Why use this workflow
This is the safest structural repair mode after review-only QA.

---

## Workflow I — Graph/link improvement

### Use when
- the main content cluster exists
- links are present but still weak
- graph view needs clearer source/product/pricing/term connections

### Goal
Strengthen useful wikilinks and reduce isolation without inventing new facts.

### Typical outputs
- better source/product/pricing/term linking
- stronger hub pages
- fewer isolated notes
- short graph-readiness summary

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt I1 — Graph/link improvement
- Prompt I2 — Review after graph improvement

### Why use this workflow
Graph quality should be improved as a controlled pass, not as random ad hoc linking.

---

## Workflow J — Create missing files only

### Use when
- an earlier run did not create all target files
- you do not want to rerun a full generation batch
- only a few notes/pages are still missing

### Goal
Create only the missing files and avoid unnecessary rewrites.

### Typical outputs
- only the listed missing files
- optional `source_registry.md` update
- optional short `log.md` entry

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt J1 — Create missing files only

### Why use this workflow
This avoids re-touching already stable files.

---

## Workflow K — Final verification pass

### Use when
- one or more fix passes already ran
- you want a final go/no-go check before demo or commit
- you want to confirm schema, traceability, and graph quality stayed intact

### Goal
Confirm that the target batch is stable enough to stop editing and commit.

### Typical outputs
- compliant file list
- remaining blockers if any
- demo-readiness or commit-readiness assessment

### Prompt template reference
See:
- `logic/PROMPT_LIBRARY.md`
- Prompt K1 — Final verification pass

### Why use this workflow
This prevents endless editing and gives you a clean stopping point.

---

# 5. Recommended usage order

## For a new file
Use:
1. Workflow A — add source note
2. Workflow B or C — build product/pricing page
3. Workflow D or I — enrich links if needed
4. Workflow G — schema review only
5. Workflow H — fix to schema if needed
6. Workflow K — final verification pass

## For a product-focused update
Use:
1. Workflow B
2. Workflow E if terms need cleanup
3. Workflow D or I for graph improvement
4. Workflow F or G for review
5. Workflow K for final verification

## For a pricing-focused update
Use:
1. Workflow C
2. Workflow F or G for safe review
3. Workflow H if schema or freshness issues are found
4. Workflow I if graph or term links need strengthening
5. Workflow K for final verification

## For a messy existing batch
Use:
1. Workflow G — schema review only
2. Workflow H — fix only failed files
3. Workflow I — graph/link improvement
4. Workflow F — small post-fix review if needed
5. Workflow K — final verification pass

## If expected files are missing
Use:
1. Workflow J — create missing files only
2. Workflow G — schema review only
3. Workflow H — fix to schema if needed

---

# 6. What to review after each run

## Source note runs
- was the source note created?
- was `source_registry.md` updated?
- was `log.md` appended?

## Product page runs
- is frontmatter present?
- are source notes linked?
- are product facts separated from marketing claims?
- is `native_review_required` set when needed?

## Pricing page runs
- does pricing include channel and currency?
- is `date_observed` present or clearly missing?
- is pricing marked as evidence rather than timeless truth?
- are source links present?

## Graph/link runs
- do source notes link to product pages?
- do product pages link back to source notes?
- do product pages link to pricing and term pages?
- are important pages still isolated?
- are the links meaningful, not just present?

## Schema fix runs
- were missing required fields added only where needed?
- were invalid enum/status values corrected?
- were placeholders used safely?
- was existing meaning preserved?

## Final verification runs
- are the target files compliant?
- are remaining issues minor or blocking?
- is the batch ready to demo or commit?

---

# 7. Minimal operator rules

- Do not start from product pages if no source note exists yet.
- Do not treat marketing copy as validated fact.
- Do not treat undated pricing as current truth.
- Do not publish high-risk customer-facing English without review.
- Do not invent missing facts to satisfy format.
- Preserve existing IDs, filenames, and valid wikilinks.
- Prefer small scoped runs over giant prompts.
- Prefer review-first when a batch already exists.

---

# 8. Recommended file scopes per run

## Safe small run
Good:
- 1 source note
- 1 product page
- 1 pricing page
- 1 small link update

## Medium run
Good:
- 3–5 related files
- one product family
- one pricing context
- a few term pages

## Avoid
- all files at once
- all product pages at once
- all pricing pages at once
- all graph cleanup at once
- all schema cleanup at once

Reason:
Smaller runs are easier to verify and debug.

---

# 9. Demo workflow

If you want to show the system to someone, use this path:

- `README.md`
- `wiki/00_overview/knowledge_map.md`
- `wiki/01_sources/source_registry.md`
- one source note
- one product page
- one pricing page
- one term page
- graph view in Obsidian

### Why this demo works
It shows:
- source evidence
- structured knowledge
- pricing control
- term normalization
- connected notes

---

# 10. Prompt writing tips

## Good prompt traits
- exact file list
- exact target file list
- clear `create` vs `update`
- small scope
- explicit `do not modify any other files`

## Good wording examples
- Create exactly one new Source Note.
- Update only these existing files.
- Review only. Do not modify files.
- Append one short entry to `log.md`.
- Use only the uploaded files in this session as source inputs.

## Avoid vague wording
Avoid:
- organize everything
- fix the vault
- update all relevant files
- handle all products
- improve everything

---

# 11. Final operator checklist

Before finishing a run, ask:

- Was a source note created first if needed?
- Are source links preserved?
- Are facts separated from claims?
- Is pricing treated as evidence?
- Are high-risk English outputs flagged?
- Was `log.md` updated if meaningful?
- Was `source_registry.md` updated if a new source note was created?
- Are key notes linked for graph readiness?
- Should a final verification pass be run before demo or commit?
