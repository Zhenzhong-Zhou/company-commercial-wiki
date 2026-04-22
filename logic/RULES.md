# RULES.md

## Purpose
This file defines the operating rules for maintaining the company commercial knowledge base.

These rules apply to:
- all agents
- all wiki pages
- all source notes
- all update workflows
- all customer-facing and internal knowledge outputs

This file is policy-oriented.
It defines boundaries, review triggers, and decision rules.

---

## 1. Repository Rules

### 1.1 Layer Separation
The repository must remain split into three layers:

1. `raw/`
   - immutable source files
   - original evidence only

2. `wiki/`
   - structured knowledge pages
   - source notes
   - product pages
   - pricing pages
   - term registry
   - inquiry patterns
   - templates and syntheses

3. `logic/`
   - agent definitions
   - skills
   - rules
   - schemas
   - templates
   - workflows

### 1.2 Raw File Integrity
Rules:
- raw files must never be overwritten during routine maintenance
- raw files must never be “corrected” in place by agents
- if a source is outdated, mark it as legacy in the Source Note, not by editing the original file
- if a better version appears, keep both and manage via status + linkage

---

## 2. Knowledge Status Rules

### 2.1 Allowed Status Values
Every important Knowledge Object or page-level claim should use one of the following statuses:

- `current`
- `historical`
- `conflicting`
- `pending_confirmation`
- `deprecated`

### 2.2 Status Meaning
- `current`
  - currently preferred working knowledge based on strongest available support

- `historical`
  - old but still useful for traceability, history, or comparison

- `conflicting`
  - contradicts another supported claim and cannot be auto-resolved safely

- `pending_confirmation`
  - incomplete, ambiguous, or risky enough to require human validation

- `deprecated`
  - retired from current use and no longer recommended as working knowledge

### 2.3 State Transition Rule
Agents must prefer:
- explicit status transition
over
- silent text overwrite

---

## 3. Traceability Rules

### 3.1 Source Link Rule
Every important business claim must trace back to at least one Source Note.

Important claim categories include:
- product identity
- ingredients
- dosage
- NPN or regulatory identifiers
- pack size
- recommended use / suggested use
- pricing
- channel pricing
- certification references
- key marketing claims
- bilingual terminology mappings

### 3.2 No Orphan Rule
Pages must not contain unsupported “official” conclusions without source linkage.

### 3.3 Source First Rule
Before spreading facts into the wiki:
1. create or update a Source Note
2. classify the source
3. extract structured facts
4. then update downstream pages

---

## 4. Freshness and Priority Rules

### 4.1 New Is Not Automatically True
Newer material is not automatically more correct.
Agents must consider:
- source date
- source authority
- source type
- domain risk
- evidence specificity

### 4.2 Working Priority Heuristic
When two claims differ, prefer the claim that is more likely:
1. newer
2. more authoritative
3. more explicit
4. more product-specific
5. more compliance-safe
6. more directly supported

### 4.3 Conflict Rule
If the priority cannot be safely determined:
- mark the claim as `conflicting` or `pending_confirmation`
- do not auto-finalize

---

## 5. Product Rules

### 5.1 Structured Product Facts
The following are structured product facts and should be stored carefully:
- product name
- brand
- dosage form
- ingredients
- dose amount
- suggested use
- recommended use
- NPN
- pack size
- country of origin

### 5.2 Product Conflict Rule
If any of the following conflict across sources, trigger review:
- ingredient composition
- ingredient amount
- recommended use
- dosage instructions
- NPN
- pack size
- target population if materially different

### 5.3 Product Fact vs Marketing Copy
Do not confuse:
- product fact
with
- marketing slogan

Examples:
- “Contains 100mg ubiquinol” = product fact
- “Gives your heart an energy shield” = marketing phrasing

---

## 6. Material Rules

### 6.1 Material Scope
Material knowledge may include:
- dosage form
- softgel / tablet / capsule distinctions
- delivery base
- packaging form
- light-protective packaging
- chelated mineral form
- manufacturing form references

### 6.2 Material Rule
Material details may be stored as:
- product-specific facts
or
- reusable material pages

### 6.3 Avoid Over-Interpretation
Do not infer manufacturing or material properties beyond source support.

---

## 7. Marketing Rules

### 7.1 Marketing Claim Categories
Marketing content should be separated into:
- brand positioning
- selling points
- claims
- social proof
- endorsements
- event references
- platform/channel messaging

