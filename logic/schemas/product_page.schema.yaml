name: product_page
version: 1.0
description: >
  Schema for normalized product pages in the commercial LLM Wiki.
  Product pages should separate structured product facts from marketing claims
  and preserve source traceability.

applies_to:
  - wiki/02_products/PROD-*.md

inherits:
  - knowledge_object

required_frontmatter:
  - id
  - title_en
  - page_type
  - status
  - source_ids

required_values:
  page_type:
    allowed_values:
      - product

optional_frontmatter:
  - title_zh
  - brand
  - canonical_language
  - supported_languages
  - updated_at
  - review_required
  - native_review_required
  - related_pages
  - tags

field_rules:
  id:
    required_pattern: "^PROD-"
    description: Product page ids should start with PROD-.

  page_type:
    type: enum
    required: true
    allowed_values:
      - product

  brand:
    type: string
    required: false
    description: Brand associated with the product.

  source_ids:
    type: list[string]
    required: true
    description: Source Note ids supporting the product page.

  native_review_required:
    type: boolean
    required: false
    description: Should be true when customer-facing English is high-risk.

required_sections:
  - Product Identity
  - Summary (EN)
  - 中文说明
  - Structured Facts
  - Canonical Terms
  - Current Working Claims
  - Historical / Legacy Claims
  - Marketing Claims (Not Auto-Validated)
  - Customer-Facing English Draft
  - Internal Notes (ZH)
  - Open Questions
  - Source Map

section_guidance:
  Product Identity:
    description: >
      Should include brand, product line, dosage form, pack size, NPN, and country of origin if known.

  Summary (EN):
    description: >
      Clear English summary of the product as currently understood.

  中文说明:
    description: >
      Internal Chinese support explanation or bilingual business context.

  Structured Facts:
    description: >
      Should include ingredients, suggested use, recommended use, target users, packaging/form.

  Canonical Terms:
    description: >
      English canonical term, preferred Chinese translation, aliases, discouraged variants where relevant.

  Current Working Claims:
    description: >
      Current working claims supported strongly enough for internal use.

  Historical / Legacy Claims:
    description: >
      Old or superseded claims preserved for traceability.

  Marketing Claims (Not Auto-Validated):
    description: >
      Strong promotional claims should remain clearly separated from validated facts.

  Customer-Facing English Draft:
    description: >
      Only draft-level outward-facing English. High-risk content should set native_review_required: true.

  Internal Notes (ZH):
    description: >
      Internal Chinese interpretation, caution, or usage notes.

  Open Questions:
    description: >
      Unresolved issues, conflicts, review needs, or missing evidence.

  Source Map:
    description: >
      Must point back to source notes.

global_rules:
  - Separate fact from claim.
  - Preserve bilingual structure where useful.
  - Do not treat strong marketing phrases as validated facts.
  - Preserve source traceability.
  - Use explicit historical or conflicting sections when needed.

lint_expectations:
  - source_ids must not be empty
  - Source Map should exist
  - product facts and marketing claims should not be merged into one unlabeled block
  - high-risk customer-facing English should set native_review_required: true