# SKILL.md

## Purpose
This file defines the reusable operational skills used by the commercial knowledge wiki.

Skills are procedural.
They explain how agents execute work inside the rules defined in `RULES.md`.

These skills support the main maintenance path:

ingest -> compare -> update -> archive

---

## Skill: IngestSource

### Goal
Convert one raw file into structured source-level evidence without prematurely deciding final truth.

### Use When
- a new deck is uploaded
- an old product sheet is added
- a pricing card appears
- a bilingual product hand card is received
- a marketing file or inquiry sample is added

### Input
- one file from `raw/`
- existing source registry
- file metadata if available

### Output
- one Source Note
- extracted metadata
- candidate claims
- source classification
- risk markers

### Procedure
1. Identify the file:
   - file name
   - probable brand
   - probable product line
   - probable language mix
   - probable date or version signal

2. Classify the source as one or more of:
   - `brand_source`
   - `product_fact_source`
   - `product_marketing_source`
   - `material_source`
   - `pricing_source`
   - `translation_source`
   - `inquiry_source`

3. Clean and preprocess:
   - normalize broken text
   - remove obvious duplicate fragments
   - preserve original wording where evidence matters
   - extract dates, identifiers, dosage numbers, pack sizes, currency, channel names

4. Extract structured evidence:
   - product names
   - ingredients
   - dose amounts
   - suggested use / recommended use
   - NPN / certification references
   - packaging and dosage form
   - target users
   - EN/CN terminology pairs
   - price snippets
   - platform/channel references
   - claims and selling points

5. Separate extracted evidence into:
   - stable facts
   - time-sensitive facts
   - marketing phrasing
   - pricing evidence
   - translation evidence
   - open questions

6. Create or update a Source Note.

7. Mark source status:
   - `current`
   - `historical`
   - `pending_confirmation`
   - or leave unresolved if not safe to decide

### Guardrails
- do not edit raw files
- do not auto-finalize conflicting facts
- do not rewrite source evidence into polished truth here
- do not drop risky wording without preserving it as source evidence

---

## Skill: CompareClaims

### Goal
Compare newly extracted candidate claims against current wiki knowledge.

### Use When
- a Source Note has been created
- new facts need to be reconciled with existing wiki pages

### Input
- Source Note
- candidate claims
- relevant existing wiki pages
- term registry
- pricing registry if needed

### Output
- claim comparison results
- recommended statuses
- conflict markers
- review flags

### Procedure
1. Match candidate claims to existing knowledge by:
   - product identity
   - material concept
   - term entry
   - pricing context
   - marketing concept
   - channel context

2. For each claim, determine whether it is:
   - `new_claim`
   - `updated_claim`
   - `conflicting_claim`
   - `deprecated_claim`
   - `pending_confirmation`

3. Compare by category:
   - product facts
   - material facts
   - pricing
   - translation mappings
   - marketing claims
   - brand positioning

4. Apply priority logic:
   - newer may outrank older
   - authoritative may outrank informal
   - specific may outrank vague
   - safer may outrank aggressive

5. If the comparison is unsafe to finalize:
   - mark as `conflicting` or `pending_confirmation`
   - request human review

### Guardrails
- do not assume “newest” always wins
- do not merge different pricing contexts into one price
- do not convert marketing rhetoric into product fact
- do not auto-resolve high-risk conflicts

---

## Skill: UpdateWiki

### Goal
Update wiki pages using traceable, stateful, linked knowledge.

### Use When
- comparison results are available
- affected pages are known

### Input
- Source Note
- comparison output
- existing wiki pages
- term registries
- pricing registry
- inquiry patterns if needed

### Output
- updated wiki pages
- updated source maps
- updated metadata
- index/log changes
- new review flags if needed

### Procedure
1. Update Source Note first.

2. Identify affected page types:
   - product page
   - material page
   - marketing page
   - translation page
   - pricing page
   - inquiry pattern page
   - reply template
   - synthesis page

3. Update pages by claim type:
   - product facts -> product pages
   - packaging/form/material facts -> material pages or product page sections
   - pricing evidence -> pricing pages
   - EN/CN terminology -> translation pages / term registry
   - reusable messaging -> marketing pages
   - recurring inquiry patterns -> inquiry pattern pages

