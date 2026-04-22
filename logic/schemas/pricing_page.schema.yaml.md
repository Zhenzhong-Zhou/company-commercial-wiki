name: pricing_page
version: 1.0
description: >
  Schema for pricing pages in the commercial LLM Wiki.
  Pricing pages must store pricing as evidence with context, not as timeless truth.

applies_to:
  - wiki/06_pricing/PRICE-*.md

inherits:
  - knowledge_object

required_frontmatter:
  - id
  - title_en
  - page_type
  - status
  - source_ids
  - review_required

required_values:
  page_type:
    allowed_values:
      - pricing

optional_frontmatter:
  - title_zh
  - canonical_language
  - supported_languages
  - updated_at
  - native_review_required
  - related_pages
  - tags

field_rules:
  id:
    required_pattern: "^PRICE-"
    description: Pricing page ids should start with PRICE-.

  page_type:
    type: enum
    required: true
    allowed_values:
      - pricing

  review_required:
    type: boolean
    required: true
    expected_default: true
    description: Pricing is high-risk and should normally require review.

  native_review_required:
    type: boolean
    required: false
    description: Usually true if outward-facing English pricing wording is present.

  source_ids:
    type: list[string]
    required: true
    description: Source Note ids supporting the pricing page.

required_sections:
  - Pricing Scope
  - Current Working Price Snapshot
  - Historical Price Snapshots
  - Pricing Notes
  - Guardrails
  - Customer-Facing Reply Notes
  - Open Questions
  - Source Map

section_guidance:
  Pricing Scope:
    description: >
      Should identify product, market, currency, and channel context.

  Current Working Price Snapshot:
    description: >
      Use only when there is enough context to maintain one working price snapshot.
      Must include channel, price, currency, date observed, source id, and confidence if possible.

  Historical Price Snapshots:
    description: >
      Preserve prior channel-specific or date-specific price evidence.

  Pricing Notes:
    description: >
      Explain retail, livestream, promo, platform, or campaign distinctions.

  Guardrails:
    description: >
      State usage limits clearly, such as not treating undated pricing as current truth.

  Customer-Facing Reply Notes:
    description: >
      Draft-level external wording plus internal Chinese support note if needed.

  Open Questions:
    description: >
      Include uncertainty about date, channel, campaign status, or officialness.

  Source Map:
    description: >
      Must point to source notes.

pricing_evidence_minimum_fields:
  - product
  - channel
  - currency
  - price
  - source_id

recommended_pricing_fields:
  - date_observed
  - market
  - price_type
  - confidence
  - notes

global_rules:
  - Pricing is evidence, not timeless truth.
  - Do not merge different channels into one official price without policy support.
  - Do not use undated pricing as current truth.
  - Outward-facing pricing language should be reviewed.
  - Preserve source traceability.

lint_expectations:
  - review_required should normally be true
  - Source Map should exist
  - Current Working Price Snapshot should not exist without contextual support
  - pricing pages should preserve channel distinctions
  - outdated or weakly grounded pricing should be flagged