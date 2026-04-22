# PROMPT_LIBRARY.md

## Purpose

This prompt library stores reusable maintenance prompt templates for the commercial LLM Wiki.

These prompts are for:
- source-note creation and recovery
- product and pricing page maintenance
- term page maintenance
- schema QA and normalization
- graph/link improvement
- post-fix verification
- final commit/demo verification

This file stores exact reusable prompt bodies.

It is not:
- the main workflow guide
- the schema definitions
- the lint policy itself

---

# 1. Prompt alignment rule

Use this naming rule consistently:

- workflow letter = operator stage
- prompt letter + number = reusable prompt template under that workflow

Examples:
- Workflow A uses Prompt A1 or A2
- Workflow H uses Prompt H1 or H2
- Workflow K uses Prompt K1

---

# 2. Workflow A prompts

## Prompt A1 — Create one source note

Use when:
- one meaningful uploaded source needs to become a source note first

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

## Prompt A2 — Create missing source files only

Use when:
- an earlier run did not create all intended source notes
- you want recovery without rerunning the whole batch

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Use only these uploaded files in the current session as source inputs.
Do not assume any repo raw/ path that has not been explicitly created yet.
When referencing sources, use the exact uploaded file names.

Create only these missing files:
- [list only the missing files]

Also:
- update wiki/01_sources/source_registry.md if a new source note is created
- append one short entry to log.md if meaningful

Do not modify any other files.
```

---

# 3. Workflow B prompts

## Prompt B1 — Build or update one product page

Use when:
- a source note already exists
- you want one reusable product page created or updated

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/product_page.schema.yaml
- logic/schemas/common_enums.schema.yaml

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

## Prompt B2 — Product page schema fix

Use when:
- a product page already exists
- review notes identified schema, frontmatter, or traceability issues

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/product_page.schema.yaml
- logic/schemas/common_enums.schema.yaml

Update only these files:
- [exact product page file list]
- log.md

Goals:
- normalize the listed product page(s) to schema
- add missing required frontmatter only where needed
- fix invalid enum/status values
- add missing required sections if clearly needed
- preserve source traceability
- preserve existing meaning
- do not invent missing facts

Do not modify any other files.
```

---

# 4. Workflow C prompts

## Prompt C1 — Build or update one pricing page

Use when:
- a source contains pricing
- you want one pricing page created or updated

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
wiki/06_pricing/PRICE-XXXX.md

Rules:
- treat pricing as evidence, not timeless truth
- keep channel, currency, source_id, and date_observed explicit
- do not merge channel prices into one official price without confirmation
- mark pricing as review_required: true
- append one short entry to log.md if updated
```

## Prompt C2 — Pricing page schema fix

Use when:
- a pricing page exists
- frontmatter, section structure, or review flags need normalization

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

Update only these files:
- [exact pricing page file list]
- log.md

Goals:
- normalize the listed pricing page(s) to schema
- add missing required frontmatter only where needed
- improve source traceability
- preserve existing meaning
- do not invent missing facts
- do not promote undated pricing to current truth

Do not modify any other files.
```

## Prompt C3 — Pricing freshness review

Use when:
- you want to check whether pricing language is too current-seeming
- a pricing page may have undated evidence

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

---

# 5. Workflow D prompts

## Prompt D1 — Graph/link improvement

Use when:
- the content cluster already exists
- links need strengthening
- the graph still has weak connectivity

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

Update only these existing files:
- [exact file list]

Goals:
- strengthen wikilinks between source notes, product pages, pricing pages, and term pages
- reduce isolated pages
- improve source traceability
- keep schema/frontmatter consistency intact
- preserve existing meaning
- do not invent facts
- do not modify any other files beyond the listed files

Also provide in chat only:
- which pages are now well linked
- which pages are still isolated
- next 3 pages that would improve graph view most
```

## Prompt D2 — Review after graph improvement

Use when:
- a graph/link improvement pass has just completed
- you want to verify whether links became meaningful, not just present

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

Review only these files:
- [same file list you just updated]

Check:
- whether wikilinks meaningfully improved
- whether source traceability improved
- whether each file now links to the right related page types
- whether any important pages are still isolated
- whether backlinks/outgoing-link quality is still weak
- whether schema compliance was preserved

Output:
1. files now well-linked
2. files still weakly linked or isolated
3. exact remaining link gaps
4. top 3 next pages to update for graph improvement
5. whether the batch is now graph-ready enough for demo
```

## Prompt D3 — Cross-link consistency fix

Use when:
- two related pages link asymmetrically
- you want to decide whether the relationship should be kept symmetrically or removed

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/product_page.schema.yaml
- logic/schemas/common_enums.schema.yaml

Update only these files:
- [exact file list]
- log.md