4. Apply state transitions:
   - stronger supported claim -> `current`
   - old replaced claim -> `historical`
   - retired claim -> `deprecated`
   - unresolved contradiction -> `conflicting`
   - unclear high-risk content -> `pending_confirmation`

5. Preserve:
   - source_ids
   - updated_at
   - review flags
   - lineage where practical

6. Update:
   - `index.md` if a major page is created
   - `log.md` for meaningful changes

### Guardrails
- do not silently delete old claims
- do not rewrite a whole page if only one section changed
- do not finalize high-risk customer-facing English without review
- do not remove traceability

---

## Skill: ArchiveState

### Goal
Preserve superseded knowledge without polluting current working knowledge.

### Use When
- claims are replaced
- pages become obsolete
- old pricing snapshots are no longer current
- terminology becomes discouraged
- historical versions remain useful for traceability

### Input
- updated pages
- superseded claims
- change history
- source references

### Output
- historical sections
- archive entries
- deprecated claim records
- preserved rollback trail

### Procedure
1. Identify knowledge that is no longer current.

2. Decide archive path:
   - keep on-page as `historical`
   - move on-page as `deprecated`
   - move to `wiki/10_archive/` if clutter is too high

3. Preserve:
   - source links
   - prior status
   - date of change
   - reason for change

4. Update `log.md` with:
   - what changed
   - why it changed
   - which page was affected

### Guardrails
- do not archive the only available evidence
- do not archive unresolved conflicts as if they were settled
- do not destroy comparison context

---

## Skill: BuildSourceNote

### Goal
Create a clean, structured Source Note from one source file.

### Use When
- a file has been ingested
- a source needs a traceable evidence page

### Input
- raw file
- extracted metadata
- extracted claim groups

### Output
- `wiki/01_sources/SRC-*.md`

### Procedure
1. Assign source id.
2. Fill metadata.
3. Summarize file role.
4. List structured facts.
5. List time-sensitive or risky claims.
6. List pricing evidence if any.
7. List translation evidence if any.
8. List open questions.
9. List recommended wiki updates.

### Guardrails
- preserve evidence flavor
- do not over-sanitize risky claims out of existence
- do not pretend the Source Note replaces the original source

---

## Skill: BuildProductPage

### Goal
Create or update a product page with structured facts, bilingual presentation, and explicit claim handling.

### Use When
- a product appears in one or more sources
- product facts need to be normalized

### Input
- source notes
- product-related candidate claims
- existing product page if any
- term registry

### Output
- `wiki/02_products/PROD-*.md`

### Procedure
1. Normalize identity:
   - title_en
   - title_zh
   - brand
   - dosage form
   - pack size
   - NPN
   - country of origin

2. Populate:
   - Summary (EN)
   - 中文说明
   - Structured Facts
   - Canonical Terms
   - Current Working Claims
   - Historical / Legacy Claims
   - Marketing Claims
   - Source Map

3. Separate clearly:
   - product facts
   - marketing claims
   - historical statements

4. If customer-facing English draft exists:
   - set `native_review_required: true` when high risk

### Guardrails
- do not flatten all claims into one summary
- do not lose distinction between claim and evidence
- do not let aggressive marketing phrasing rewrite product facts

---

## Skill: BuildPricingPage

### Goal
Create or update a pricing page using snapshot logic rather than timeless truth logic.

### Use When
- price evidence exists
- channel price differences appear
- campaign pricing needs traceable storage

### Input
- source notes
- product identity
- extracted price records

### Output
- `wiki/06_pricing/PRICE-*.md`

### Procedure
1. Normalize price evidence:
   - product
   - channel
   - currency
   - observed price
   - date_observed
   - source_id
   - confidence

2. Create sections:
   - Current Working Price Snapshot
   - Historical Price Snapshots
   - Pricing Notes
   - Rules
   - Customer-facing Guardrail
   - Source Map

3. Keep channel distinctions explicit.

4. Mark review for outward-facing use.

