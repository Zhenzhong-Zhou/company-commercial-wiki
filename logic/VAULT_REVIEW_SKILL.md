# VAULT_REVIEW_SKILL.md

## Skill Name
Vault Review Skill

## Purpose
Use this skill to review an existing LLM Wiki / Obsidian vault batch and return structured quality findings without making uncontrolled changes.

This skill is for:
- schema compliance review
- source traceability review
- graph/link quality review
- pricing evidence review
- bilingual consistency review
- customer-facing risk review
- final verification before demo or commit

This skill is review-first by default.

---

## Default Mode
Review only.

Do not modify files unless the calling prompt explicitly requests an update pass.

---

## When To Use This Skill

Use this skill when:
- a batch of pages already exists
- you want QA before more edits
- you want to identify exact files needing fixes
- you want to check graph/link improvement
- you want to validate schema normalization
- you want a final go/no-go review before demo or commit

---

## Inputs

This skill expects:
- an exact file list
- the relevant schema files under `logic/schemas/`
- the core governance files:
    - `logic/SYSTEM_PROMPT.md`
    - `logic/AGENTS.md`
    - `logic/RULES.md`
    - `logic/SKILL.md`
    - `logic/LINT.md`

Optional inputs:
- uploaded source files
- a target review mode
- a prior review result
- a previous fix batch

---

## Review Modes

### 1. Batch QA Mode
Use when you want one structured review over a defined batch.

Checks:
- missing required frontmatter
- schema mismatches
- invalid enum/status values
- missing required sections
- missing source links
- weak or missing wikilinks
- missing tags
- graph-readiness gaps
- customer-facing risk flags
- pricing freshness / evidence issues

### 2. Schema Review Mode
Use when the main concern is compliance with `logic/schemas/*.yaml`.

Checks:
- required fields
- allowed page_type
- allowed enum values
- placeholder correctness
- schema/frontmatter alignment

### 3. Graph Review Mode
Use when the main concern is Obsidian graph quality.

Checks:
- whether source notes link to downstream pages
- whether product pages link to sources and terms
- whether pricing pages link to products and sources
- whether important pages remain isolated
- whether links are meaningful, not decorative
- whether backlinks/outgoing-link quality is weak

### 4. Pricing Review Mode
Use when pricing pages or pricing language are involved.

Checks:
- pricing treated as evidence, not timeless truth
- channel explicit where relevant
- currency explicit where relevant
- source traceability preserved
- undated pricing clearly non-current or pending confirmation
- review flags present where needed

### 5. Final Verification Mode
Use when one or more fix passes already ran.

Checks:
- earlier flagged issues resolved
- no new schema mismatches introduced
- traceability preserved
- valid wikilinks preserved
- batch is ready for demo or commit

---

## Operating Rules

### 1. Truthfulness and preservation
- Do not invent missing facts.
- Do not strengthen claims during cleanup.
- Do not convert marketing copy into validated fact.
- Do not treat undated pricing as current truth.

### 2. Structure preservation
- Preserve existing IDs, filenames, and valid wikilinks.
- Preserve meaningful source traceability.
- Preserve bilingual structure where present.
- Do not recommend broad rewrites when a targeted fix is enough.

### 3. Scope control
- Review only the explicitly listed files.
- Do not infer unrelated file changes.
- Prefer exact fix targets over vague advice.

### 4. Placeholder rules
When a field is required but the real value is unknown:
- prefer enum placeholders such as `pending_confirmation`
- prefer `[]` for missing list fields
- prefer `null` for unknown scalar fields only if schema allows it
- avoid blank strings unless explicitly allowed

---

## Output Format

Return:

1. compliant files
2. files needing fixes
3. exact fixes recommended
4. highest-priority cleanup actions
5. whether the batch is demo-ready / commit-ready

For smaller targeted reviews, return:

1. strong links confirmed
2. weak links still remaining
3. exact next link improvements

For final verification, return:

1. compliant files
2. files still needing fixes
3. exact remaining fixes
4. whether this batch is ready to commit

---

## Severity Guidance

### High priority
- schema mismatch blocking consistency
- broken or missing source traceability
- undated pricing presented as current
- risky customer-facing English without review flag
- important hub pages still isolated

### Medium priority
- weak wikilinks
- missing tags
- asymmetric related-page links
- inconsistent placeholder usage

### Low priority
- cosmetic formatting cleanup
- optional graph enrichment
- minor wording normalization that does not affect meaning

---

## Recommended Review Procedure

### Step 1
Confirm the exact file list.

### Step 2
Identify the primary mode:
- batch QA
- schema review
- graph review
- pricing review
- final verification

### Step 3
Review only the listed files against:
- schema
- traceability
- links
- pricing evidence quality
- bilingual consistency
- review flags

### Step 4
Separate:
- compliant files
- files needing fixes

### Step 5
Recommend only the smallest useful next pass.

---

## What This Skill Should Not Do

- do not rewrite the whole vault by default
- do not modify files unless explicitly requested
- do not recommend giant all-vault cleanup passes when smaller passes are safer
- do not replace source evidence with inferred facts
- do not remove valid links without reason

---

## Recommended Companion Files

This skill works best together with:
- `logic/USER_WORKFLOWS.md`
- `logic/PROMPT_LIBRARY.md`
- `logic/RULES.md`
- `logic/LINT.md`
- `logic/schemas/*.yaml`

---

## Practical Use

Use this skill as the nightly or pre-commit review layer for the vault.

Typical result:
- precise QA
- safer cleanup planning
- better graph improvement decisions
- clearer stop/commit points
- 