Goals:
- resolve cross-page linking asymmetry
- use shared source evidence only if the relationship is justified
- keep the relationship symmetric if it is kept
- remove the weaker side if the relationship is not justified
- append one short entry to log.md if meaningful

Rules:
- Do not modify any other files
- Do not invent relationships
- Preserve source traceability
- If shared evidence materially supports a related-pages link, make both pages consistent
- If the relationship is too weak, remove the asymmetrical link instead of forcing it
```

---

# 6. Workflow E prompts

## Prompt E1 — Create term registry entries

Use when:
- one or more repeated terms need reusable term pages

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/term_entry.schema.yaml
- logic/schemas/common_enums.schema.yaml

Use the existing source notes and uploaded files as evidence.

Create exactly these term pages:
- [exact TERM-* file list]

Rules:
- canonical English term first
- preferred Chinese translation explicit
- aliases and discouraged variants separated
- distinguish literal translation from business-ready wording
- preserve source traceability
```

## Prompt E2 — TERM-* page normalization

Use when:
- term pages exist
- schema says the current `page_type` or related frontmatter is inconsistent

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/term_entry.schema.yaml
- logic/schemas/common_enums.schema.yaml

Update only these files:
- [exact TERM-* file list]
- log.md

Goals:
- normalize these TERM-* pages to the relevant schema
- resolve the page_type rule consistently across all listed TERM-* pages
- fix related frontmatter/status/review flag inconsistencies only where needed
- preserve existing meaning, bilingual structure, and source traceability
- append one short entry to log.md if meaningful

Rules:
- Do not modify any other files
- Do not invent missing facts
- Preserve existing IDs, filenames, and valid wikilinks
- If the schema clearly requires one page_type value, apply it consistently across the listed term pages
```

---

# 7. Workflow F prompts

## Prompt F1 — General review-only QA

Use when:
- you want one structured review over a defined batch
- you do not want any files modified

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

Review these files only:
- [exact file list]

Check:
- missing required frontmatter
- schema mismatches
- missing source links
- weak or missing wikilinks
- missing tags
- high-risk customer-facing English without native_review_required
- pricing freshness / pricing evidence issues
- graph-readiness gaps

Output:
1. compliant files
2. files needing fixes
3. exact fixes recommended
4. top 5 highest-priority cleanup actions
```

## Prompt F2 — Small post-fix review

Use when:
- only a few files changed
- you want a quick “did the fix work?” check

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/pricing_page.schema.yaml
- logic/schemas/term_entry.schema.yaml
- logic/schemas/common_enums.schema.yaml

Review only.
Do not modify files.

Review these files only:
- [exact file list]

Check:
- remaining schema mismatches
- remaining invalid statuses / review flags
- whether undated pricing is clearly non-current
- whether source traceability is still preserved
- whether the files are now compliant

Output:
1. compliant files
2. files still needing fixes
3. exact remaining fixes if any
```

## Prompt F3 — Final verification pass

Use when:
- one or more repair passes already ran
- you want a final commit-readiness check

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/product_page.schema.yaml
- logic/schemas/term_entry.schema.yaml
- logic/schemas/common_enums.schema.yaml

Review only.
Do not modify files.

Review only these files:
- [exact file list]

Check:
- schema files now exist and are usable
- page_type values are now consistent with schema
- no remaining frontmatter/status mismatches in the listed files
- source traceability is preserved
- graph/link decisions are now consistent
- the batch is ready to commit or still blocked

Output:
1. compliant files
2. files still needing fixes
3. exact remaining fixes
4. whether this batch is ready to commit
```

---

# 8. Workflow G prompts

## Prompt G1 — Review-only schema QA

Use when:
- files already exist
- you want schema-focused QA without modifying anything
- you want exact schema fix targets

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

Check only these files:
- [exact file list]

For each file, report:
1. schema used
2. missing required frontmatter fields
3. invalid enum/status values
4. missing required sections
5. weak or missing source traceability
6. bilingual structure issues
7. customer-facing review flag issues
8. whether the file is schema-compliant, partially compliant, or non-compliant

Also report:
- which pages are now linked
- which pages are still isolated
- the next 3 pages that would improve graph view most

Output concise review notes only.
```

---

# 9. Workflow H prompts

## Prompt H1 — Fix-only schema normalization

Use when:
- a review pass already identified problem files
- you want targeted cleanup only

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
- [paste only the files that need fixing from the review]

Goals:
- normalize to the relevant schema(s)
- add missing required frontmatter only where needed
- add missing required sections if clearly needed
- improve wikilinks between source, product, pricing, and term pages
- improve source traceability
- add useful tags consistently
- preserve existing meaning
- preserve existing IDs, filenames, and valid wikilinks
- do not invent missing facts
- do not rewrite strong existing content unless needed for compliance, traceability, or link improvement

Also:
- append one short entry to log.md if meaningful

Do not modify any other files.
```

## Prompt H2 — Schema bootstrap/fix

