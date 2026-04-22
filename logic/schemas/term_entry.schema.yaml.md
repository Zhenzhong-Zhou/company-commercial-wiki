name: term_entry
version: 1.0
description: >
  Schema for term registry entries in the commercial LLM Wiki.
  Term pages normalize recurring bilingual terminology and help keep
  product, pricing, translation, and marketing language consistent.

applies_to:
  - wiki/09_term_registry/TERM-*.md

inherits:
  - knowledge_object

required_frontmatter:
  - id
  - title_en
  - page_type
  - status
  - canonical_language

required_values:
  page_type:
    allowed_values:
      - translation

  canonical_language:
    allowed_values:
      - en

optional_frontmatter:
  - title_zh
  - supported_languages
  - updated_at
  - review_required
  - native_review_required
  - source_ids
  - related_pages
  - tags

field_rules:
  id:
    required_pattern: "^TERM-"
    description: Term entry ids should start with TERM-.

  page_type:
    type: enum
    required: true
    allowed_values:
      - translation

  canonical_language:
    type: enum
    required: true
    allowed_values:
      - en
    description: Canonical term language should be English.

  title_en:
    type: string
    required: true
    description: Canonical English term label.

  title_zh:
    type: string
    required: false
    description: Preferred Chinese translation if applicable.

  source_ids:
    type: list[string]
    required: false
    description: Supporting source note ids or page references for the term.

  related_pages:
    type: list[string]
    required: false
    description: Pages where this term is important or frequently used.

required_sections:
  - Canonical English Term
  - Preferred Chinese Translation
  - Aliases
  - Discouraged Variants
  - Domain
  - Definition (EN)
  - 中文解释
  - Usage Context
  - Approved Usage Examples
  - Discouraged Usage Examples
  - Notes
  - Source Map

section_guidance:
  Canonical English Term:
    description: >
      The single preferred English term used as the canonical registry key.

  Preferred Chinese Translation:
    description: >
      The preferred Chinese rendering for consistent internal and external use where appropriate.

  Aliases:
    description: >
      Accepted alternate phrasings or synonymous terms that may appear in source materials.

  Discouraged Variants:
    description: >
      Variants that are misleading, unstable, too sales-driven, or otherwise not preferred.

  Domain:
    description: >
      Which business domains the term belongs to, such as product, pricing, marketing, translation, inquiry, or compliance.

  Definition (EN):
    description: >
      A concise English definition of the term.

  中文解释:
    description: >
      A concise Chinese explanation of the term.

  Usage Context:
    description: >
      Where and how the term should be used, for example internal, customer-facing, pricing, marketing, or product facts.

  Approved Usage Examples:
    description: >
      Safe example usage in English and/or Chinese.

  Discouraged Usage Examples:
    description: >
      Unsafe, misleading, or non-preferred examples in English and/or Chinese.

  Notes:
    description: >
      Optional notes about literal translation, business rewrite, ambiguity, or risk.

  Source Map:
    description: >
      Source notes or supporting pages connected to this term.

global_rules:
  - Every important repeated business term should map to one canonical English term entry.
  - Chinese translations should reference the canonical English term, not create parallel independent concepts.
  - Aliases and discouraged variants must be explicitly separated.
  - Literal translation and business-ready rewrite should not be confused.
  - High-risk customer-facing wording may require native review.

lint_expectations:
  - page_type should be translation
  - canonical_language should be en
  - canonical English term should exist
  - preferred Chinese translation should exist when the term is used bilingually
  - aliases and discouraged variants should be separated
  - Source Map should exist when supporting evidence is available