### 7.2 Approved vs Unverified
Marketing language must be split into:
- `current_working_marketing`
- `historical_marketing`
- `unverified_marketing_claim`
- `customer_facing_high_risk`

### 7.3 No Auto-Promotion Rule
Do not convert strong marketing language into validated product fact automatically.

### 7.4 Superiority / Extreme Wording Rule
The following classes must be review-sensitive:
- “best”
- “strongest”
- “ceiling”
- “X times stronger”
- “far stricter than”
- “guaranteed”
- “works for everyone”
- “industry-leading” when evidence is unclear

---

## 8. Translation Rules

### 8.1 Canonical Language Rule
Use English as canonical for:
- file names
- folder names
- metadata keys
- enum values
- schemas
- system labels
- technical terminology

### 8.2 Bilingual Knowledge Rule
Use bilingual structure for business knowledge where helpful:
- canonical English term
- preferred Chinese translation
- aliases
- discouraged variants

### 8.3 Translation Separation Rule
Distinguish clearly between:
- literal translation
- internal interpretation
- business rewrite
- customer-facing English draft

### 8.4 Terminology Registry Rule
Every important recurring term should be stored in a term registry before being reused broadly.

### 8.5 Discouraged Translation Rule
If a translation is misleading, exaggerated, or unstable:
- store it as an alias or discouraged variant
- do not use it as the preferred term

---

## 9. Pricing Rules

### 9.1 Pricing Is High Risk
All pricing content is high-risk by default.

### 9.2 Price Snapshot Rule
Every price record should include:
- product
- channel
- currency
- date_observed
- source_id
- confidence
- review_required

### 9.3 No Timeless Price Rule
Do not treat price found in a deck, product card, or campaign material as timeless truth.

### 9.4 External Use Rule
Any outward-facing price statement should be validated freshly when possible.

### 9.5 Platform Rule
Do not collapse:
- Amazon price
- livestream price
- retail price
- campaign price
into one “official price” unless confirmed by policy.

---

## 10. Customer-Facing English Rules

### 10.1 English Output Rule
Customer-facing output defaults to English.

### 10.2 Native Review Rule
Set `native_review_required: true` for high-risk English content, including:
- marketing copy
- product claims
- sales-facing product intros
- claim-heavy email templates
- compliance-sensitive language
- pricing-related external wording

### 10.3 CN-to-EN Rewrite Rule
Do not directly convert aggressive CN sales language into final EN customer copy without review.

---

## 11. Human Review Boundary

### 11.1 Mandatory Human Review Cases
Trigger human review when:
1. pricing changes or outward-facing pricing language appears
2. NPN or certification references conflict
3. product ingredients or dosage conflict
4. claim wording becomes stronger than source evidence
5. customer-facing English is high-risk
6. core brand positioning changes materially
7. major bilingual term ambiguity affects external meaning
8. logic or workflow changes alter system behavior

### 11.2 Optional Human Review Cases
Optional review may be used for:
- internal summaries
- source notes
- low-risk internal bilingual explanations
- non-promotional internal rewrite drafts

---

## 12. Update and Archive Rules

### 12.1 Update Rule
Updates must be represented as:
- new evidence
- state change
- linked page updates

### 12.2 Archive Rule
When a claim is superseded:
- preserve it as `historical` or `deprecated`
- do not erase traceability

### 12.3 Log Rule
Meaningful changes must be recorded in `log.md`.

### 12.4 Index Rule
Important newly created pages should be reflected in `index.md`.

---

## 13. Page Minimum Metadata Rules

Important wiki pages should preserve at least:
- `id`
- `title_en`
- `title_zh` if available
- `page_type`
- `status`
- `source_ids`
- `updated_at`
- `review_required`

---

## 14. Governance Rules

### 14.1 Governance Checks
The system should regularly check for:
- orphan claims
- missing source_ids
- stale pricing
- unresolved conflicts
- inconsistent terms
- customer-facing English without native review flags
- unsupported “official” conclusions

### 14.2 Recursive Cleanup Rule
The system may suggest:
- page merge
- archive
- registry normalization
- duplicate claim cleanup

But must not destroy traceability.

---

## 15. Practical Decision Rule
When unsure:
- preserve
- annotate
- downgrade confidence
- request review

Never guess silently.