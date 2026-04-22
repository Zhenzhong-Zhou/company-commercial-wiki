name: knowledge_object
version: 1.0
description: >
  Base schema for important knowledge objects in the commercial LLM Wiki.
  This schema defines shared metadata expectations across source notes,
  product pages, pricing pages, and other structured wiki pages.

applies_to:
  - wiki/**/*.md

required_frontmatter:
  - id
  - title_en
  - status

optional_frontmatter:
  - title_zh
  - page_type
  - domain
  - object_type
  - canonical_language
  - supported_languages
  - source_ids
  - source_type
  - source_date
  - effective_date
  - updated_at
  - confidence
  - owner
  - review_required
  - native_review_required
  - related_pages
  - aliases
  - discouraged_variants
  - tags

field_rules:
  id:
    type: string
    required: true
    description: Stable unique identifier for the page or knowledge object.

  title_en:
    type: string
    required: true
    description: Canonical English title.

  title_zh:
    type: string
    required: false
    description: Preferred Chinese title if available.

  status:
    type: enum
    required: true
    allowed_values:
      - current
      - historical
      - conflicting
      - pending_confirmation
      - deprecated
    description: Status of the knowledge object.

  page_type:
    type: string
    required: false
    description: Page category such as product, pricing, source, translation, overview.

  domain:
    type: list[string]
    required: false
    description: Domain tags such as product, pricing, translation, marketing.

  object_type:
    type: string
    required: false
    description: Optional subtype for knowledge objects.

  canonical_language:
    type: string
    required: false
    expected_values:
      - en
    description: Canonical language should normally be English.

  supported_languages:
    type: list[string]
    required: false
    description: Languages supported by the page, typically [en, zh].

  source_ids:
    type: list[string]
    required: false
    description: Linked Source Note ids supporting this knowledge object.

  source_type:
    type: string
    required: false
    description: Source type when directly relevant.

  source_date:
    type: string
    required: false
    description: Date of source material if known.

  effective_date:
    type: string
    required: false
    description: Date from which the knowledge should be treated as effective.

  updated_at:
    type: string
    required: false
    description: Last meaningful update date for the page.

  confidence:
    type: enum
    required: false
    allowed_values:
      - high
      - medium
      - low
    description: Confidence in current knowledge interpretation.

  owner:
    type: string
    required: false
    description: Logical owner or responsible team.

  review_required:
    type: boolean
    required: false
    description: Whether human review is needed.

  native_review_required:
    type: boolean
    required: false
    description: Whether high-risk customer-facing English needs native review.

  related_pages:
    type: list[string]
    required: false
    description: Related wiki pages.

  aliases:
    type: list[string]
    required: false
    description: Alternate names or variants.

  discouraged_variants:
    type: list[string]
    required: false
    description: Terms or variants that should not be preferred.

  tags:
    type: list[string]
    required: false
    description: Lightweight tags for grouping and search.

global_rules:
  - Use English-first metadata keys.
  - Use only allowed status values.
  - Preserve traceability where meaningful.
  - Prefer bilingual business content sections, but keep metadata English-first.
  - Do not silently omit source_ids for important claims.

lint_expectations:
  - important pages should usually have source_ids
  - customer-facing risky pages should usually set native_review_required
  - bilingual pages should separate EN and ZH sections clearly