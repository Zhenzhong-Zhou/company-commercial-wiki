# LINT.md

## Purpose
This file defines lightweight lint checks for the commercial knowledge wiki.

The goal is not strict code formatting.
The goal is:
- structure consistency
- metadata completeness
- traceability
- bilingual stability
- safer customer-facing output

---

## 1. Structure Checks

### 1.1 File Naming
Rules:
- use English-first file names
- avoid Chinese file names in `wiki/` and `logic/`
- prefer uppercase IDs only where intentional
- use stable separators such as `-` or `_`

Examples:
- `PROD-ASTAXANTHIN-PLUS.md`
- `pricing_rules.md`
- `translation_style_guide.md`

### 1.2 Folder Placement
Check that each page is in the correct folder:
- source note -> `wiki/01_sources/`
- product page -> `wiki/02_products/`
- material page -> `wiki/03_materials/`
- marketing page -> `wiki/04_marketing/`
- translation page -> `wiki/05_translation/`
- pricing page -> `wiki/06_pricing/`
- inquiry pattern -> `wiki/07_inquiry_patterns/`
- reply template -> `wiki/08_reply_templates/`

### 1.3 Required Files
Confirm these exist:
- `logic/SYSTEM_PROMPT.md`
- `logic/AGENTS.md`
- `logic/RULES.md`
- `logic/SKILL.md`
- `logic/LINT.md`
- `index.md`
- `log.md`

---

## 2. Metadata Checks

### 2.1 Required Frontmatter Fields
Important pages should include:
- `id`
- `title_en`
- `page_type`
- `status`
- `source_ids`
- `updated_at` or an intentionally blank placeholder
- `review_required`

### 2.2 Allowed Status Values
Only allow:
- `current`
- `historical`
- `conflicting`
- `pending_confirmation`
- `deprecated`

### 2.3 Page Type Consistency
Examples:
- product page -> `page_type: product`
- pricing page -> `page_type: pricing`
- translation page -> `page_type: translation`
- source note -> source-specific metadata

---

## 3. Traceability Checks

### 3.1 Source Coverage
Every important claim should have at least one source reference.

### 3.2 No Unsupported Official Claims
Flag if a page presents a claim as settled but:
- no source_ids exist
- no Source Map section exists
- no matching source note exists

### 3.3 Source Registry Linkage
New source notes should be reflected in:
- `wiki/01_sources/source_registry.md`

---

## 4. Pricing Checks

### 4.1 Required Pricing Fields
Every pricing record should try to preserve:
- product
- channel
- currency
- date_observed
- source_id
- confidence
- review_required

### 4.2 Stale Pricing
Flag if:
- undated pricing is treated as current
- campaign price is shown without context
- platform prices are merged as one “official” price without policy support

### 4.3 Customer-Facing Pricing Risk
Flag outward-facing price wording if:
- no date exists
- no source exists
- no review flag exists

---

## 5. Translation Checks

### 5.1 Canonical English Term
Each term entry should include:
- canonical English term

### 5.2 Preferred Chinese Translation
If term is used in bilingual business contexts, include:
- preferred Chinese translation

### 5.3 Variant Separation
Aliases and discouraged variants must be separated.

### 5.4 EN/ZH Section Separation
Do not allow chaotic bilingual mixing inside structured fields.

Preferred:
- `Summary (EN)`
- `中文说明`

---

## 6. Marketing and Customer-Facing Checks

### 6.1 Claim Risk
Flag strong wording such as:
- strongest
- best
- ceiling
- guaranteed
- X times better
- stricter than regulator Y
unless clearly handled as risky marketing phrasing

### 6.2 Native Review Requirement
Flag customer-facing English if high risk and:
- `native_review_required` is missing
- `native_review_required: false` seems unsafe

### 6.3 Fact vs Copy Separation
Flag if product facts and marketing slogans are mixed into one unlabeled block.

---

## 7. Update Hygiene Checks

### 7.1 Index Update
If a major new page is created, ensure it appears in `index.md`.

### 7.2 Log Update
If a major change happened, ensure `log.md` is updated.

### 7.3 Conflict Handling
Flag if contradictory evidence exists but page has no:
- `conflicting`
- `pending_confirmation`
- historical notes

---

## 8. Recommended Lint Routine

After each meaningful update:
1. check metadata
2. check source linkage
3. check pricing freshness if relevant
4. check bilingual structure
5. check customer-facing review flags
6. check index/log updates

When unsure:
- flag
- do not auto-destroy content