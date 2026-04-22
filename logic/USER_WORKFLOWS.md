# USER_WORKFLOWS.md

## Purpose
This file is the operator guide for using the commercial LLM Wiki.

It explains:
- which prompt to use
- when to use it
- which files will be created or updated
- what to review after each run

This is a human-facing workflow guide.
It is not the same as:
- `SYSTEM_PROMPT.md`
- `AGENTS.md`
- `RULES.md`
- `SKILL.md`

---

# 1. Quick mental model

Use this system in four steps:

1. ingest source
2. create or update source note
3. normalize into wiki pages
4. review links, pricing, and customer-facing risk

---

# 2. Common workflow types

## Workflow A — Add one new source

### Use when:
- a new deck is uploaded
- a product card is uploaded
- a product sheet is uploaded
- a bilingual marketing file is uploaded

### Goal
Create one source note and update registry/log only.

### Typical outputs
- one new file in `wiki/01_sources/`
- update `wiki/01_sources/source_registry.md`
- append one short entry to `log.md`

### Prompt
```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Use only this uploaded file as the source input.

Create exactly one new Source Note under:
wiki/01_sources/

Also:
- update wiki/01_sources/source_registry.md
- append one short entry to log.md

Do not modify any other files.
Preserve source traceability.
Do not convert marketing copy into validated fact.
```

### Why use this workflow
It is the safest starting point.
Every meaningful file should first become a source note.

## Workflow B — Build or update one product page

### Use when:
- a source note already exists
- you want reusable structured product knowledge

### Goal
Create or update one normalized product page.

### Typical outputs
- one new or updated file in `wiki/02_products/`
- optional short log entry

### Prompt
```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Use the relevant source note(s) already created in wiki/01_sources/.

Create or update exactly one file:
wiki/02_products/PROD-XXXX.md

Rules:
- use bilingual structure for business knowledge
- keep English-first metadata and file naming
- separate product facts from marketing claims
- preserve source links
- mark high-risk customer-facing English with native_review_required: true

Do not modify any other files except log.md if a meaningful update is made.
```

### Why use this workflow
This is how raw product content becomes reusable knowledge.

## Workflow C — Build or update one pricing page

### Use when:
- a source contains pricing
- pricing varies by channel
- marketing materials contain platform prices
- you need a safer pricing record

### Goal
Store pricing as traceable evidence.

### Typical outputs
- one file in `wiki/06_pricing/`
- optional short log entry

### Prompt
```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Use the relevant uploaded file(s) and/or source note(s).

Create or update exactly one file:
wiki/06_pricing/PRICE-XXXX.md

Rules:
- treat pricing as evidence, not timeless truth
- keep channel, currency, source_id, and date_observed explicit
- do not merge channel prices into one official price without confirmation
- mark pricing as review_required: true
- append one short entry to log.md if updated
```

### Why use this workflow
Pricing is high-risk and should not be handled as casual product copy.

## Workflow D — Enrich links and graph readiness

### Use when:
- pages already exist
- Obsidian graph view looks empty
- product/source/pricing pages are isolated
- you want better navigation

### Goal
Improve connections without changing core facts.

### Typical outputs
- updated existing pages only
- more wikilinks
- improved frontmatter
- improved tags

### Prompt
```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Update only these existing files:
- [list exact files]

Goals:
- add wikilinks between source notes, product pages, pricing pages, and term pages
- normalize frontmatter fields
- add useful tags consistently
- preserve source traceability

Do not create new files unless explicitly listed.
Do not modify any other files.
After updating, provide a short graph-readiness summary in chat only.
```

### Why use this workflow
Obsidian graph view depends on links, not just folders.

## Workflow E — Create term registry entries

### Use when:
- one term appears repeatedly
- bilingual usage is inconsistent
- customer-facing English needs normalization
- translations vary across files

### Goal
Create reusable term pages.

### Typical outputs
- one or more files in `wiki/09_term_registry/`

### Prompt
```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Use the existing source notes and uploaded files as evidence.

Create exactly these term pages:
- wiki/09_term_registry/TERM-XXXX.md
- ...

Rules:
- canonical English term first
- preferred Chinese translation explicit
- aliases and discouraged variants separated
- distinguish literal translation from business-ready wording
- preserve source traceability
```

### Why use this workflow
Term pages stabilize bilingual consistency and improve graph connectivity.

## Workflow F — Review only

### Use when:
- you want a safe check
- you do not want files modified
- you want to inspect quality before updating

### Goal
Get review notes only.

### Prompt
```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Review only.
Do not modify files.

Check:
- traceability
- status consistency
- pricing freshness
- bilingual consistency
- missing wikilinks
- high-risk customer-facing English

Output concise review notes only.
```

### Why use this workflow
This gives a safe audit mode before making changes.

## Workflow G — Schema review only

### Use when:
- you want to check if files match schema
- you do not want changes yet
- you want safe QA

### Goal
Validate files against the relevant schema without editing them.