Use when:
- schema files are missing
- schema files are empty
- enum consistency across schema files is broken

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Update only these files:
1. logic/schemas/knowledge_object.schema.yaml
2. logic/schemas/source_note.schema.yaml
3. logic/schemas/product_page.schema.yaml
4. logic/schemas/pricing_page.schema.yaml
5. logic/schemas/term_entry.schema.yaml
6. logic/schemas/common_enums.schema.yaml
7. log.md

Goals:
- ensure each listed schema file exists at the exact path
- ensure each schema file is non-empty and usable
- ensure enum/status definitions are consistent across the schema set
- preserve existing schema intent where already valid
- do not invent business facts; this is schema/governance work only
- append one short entry to log.md if meaningful

Rules:
- Do not modify any other files
- Keep file names and paths exactly as listed
- If a schema already exists and is valid, only normalize minimally
- Prefer consistency over expansion
```

---

# 10. Workflow I prompts

## Prompt I1 — Graph/link improvement

Use when:
- the main content cluster exists
- graph improvement is the primary goal for this pass

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

Update only these existing files:
- [exact file list]

Goals:
- strengthen wikilinks between source notes, product pages, pricing pages, and term pages
- reduce isolated pages
- preserve source traceability
- preserve existing meaning
- do not invent facts
- do not modify any other files

Also provide in chat only:
- which pages are now well linked
- which pages are still isolated
- next 3 pages that would improve graph view most
```

## Prompt I2 — Review after graph improvement

Use when:
- you want a graph-focused verification pass after I1

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

Review only these files:
- [same file list you just updated]

Check:
- whether links are meaningful, not just present
- whether the term pages now have useful backlinks
- whether product pages connect source + pricing + term pages
- whether any of these pages are still weakly connected

Output:
1. strong links confirmed
2. weak links still remaining
3. exact next link improvements
```

---

# 11. Workflow J prompts

## Prompt J1 — Create missing files only

Use when:
- some of the expected files were not actually created
- you want recovery without rerunning a whole batch

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Use only these uploaded files in the current session as source inputs.
Do not assume any repo raw/ path that has not been explicitly created yet.
When referencing sources, use the exact uploaded file names.

Create only these missing files:
- [list only the missing files]

Also:
- update wiki/01_sources/source_registry.md if a new source note is created
- append one short entry to log.md

Do not modify any other files.
```

---

# 12. Workflow K prompts

## Prompt K1 — Final verification pass

Use when:
- one or more fix passes already ran
- you want a final go/no-go check before demo or commit

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

Review only these files:
- [exact file list]

Check:
- whether wikilinks meaningfully improved
- whether source traceability improved
- whether schema compliance was preserved
- whether tags/frontmatter remain consistent
- whether any important pages are still isolated or weakly connected
- whether the batch is demo-ready or commit-ready

Output:
1. compliant / well-linked files
2. files still needing fixes
3. exact remaining fixes
4. whether this batch is demo-ready / commit-ready
```

---

# 13. One-time refactor prompts

## Prompt R1 — Rename prompt library references

Use when:
- `logic/MAINTENANCE_PROMPTS.md` was renamed to `logic/PROMPT_LIBRARY.md`
- you need to update remaining internal references
- you want wording and file references to stay consistent after the rename

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Update only these files:
- logic/USER_WORKFLOWS.md
- logic/PROMPT_LIBRARY.md
- README.md
- docs/PROJECT_SETUP_README.md
- docs/VAULT_HEALTH_CHECK_PROMPT.md
- logic/VAULT_REVIEW_SKILL.md

Goals:
- rename all intended references from `logic/MAINTENANCE_PROMPTS.md` to `logic/PROMPT_LIBRARY.md`
- update wording so “prompt library” is used consistently where appropriate
- update the title/header inside `logic/PROMPT_LIBRARY.md` so it no longer says `MAINTENANCE_PROMPTS.md`
- preserve all workflow-to-prompt references
- do not change the meaning of workflows, rules, or setup instructions
- do not modify any other files

Rules:
- Do not invent new workflows or prompts
- Preserve existing IDs, filenames, and valid wikilinks except for the intended file rename
- Keep wording concise and structurally consistent
```

verify no old references remain

```bash
rg -n "MAINTENANCE_PROMPTS\.md|# MAINTENANCE_PROMPTS\.md|maintenance prompts" .

```

Same format you can keep for future one-time refactor prompts

 ```text
 
 Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Update only these files:
- [exact file list]

Goals:
- [exact rename / refactor goal]
- [wording consistency goal]
- [header/title update goal if needed]
- preserve all valid references
- do not change meaning
- do not modify any other files

Rules:
- Do not invent new workflows or prompts
- Preserve existing IDs, filenames, and valid wikilinks except for the intended rename/refactor
- Keep wording concise and structurally consistent
   ```