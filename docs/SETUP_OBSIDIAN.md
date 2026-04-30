# SETUP_OBSIDIAN.md

## Purpose

This file explains how to use the project as an Obsidian vault.

It covers:
- opening the project as a vault
- recommended Obsidian features
- optional plugins
- graph view expectations
- search and navigation tips
- lightweight git / CLI usage
- operator best practices

This is a practical setup guide.
It is not the system prompt and it is not the workflow policy file.

---

## What this file is for

This file teaches you how to use this project inside Obsidian.

Obsidian is mainly used here for:

- reading wiki pages
- searching product and pricing information
- clicking links between related notes
- checking backlinks
- viewing the knowledge graph
- editing Markdown files when needed

This file does not explain the whole business system.

For the full project overview, read `README.md` first.
For local setup and Git/tooling, read `docs/PROJECT_SETUP_README.md`.

---

# 1. Recommended setup model

For v1, the recommended setup is:

- local project folder
- open that folder as an Obsidian vault
- initialize local git
- optionally push to a private GitHub repo later

Recommended project root example:

```text
company-commercial-wiki/
```

Inside it, the main structure should look like:

```text
company-commercial-wiki/
├── raw/
├── wiki/
├── logic/
├── docs/
├── README.md
├── index.md
└── log.md
```

# 2. Open the project as an Obsidian vault

## Step 1

Create or clone the project folder locally.

## Step 2

Open Obsidian.

## Step 3

Choose:

`Open folder as vault`

## Step 4

Select the project root folder, for example:

`company-commercial-wiki/`

## Step 5

Confirm that these top-level folders are visible:

- `raw/`
- `wiki/`
- `logic/`
- `docs/`

If they are visible, the vault is ready to use.

# 3. How this vault is intended to work

This vault follows a Raw / Wiki / Logic model.

## `raw/`

Purpose:
- keep original source files
- preserve evidence
- avoid rewriting source materials

Typical examples:
- company deck
- product sheet
- product marketing card
- pricing source material

## `wiki/`

Purpose:
- store structured markdown knowledge
- source notes
- product pages
- pricing pages
- term pages
- inquiry patterns
- reply templates

## `logic/`

Purpose:
- store system behavior
- prompts
- rules
- skills
- lint guidance
- templates

This separation is important because folders in Obsidian are not enough by themselves.
The vault becomes useful only when:

- source evidence is preserved
- structured knowledge is linked
- system logic is kept separate

# 4. Recommended Obsidian built-in features

The following built-in Obsidian features are enough for v1.

## 4.1 File Explorer

Use it to browse:
- `raw/`
- `wiki/`
- `logic/`

## 4.2 Search

Use search to find:
- product IDs
- source note IDs
- tags
- metadata values
- review flags

Examples:

```text
PROD-ASTAXANTHIN-PLUS
SRC-
native_review_required
page_type: product
```

## 4.3 Backlinks

Backlinks help show which pages point to a product, source note, or term page.

This is very useful for:
- source traceability
- term reuse
- pricing/product relationships

## 4.4 Outgoing Links

Outgoing links help verify whether a page is properly connected.

## 4.5 Graph View

Graph View is useful, but it is not magic.

It only becomes helpful when pages contain real links such as:

```md
[[PROD-ASTAXANTHIN-PLUS]]
[[SRC-PG-ASTAXANTHIN-CN-CARD]]
[[TERM-NPN]]
```

If pages are only stored in folders but do not link to each other, the graph will not show useful relationships.

Important:
- folders do not create graph relationships
- file names alone do not create graph relationships
- graph depends mostly on `[[wikilinks]]`

## 4.6 Properties / Frontmatter

Use frontmatter consistently.

Recommended frontmatter fields include:
- `id`
- `title_en`
- `title_zh`
- `page_type`
- `status`
- `source_ids`
- `updated_at`
- `review_required`
- `native_review_required`
- `tags`

# 5. What makes graph view useful

A common misconception is that clean folders automatically create a good graph.
They do not.

To make graph view useful, pages should include:
- source links
- related page links
- term links
- pricing/product links
- tags where helpful

## Minimal linking rule

Each meaningful page should try to link to at least:
- one source note
- one related page
- one concept or term page if relevant

## Example

A product page should usually link to:
- its source notes
- its pricing page if one exists
- one or more term pages

A source note should usually link to:
- affected product pages
- relevant term pages
- relevant pricing pages if pricing appears

# 6. Recommended linking conventions

Use standard Obsidian wikilinks:

```text
[[SRC-PG-ASTAXANTHIN-CN-CARD]]
[[PROD-ASTAXANTHIN-PLUS]]
[[PRICE-D3-K2-CA-MG-ZN]]
[[TERM-NPN]]
```

## Preferred patterns

### Source note

Include sections such as:
- Linked Pages
- Recommended Wiki Updates

### Product page

Include sections such as:
- Source Map
- Related Pages
- Canonical Terms

### Pricing page

Include sections such as:
- Related Product
- Source Map

### Term page

Include sections such as:
- Related Pages
- Usage Context

# 7. Recommended tags

Tags are useful for grouping and search, but should not replace links.

Suggested tags:
- `#source`
- `#product`
- `#pricing`
- `#translation`
- `#marketing`
- `#pending-review`
- `#customer-facing`
- `#native-review-required`

Important note:

Use tags consistently, but do not rely on tags alone to build graph connectivity.

# 8. Recommended frontmatter conventions

Use English-first metadata keys.

## Example product page frontmatter

```yaml
id: PROD-ASTAXANTHIN-PLUS
title_en: Astaxanthin Plus
title_zh: 复合虾青素 PLUS
page_type: product
status: current
canonical_language: en
supported_languages: [en, zh]
updated_at:
review_required: false
native_review_required: true
source_ids:
  - SRC-PG-ASTAXANTHIN-CN-CARD
tags:
  - product
  - marketing
  - customer-facing
```