### Prompt
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

Check the listed files against the relevant schema(s).

For each file, report:
1. schema used
2. missing required frontmatter fields
3. invalid enum/status values
4. missing required sections
5. weak or missing source traceability
6. bilingual structure issues
7. customer-facing review flag issues
8. whether the file is:
   - schema-compliant
   - partially compliant
   - non-compliant

Output concise review notes only.
```

### Why use this workflow
This is your safe validation mode.

Use it before:
- demos
- major updates
- publishing outward-facing content
- large cleanup passes

## Workflow H — Fix to schema

### Use when:
- a file already exists
- you want it normalized to the schema
- you want targeted cleanup

### Goal
Repair or normalize existing files to match the relevant schema.

### Prompt
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

Update only these files:
- [list exact files]

Normalize them to the relevant schema(s).

Goals:
- add missing required frontmatter
- fix invalid enum/status values
- add missing required sections if clearly needed
- preserve existing meaning
- preserve source traceability
- preserve bilingual structure
- do not invent missing facts

Also:
- append one short entry to log.md if the update is meaningful

Do not modify any other files.
```

### Why use this workflow
This is your repair / normalization mode.

Use it after:
- early draft generation
- imports from messy prompts
- graph/linking runs
- manual edits that broke structure

# 3. Recommended usage order

## For a new file
Use:
- Workflow A — add source note
- Workflow B or C — build product/pricing page
- Workflow D — enrich links if needed

## For a product-focused update
Use:
- Workflow B
- Workflow E if terms need cleanup
- Workflow D for graph improvement

## For a pricing-focused update
Use:
- Workflow C
- Workflow F or Workflow G if you want a safety check
- Workflow H if cleanup is needed after validation

# 4. What to review after each run

After a run, check:

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
- is pricing marked `review_required: true`?
- are source links present?

## Link-enrichment runs
- do source notes link to product pages?
- do product pages link back to source notes?
- do product pages link to term pages?
- does graph view improve?

## Schema validation runs
- was the correct schema used?
- are required frontmatter fields present?
- are enum/status values valid?
- are required sections present?
- are review flags set correctly?

# 5. Minimal operator rules

- Do not start from product pages if no source note exists yet.
- Do not treat marketing copy as validated fact.
- Do not treat undated pricing as current truth.
- Do not publish high-risk customer-facing English without review.
- Do not ask for too many unrelated files in one run.
- Prefer small scoped runs over giant prompts.

# 6. Recommended file scopes per run

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

Reason:
Smaller runs are easier to verify and debug.

# 7. Demo workflow

If you want to show the system to someone, use this path:

- `wiki/00_overview/knowledge_map.md`
- `wiki/01_sources/source_registry.md`
- one source note: `wiki/01_sources/SRC-PG-ASTAXANTHIN-CN-CARD.md`
- one product page: `wiki/02_products/PROD-ASTAXANTHIN-PLUS.md`
- one pricing page: `wiki/06_pricing/PRICE-D3-K2-CA-MG-ZN.md`
- one term page: `wiki/09_term_registry/TERM-NPN.md`
- graph view in Obsidian

### Why this demo works
It shows:
- source evidence
- structured knowledge
- pricing control
- term normalization
- connected notes

# 8. Recommended first prompts for real use

If you do not know where to start, use these in order:

## Prompt 1
Create one source note from one uploaded file.

## Prompt 2
Create or update one product page from that source note.

## Prompt 3
Create or update one pricing page if pricing exists.

## Prompt 4
Create 3–5 term pages for repeated concepts.

## Prompt 5
Run a link-enrichment update on those pages.

That sequence is enough to build a clean vertical slice.

# 9. Prompt writing tips

## Good prompt traits
- exact file list
- exact target file list
- clear `create` vs `update`
- small scope
- explicit `do not modify any other files`

## Good wording examples
- Create exactly one new Source Note
- Update only these existing files
- Review only. Do not modify files.
- Append one short entry to `log.md`
- Use only the uploaded files in this session as source inputs

## Avoid vague wording
Avoid:
- organize everything
- fix the vault
- update all relevant files
- handle all products
- improve everything

# 10. When to require native review

Set `native_review_required: true` when:
- English is customer-facing
- claims are strong
- pricing wording is external-facing
- compliance or certification wording appears
- CN marketing language is being converted into English sales copy

# 11. Escalation moments

Stop and review manually if:
- product facts conflict
- dosage or NPN conflicts
- pricing conflicts materially
- customer-facing English feels too strong
- certification wording seems risky
- translation changes meaning

# 12. Final operator checklist

Before finishing a run, ask:
- Was a source note created first if needed?
- Are source links preserved?
- Are facts separated from claims?
- Is pricing treated as evidence?
- Are high-risk English outputs flagged?
- Was `log.md` updated if meaningful?
- Was `source_registry.md` updated if a new source note was created?
- Are key notes linked for graph readiness?
