name: source_note
version: 1.0
description: >
  Schema for Source Notes created from uploaded or stored source files.
  A Source Note is the first structured layer between raw evidence and wiki knowledge.

applies_to:
  - wiki/01_sources/SRC-*.md

inherits:
  - knowledge_object

required_frontmatter:
  - id
  - title_en
  - source_type
  - source_status

optional_frontmatter:
  - title_zh
  - brand
  - product_family
  - domains
  - languages
  - source_date
  - ingested_at
  - owner
  - confidence
  - review_required
  - linked_pages
  - tags

required_values:
  source_status:
    allowed_values:
      - current
      - historical
      - pending_confirmation
      - deprecated

recommended_values:
  source_type:
    typical_values:
      - brand_source
      - product_fact_source
      - product_marketing_source
      - pricing_source
      - translation_source
      - material_source
      - inquiry_source

field_rules:
  id:
    required_pattern: "^SRC-"
    description: Source Note ids should start with SRC-.

  source_type:
    type: string
    required: true
    description: Classified source type.

  source_status:
    type: enum
    required: true
    allowed_values:
      - current
      - historical
      - pending_confirmation
      - deprecated
    description: Working status of the source itself.

  brand:
    type: string
    required: false
    description: Brand associated with the source if clear.

  product_family:
    type: string
    required: false
    description: Product family associated with the source if relevant.

  domains:
    type: list[string]
    required: false
    description: Covered domains such as product, pricing, marketing, translation.

  languages:
    type: list[string]
    required: false
    description: Languages present in the source, such as [en], [zh], or [en, zh].

  ingested_at:
    type: string
    required: false
    description: Date the source was ingested into the wiki.

  linked_pages:
    type: list[string]
    required: false
    description: Linked downstream pages such as product or pricing pages.

required_sections:
  - File Identity
  - Source Summary
  - Extracted Structured Facts
  - Stable Facts
  - Time-Sensitive Facts
  - Marketing Phrasing
  - Pricing Evidence
  - Translation Evidence
  - Conflicts / Open Questions
  - Recommended Wiki Updates
  - Review

section_guidance:
  File Identity:
    description: >
      Should identify file name, path if known, source type, language mix, and probable usage.

  Source Summary:
    description: >
      Should summarize the source in English and/or Chinese without pretending the source note replaces the original.

  Extracted Structured Facts:
    description: >
      Should capture product names, ingredients, dosage, NPN references, packaging, channel mentions, and key structured evidence.

  Stable Facts:
    description: >
      Facts likely to remain valid across time unless contradicted later.

  Time-Sensitive Facts:
    description: >
      Facts that may age quickly, such as campaign language, launch framing, dates, or unstable claims.

  Marketing Phrasing:
    description: >
      Keep strong or sales-oriented phrasing here instead of turning it into validated fact automatically.

  Pricing Evidence:
    description: >
      Include pricing evidence only as source evidence, not timeless truth.

  Translation Evidence:
    description: >
      Include EN/CN term evidence and wording cues.

  Conflicts / Open Questions:
    description: >
      Flag ambiguity, missing dates, unclear regulatory wording, or conflicting facts.

  Recommended Wiki Updates:
    description: >
      Suggest downstream pages that should be created or updated.

  Review:
    description: >
      Record whether review is needed and why.

global_rules:
  - Every meaningful source file should first become a Source Note.
  - Do not rewrite the raw source in place.
  - Do not auto-promote source phrasing into validated truth.
  - Preserve risky wording as evidence when relevant.
  - Use the exact uploaded file name when no repo raw path is finalized yet.

lint_expectations:
  - source_type should be present
  - source_status should be present
  - key sections should not be missing
  - review_required should be set when needed
  - linked_pages should be added once downstream pages exist