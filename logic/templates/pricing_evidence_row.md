# pricing_evidence_row.md

## Purpose
This template defines the minimum row shape for a pricing evidence record.

Use this structure when extracting pricing from:
- product cards
- livestream sheets
- deck snapshots
- e-commerce pages
- campaign materials
- sales screenshots

---

## YAML-style Example

product_id: PROD-XXXX
product_title_en:
product_title_zh:
channel:
market:
currency:
price:
price_type:
date_observed:
source_id:
source_file:
confidence:
review_required: true
notes:

---

## Field Definitions

- `product_id`
  - canonical product id

- `product_title_en`
  - product English title if available

- `product_title_zh`
  - product Chinese title if available

- `channel`
  - example:
    - Amazon
    - Douyin
    - Kuaishou
    - Tmall
    - retail
    - livestream

- `market`
  - example:
    - Canada
    - China
    - global
    - unknown

- `currency`
  - example:
    - CAD
    - RMB
    - USD

- `price`
  - numeric price value

- `price_type`
  - example:
    - retail
    - livestream
    - promo
    - marketplace
    - campaign
    - unknown

- `date_observed`
  - date seen in source
  - use blank if missing, but then confidence should be lower

- `source_id`
  - source note id

- `source_file`
  - original file name if helpful

- `confidence`
  - example:
    - high
    - medium
    - low

- `review_required`
  - usually true for outward-facing use

- `notes`
  - campaign note, ambiguity, package mismatch, etc.

---

## Markdown Table Example

| product_id          | channel | market | currency | price | price_type | date_observed | source_id             | confidence | review_required | notes                |
| ------------------- | ------- | ------ | -------- | ----: | ---------- | ------------- | --------------------- | ---------- | --------------- | -------------------- |
| PROD-D3-K2-CA-MG-ZN | Douyin  | China  | RMB      |   298 | retail     | 2026-01-01    | SRC-WIDE-BONE-CN-CARD | medium     | true            | daily flagship price |