## Example source note frontmatter

```yaml
id: SRC-PG-ASTAXANTHIN-CN-CARD
title_en: PG Astaxanthin CN Card
title_zh: PG 复合虾青素中文手卡
source_type: product_marketing_source
source_status: pending_confirmation
languages: [zh]
domains:
  - product
  - marketing
  - translation
  - pricing
review_required: false
tags:
  - source
```

# 9. Recommended folder usage inside Obsidian

## `wiki/00_overview/`

Use for:
- overall context
- overview
- knowledge map

## `wiki/01_sources/`

Use for:
- source notes
- source registry

## `wiki/02_products/`

Use for:
- normalized product pages

## `wiki/03_materials/`

Use for:
- dosage forms
- packaging-related material notes
- reusable material concepts

## `wiki/04_marketing/`

Use for:
- brand positioning
- approved vs risky claims
- social proof and channel messaging notes

## `wiki/05_translation/`

Use for:
- translation style guidance
- bilingual usage notes

## `wiki/06_pricing/`

Use for:
- pricing pages
- price evidence notes if needed

## `wiki/07_inquiry_patterns/`

Use for:
- repeatable customer question patterns

## `wiki/08_reply_templates/`

Use for:
- reusable response templates

## `wiki/09_term_registry/`

Use for:
- canonical term entries

## `wiki/10_archive/`

Use for:
- deprecated or retired knowledge that still needs preservation

# 10. Recommended daily operator flow in Obsidian

## Scenario A — a new file arrives

- add the original file to `raw/`
- create a Source Note in `wiki/01_sources/`
- update `wiki/01_sources/source_registry.md`
- append a short entry to `log.md`

## Scenario B — you need a product page

- confirm relevant source note exists
- create or update product page in `wiki/02_products/`
- add source links
- separate facts from marketing claims
- update `log.md` if meaningful

## Scenario C — pricing is present

- create or update pricing page in `wiki/06_pricing/`
- keep channel / currency / source / date explicit
- mark review risk
- update `log.md` if meaningful

## Scenario D — graph looks weak

- add `[[wikilinks]]`
- add tags
- normalize frontmatter
- link source notes to products
- link products to pricing and term pages

# 11. Optional plugins

For v1, keep plugins minimal.

## Optional plugin 1 — Dataview

Useful if you later want:
- source registries generated from frontmatter
- product lists by type
- review-needed dashboards
- pricing review lists

Not required for v1.

## Optional plugin 2 — Templater

Useful if you want faster creation of:
- source notes
- product pages
- pricing pages
- term pages

Not required if you manually copy templates.

## Optional plugin 3 — Git integration plugin

Useful if you want git status/commit support inside Obsidian.

Optional only.

## Plugin warning

Do not make your vault depend on too many plugins early.
The wiki should remain readable and operable as plain markdown.

# 12. CLI and git basics

For v1, the project should ideally be versioned with git.

## Initialize repo

```bash
git init
```

## Check status

```bash
git status
```

## Stage files

```bash
git add .
```

## Commit changes

```bash
git commit -m "feat(wiki): add initial source and product pages"
```

## Search for a product id

```bash
rg "PROD-ASTAXANTHIN-PLUS" .
```

## Search for source note ids

```bash
rg "SRC-" wiki/
```

## Search for review flags

```bash
rg "native_review_required" wiki/
```

## Search for pricing pages

```bash
rg "page_type: pricing" wiki/
```

These are enough for normal v1 operation.

# 13. What not to do

Do not:
- treat folders as relationships
- rely only on tags
- assume marketing text is validated fact
- assume pricing in old cards is current truth
- publish high-risk customer-facing English without review
- overbuild plugins and automation too early

Also do not:
- rename files casually without updating links
- create many disconnected notes with no wikilinks
- mix English and Chinese randomly in metadata fields
- use Chinese file names for system files in `logic/`

# 14. Recommended demo path inside Obsidian

When showing the system to someone, use this order:

- `README.md`
- `wiki/00_overview/knowledge_map.md`
- `wiki/01_sources/source_registry.md`
- one source note such as:
  - `wiki/01_sources/SRC-PG-ASTAXANTHIN-CN-CARD.md`
- one product page such as:
  - `wiki/02_products/PROD-ASTAXANTHIN-PLUS.md`
- one pricing page such as:
  - `wiki/06_pricing/PRICE-D3-K2-CA-MG-ZN.md`
- one term page such as:
  - `wiki/09_term_registry/TERM-NPN.md`
- graph view
- backlinks on a product page

This sequence helps users understand:
- architecture
- evidence
- structured knowledge
- pricing control
- term normalization
- linking network

# 15. Recommended graph-view check

After creating or updating notes, ask:
- Does each important page link to at least one other meaningful page?
- Do source notes point to product or pricing pages?
- Do product pages point back to source notes?
- Do product pages link to term pages?
- Do pricing pages link to products and sources?
- Are important pages still isolated?

If too many pages remain isolated, improve linking before adding more folders.

# 16. Suggested next improvements

Once the vault is running smoothly, consider:
- more source notes
- more term pages
- stronger source-to-product-to-pricing linking
- small Dataview tables
- private GitHub backup
- optional lightweight scripts for bulk validation

Do not rush these.

The most important early win is:
- clean source notes
- clean product pages
- clear pricing evidence
- explicit links
- reliable review flags

# 17. Final recommendation

For v1:
- use Obsidian as the reading and linking layer
- use local git for version control
- keep the vault readable without heavy plugins
- prioritize source traceability and page linking over fancy automation

A clean, linked markdown vault is already enough to demonstrate the LLM Wiki model well.
