# Log

## Purpose
This file records meaningful repository events:
- new source ingested
- new page created
- page updated
- claim conflict detected
- historical/deprecated transition
- review trigger raised

---

## 2026-04-21
- Initialized logic layer:
  - `logic/AGENTS.md`
  - `logic/RULES.md`
  - `logic/SKILL.md`

- Initialized templates:
  - `logic/templates/source_note.md`
  - `logic/templates/product_page.md`
  - `logic/templates/pricing_page.md`

- Initialized second-stage files:
  - `logic/SYSTEM_PROMPT.md`
  - `logic/LINT.md`
  - `logic/templates/term_entry.md`
  - `logic/templates/pricing_evidence_row.md`
  - `wiki/00_overview/overview.md`
  - `wiki/00_overview/knowledge_map.md`
  - `wiki/01_sources/source_registry.md`
  - `index.md`
  - `log.md`

- Registered initial source batch:
  - WIDE company deck
  - PG product sheet EN
  - PG Astaxanthin CN card
  - PG Ubiquinol CN card
  - WIDE D3+K2+CA+MG+ZN CN card

## Next Planned Work
- create concrete source notes
- create first product pages
- create first pricing evidence rows
- build term registry
- build approved vs unverified claims page

## 2026-04-21  
- Created `wiki/01_sources/SRC-PG-ASTAXANTHIN-CN-CARD.md`  
- Created `wiki/02_products/PROD-ASTAXANTHIN-PLUS.md`  
- Created `wiki/02_products/PROD-UBIQUINOL.md`  
- Created `wiki/02_products/PROD-D3-K2-CA-MG-ZN.md`  
- Created `wiki/06_pricing/PRICE-D3-K2-CA-MG-ZN.md`  
- Updated `wiki/01_sources/source_registry.md`  
- Flagged pricing and high-risk customer-facing claims for review

## 2026-04-22
- Added source notes and term registry pages, then linked source, product, pricing, and term pages for graph readiness.
- Normalized `logic/LINT.md`, clarified D3/K2 price evidence as non-current pending evidence, and aligned low-risk dosage-form term review behavior.
- Strengthened graph links across source registry, product pages, pricing evidence, and high-risk term entries without promoting new facts.
- Populated exact `.schema.yaml` files and aligned schema enum/page-type definitions for source notes and term entries.
- Verified listed term registry pages against `term_entry` schema; no additional term-page changes were required.
- Made Astaxanthin Plus and D3/K2 product links symmetric where supported by shared deck evidence.
- Created pricing evidence pages for PG products using existing source-card evidence:
  - `wiki/06_pricing/PRICE-ASTAXANTHIN-PLUS.md`
  - `wiki/06_pricing/PRICE-UBIQUINOL.md`
- Updated related source, product, pricing, and term links for graph readiness.
- Kept PG pricing evidence as `pending_confirmation`; no undated pricing was promoted to current truth.
- Corrected WIDE deck source filename references to match the uploaded raw file name; no source claims changed.
- Cleaned remaining source-note section gaps and pricing enum values without finalizing unresolved prices.
- Flagged governance follow-up:
  - PG pricing still needs current channel/date confirmation
  - customer-facing pricing remains review-required

## Next Planned Work
- Verify PG pricing against current channel evidence before any customer-facing quote.