### Guardrails
- do not generate an “official” price without policy support
- do not use undated price as current truth
- do not merge campaign and standard prices blindly

---

## Skill: NormalizeTerms

### Goal
Create stable bilingual terminology for repeated business use.

### Use When
- recurring EN/CN terminology appears
- translation inconsistency is detected

### Input
- translation evidence
- source notes
- existing term registry

### Output
- updated term registry entries

### Procedure
1. Choose canonical English term.
2. Choose preferred Chinese translation.
3. Add aliases.
4. Add discouraged variants if needed.
5. Note context of use:
   - factual
   - regulatory
   - marketing
   - pricing
   - customer-facing

### Guardrails
- do not create parallel duplicate canonical terms
- do not promote unstable CN phrasing as preferred
- do not mix literal translation with final copy guidance

---

## Skill: LintKnowledge

### Goal
Audit consistency and traceability across the wiki.

### Use When
- after major updates
- before outward-facing template usage
- during periodic maintenance

### Input
- wiki pages
- source registry
- term registry
- pricing pages
- log history

### Output
- lint findings
- conflict report
- stale page list
- missing-source list
- native-review-needed list

### Procedure
1. Find unsupported claims.
2. Find pages missing source_ids.
3. Find stale price records.
4. Find unresolved conflicts.
5. Find inconsistent term usage.
6. Find customer-facing English without native review flag.
7. Recommend cleanup actions.

### Guardrails
- do not auto-fix high-risk content silently
- prefer flagging over destructive rewrite

---

# Schema normalization and maintenance rules

## 1. Schema normalization rules

- Normalize only the files explicitly listed in the prompt.
- Do not invent missing facts to satisfy format.
- Add missing required fields only where needed.
- Preserve existing meaning unless a change is required for schema compliance, traceability, or risk reduction.
- Preserve existing IDs, filenames, and valid wikilinks.
- Do not rewrite strong existing content unless clearly necessary.
- Use the relevant schema files under `logic/schemas/` as the structural source of truth.

## 2. Placeholder rules

When a field is required by schema but the real value is currently unknown:

- prefer enum placeholders such as `pending_confirmation` over blank strings
- prefer `[]` for missing list fields
- prefer `null` for unknown scalar fields only if the schema allows it
- do not use fake values that could be mistaken for real facts
- do not use empty strings where a structured placeholder is safer

## 3. Source traceability preservation rules

- Do not remove meaningful source links during cleanup.
- Do not convert a sourced claim into an unsourced statement.
- If content is uncertain, preserve the uncertainty explicitly.
- When restructuring a page, keep or improve source traceability.
- Source notes remain the evidence anchor for downstream product, pricing, marketing, and term pages.

## 4. Undated pricing rules

- Do not treat undated pricing as current truth.
- Pricing should be stored and described as evidence, not timeless fact.
- If pricing lacks a clear observation date, mark the uncertainty explicitly.
- Do not merge channel-specific pricing into one official price without confirmation.
- If pricing freshness is unclear, prefer review flags and pending status over certainty language.

## 5. Link-preservation rules

- Do not remove valid wikilinks unless they are clearly wrong, duplicated without purpose, or unsupported by evidence.
- When improving graph readiness, prefer meaningful links over decorative links.
- Product pages should usually link to source notes and relevant term pages.
- Pricing pages should usually link to related products and source notes.
- Source notes should usually link to affected product, pricing, and term pages where relevant.
- Term pages should be reused across multiple pages when the term is truly shared.
- Symmetric related-page links should be used only when the relationship is genuinely justified.

## 6. Review-first rules for existing batches

- If a large batch already exists, prefer review-only QA before another broad update pass.
- After a fix pass, run a smaller verification pass before declaring the batch done.
- Use final verification before demo, publication, or commit when the batch includes pricing, customer-facing English, or schema normalization.

## 7. High-risk content preservation rules

- Do not strengthen claims during cleanup.
- Do not turn marketing language into validated factual language.
- Preserve review flags such as `review_required` and `native_review_required` where needed.
- If customer-facing English remains strong or risky, retain or add review flags rather than softening risk through silence.
