# Company Commercial LLM Wiki

# Company Commercial LLM Wiki

This is a company knowledge base for organizing product, pricing, marketing, translation, and customer inquiry information.

It keeps original source files, structured wiki pages, and operating rules separated so the information is easier to review, update, and reuse.

The goal is not to replace an ERP, CRM, database, or file storage system.

The goal is to make important commercial knowledge easier to search, trace, explain, and maintain.

---

## Start here if you are new

This project may look technical at first, but the basic idea is simple:

1. Keep original company files safe.
2. Extract useful facts from those files.
3. Turn those facts into clean wiki pages.
4. Link related pages together.
5. Use the wiki later for product questions, pricing checks, translation, marketing review, and customer replies.

You do **not** need to be an AI expert or developer to understand the basic workflow.

---

## What this project is

This is a company commercial knowledge base.

It is designed to organize:

* product information
* material information
* marketing messaging
* translation and terminology
* pricing and quotation rules
* inquiry samples and reply templates

The project follows a **Raw / Wiki / Logic** structure.

That means:

* `raw/` keeps the original source files
* `wiki/` keeps the clean knowledge pages
* `logic/` keeps the rules, prompts, templates, and workflows used to maintain the wiki

The goal is to transform messy or scattered files such as product cards, decks, PDFs, screenshots, price sheets, and bilingual marketing materials into a connected, traceable, updateable wiki.

---

## What is an LLM Wiki?

An **LLM Wiki** is a structured knowledge base that can be maintained with help from an LLM.

An **LLM** means a Large Language Model, such as ChatGPT, Claude, or another AI assistant.

In this project, the LLM is used as a helper to:

* read source material
* extract useful facts
* create source notes
* update product pages
* normalize translation terms
* compare old and new information
* flag risky or unclear claims

Important: the LLM is **not** the final source of truth.

The source files and human review are still the authority, especially for:

* pricing
* compliance wording
* certification claims
* strong health or product benefit claims
* customer-facing English

This project is inspired by Andrej Karpathy's LLM Wiki idea. His version describes the general pattern of using LLMs to build and maintain structured knowledge bases from source material.

Related references:

* Andrej Karpathy's LLM Wiki GitHub Gist
* Open-source LLM Wiki implementations inspired by that idea

This repository is customized for commercial business knowledge, especially product, pricing, marketing, translation, and inquiry workflows.

---

## Wiki-first, RAG-ready

This project is designed as a human-readable Markdown wiki first.

That means the knowledge should be understandable even without AI tools.

The core system is:

- original files in `raw/`
- structured knowledge pages in `wiki/`
- rules, prompts, templates, and workflows in `logic/`

This structure can later support RAG, which means Retrieval-Augmented Generation.

In simple terms, RAG allows an AI assistant to search the wiki and answer questions using the vault content as reference material.

However, RAG should be treated as an optional search layer, not the main source of truth.

The Markdown wiki remains the maintained knowledge base.
The RAG system only helps retrieve and explain information from it.

---

## What this project is good for

This project is best for long-term, reusable company knowledge.

Good examples:

- product descriptions
- product facts
- pricing evidence
- marketing claims
- translation terms
- customer inquiry patterns
- reply templates
- source notes
- internal review notes
- stable business rules

It is useful when the information needs to be:

- searchable
- linked
- reviewed
- explained
- traced back to source files
- maintained over time

---

## LLM Wiki limitations

This project is a structured Markdown knowledge base.

It is useful for organizing stable or semi-stable company knowledge, but it is not a replacement for a database, ERP system, CRM system, accounting system, HR system, or live document management system.

This wiki works best for knowledge that needs to be:

- searched
- reviewed
- explained
- linked to source files
- maintained over time
- reused in product, pricing, marketing, translation, or customer inquiry work

Good examples include:

- product facts
- pricing evidence
- marketing claims
- translation terms
- customer inquiry patterns
- reply templates
- source notes
- review rules
- internal knowledge explanations

This wiki is not ideal for:

- fast-changing daily records
- live inventory quantities
- live customer orders
- live accounting records
- thousands or millions of transaction rows
- highly structured data that needs advanced filtering, reporting, or calculations
- private personal information
- sensitive employee or customer records
- legal, medical, or compliance decisions without human review

Use the right system for live or sensitive business data.

For example:

- use the ERP or database for live inventory
- use accounting software for financial records
- use a CRM or order system for customer transactions
- use an HR system for employee records
- use this wiki for explanations, source notes, product knowledge, pricing evidence, translation guidance, and review workflows

The wiki can support decision-making, but it should not be treated as the only source of truth for information that changes every day or every hour.

---

## Important AI usage rule

The LLM should not freely add, remove, rename, or restructure files without following the project rules.

Before making large changes, the operator should check:

- source files remain preserved
- wiki pages stay traceable
- naming conventions stay consistent
- product, pricing, and term pages follow templates
- risky content is marked for review
- `log.md` is updated when meaningful changes happen

The LLM is a maintenance helper, not the final authority.

---

## Team knowledge vs personal information

This vault is mainly designed for team and company knowledge.

It can also be adapted for personal knowledge, but avoid storing sensitive personal information unless there is a clear reason and proper privacy protection.

For company use, the best fit is stable shared knowledge that multiple people may need to search, review, or reuse later.

---

## Possible future extensions

After the wiki is stable, the company may add:

- full-text search
- Dataview dashboards
- lightweight validation scripts
- RAG-based question answering
- private chatbot access over the wiki
- database-backed search for larger knowledge collections

These are optional future layers.

For v1, the priority is:

- clean source notes
- clear product pages
- pricing evidence
- term consistency
- explicit wikilinks
- safe review flags

---

## What is Obsidian?

**Obsidian** is a note-taking app that works with local Markdown files.

A folder opened in Obsidian is called a **vault**.

This project can be opened as an Obsidian vault so users can:

* browse files like normal notes
* search product and pricing information
* click links between related pages
* view backlinks
* use graph view to see how pages connect
* edit Markdown files directly

You can still use the files without Obsidian, but Obsidian makes the wiki easier to read and navigate.

---

## What is Git and GitHub?

**Git** is a tool that tracks changes in files.

It helps answer questions like:

* What changed?
* When did it change?
* Who changed it?
* Can we go back to an older version?

**GitHub** is an online place to store a Git repository.

For this project, GitHub is useful for:

* backup
* collaboration
* change history
* reviewing updates before they become official

Recommended setup:

* Use a local folder as the Obsidian vault.
* Use Git to track changes.
* Use a **private GitHub repository** if company information is confidential.

Do not upload sensitive company files to a public GitHub repository.

---

## Read the docs folder first

The README gives the big picture.

For setup and detailed instructions, check the `docs/` folder.

Important setup documents:

* `docs/PROJECT_SETUP_README.md` — full local project setup and tooling guide
* `docs/SETUP_OBSIDIAN.md` — how to open and use this folder as an Obsidian vault
* `docs/VAULT_HEALTH_CHECK_PROMPT.md` — how to ask an AI assistant to check the vault structure

If you are new, read this README first, then read the docs above.

---

## Repository structure

```text
company-commercial-wiki/
├── raw/
├── wiki/
├── logic/
├── docs/
├── index.md
├── log.md
└── README.md
```

---

## Folder guide

### `raw/`

Stores original source files.

Examples:

* company decks
* product sheets
* Chinese product cards
* English PDFs
* pricing screenshots
* bilingual marketing materials

Recommended subfolders:

```text
raw/brand/
raw/products/
raw/pricing/
raw/translation/
```

Rule: do not rewrite or clean up original source files during normal maintenance.

Original files are evidence.

---

### `wiki/`

Stores structured knowledge pages.

Main areas:

```text
wiki/00_overview/
wiki/01_sources/
wiki/02_products/
wiki/03_materials/
wiki/04_marketing/
wiki/05_translation/
wiki/06_pricing/
wiki/07_inquiry_patterns/
wiki/08_reply_templates/
wiki/09_term_registry/
wiki/10_archive/
```

This is where the usable business knowledge lives.

Examples:

* product pages
* source notes
* pricing evidence pages
* translation term pages
* customer reply templates

---

### `logic/`

Stores the operating rules for the wiki.

Main files:

```text
logic/SYSTEM_PROMPT.md
logic/AGENTS.md
logic/RULES.md
logic/SKILL.md
logic/LINT.md
logic/USER_WORKFLOWS.md
```

Templates:

```text
logic/templates/source_note.md
logic/templates/product_page.md
logic/templates/pricing_page.md
logic/templates/term_entry.md
logic/templates/pricing_evidence_row.md
```

A normal user does not need to read every file in `logic/` every day.

For normal work, start with:

```text
logic/USER_WORKFLOWS.md
```

---

### `docs/`

Stores setup and support documents.

Use this folder when you need help with:

* local setup
* Obsidian setup
* vault health checks
* project maintenance guidance

---

### `index.md`

The top-level navigation page.

Open this first inside Obsidian.

---

### `log.md`

The operational change log.

Use this file to record meaningful updates, such as:

* new source notes added
* product pages updated
* pricing evidence added
* term pages created
* conflicting information found

---

## Core design principles

### 1. Raw sources are preserved

Original files in `raw/` should stay unchanged.

They are used as evidence.

---

### 2. Knowledge is structured

Information should be turned into consistent page types, such as:

* source notes
* product pages
* pricing pages
* term pages
* marketing pages
* reply templates

---

### 3. New information does not automatically erase old information

When information changes, do not silently overwrite the old version.

Use clear states such as:

* `current`
* `historical`
* `conflicting`
* `pending_confirmation`
* `deprecated`

---

### 4. Important claims must be traceable

Important product, pricing, compliance, and marketing claims should point back to source notes.

The wiki should answer:

> Where did this information come from?

---

### 5. High-risk content requires review

Some content should not be published or sent to customers without human review.

Examples:

* pricing
* compliance wording
* certification wording
* strong health or benefit claims
* customer-facing English
* legal or regulatory language

Use review flags when needed.

Example:

```yaml
native_review_required: true
```

---

### 6. English-first for system logic

Use English for:

* file names
* folder names
* metadata keys
* status values
* schema names
* system logic
* architecture labels

---

### 7. Bilingual for business knowledge

Business pages may include both English and Chinese.

Term pages should keep:

* canonical English term
* preferred Chinese translation
* aliases
* discouraged variants
* usage notes

---

## How the wiki workflow works

### Step 1 — Add a source file

A source file is added to `raw/`.

Examples:

* product card
* company deck
* product sheet
* pricing screenshot
* bilingual marketing material

---

### Step 2 — Create a source note

Every important source should first become a source note in:

```text
wiki/01_sources/
```

A source note captures:

* what the source file is
* source type
* source status
* stable facts
* risky or time-sensitive claims
* pricing evidence
* translation evidence
* open questions
* suggested downstream page updates

---

### Step 3 — Update wiki pages

From the source note, update or create:

* product pages
* pricing pages
* term registry entries
* marketing pages
* inquiry patterns
* reply templates

---

### Step 4 — Link related pages

Use Obsidian-style wikilinks to connect pages.

Example:

```md
[[PROD-ASTAXANTHIN-PLUS]]
[[TERM-NPN]]
[[SRC-PG-ASTAXANTHIN-CN-CARD]]
```

Links make the wiki easier to search, review, and navigate.

---

### Step 5 — Log meaningful changes

After meaningful updates, update:

```text
log.md
wiki/01_sources/source_registry.md
```

This helps the team understand what changed and why.

---

## Common page types

### Source Note

Location:

```text
wiki/01_sources/
```

Purpose:

Keep traceable extraction from one source file.

---

### Product Page

Location:

```text
wiki/02_products/
```

Purpose:

Normalize product identity, product facts, claims, source map, and bilingual product information.

---

### Pricing Page

Location:

```text
wiki/06_pricing/
```

Purpose:

Store pricing as evidence, not timeless truth.

Pricing can become outdated, so dates and source references are important.

---

### Term Page

Location:

```text
wiki/09_term_registry/
```

Purpose:

Normalize repeated English and Chinese terms.

This helps keep translation consistent.

---

## Suggested demo path

To show someone how the system works, open these in order:

1. `index.md`
2. `wiki/00_overview/knowledge_map.md`
3. `wiki/01_sources/source_registry.md`
4. one source note, for example:

     * `wiki/01_sources/SRC-PG-ASTAXANTHIN-CN-CARD.md`
5. one product page, for example:

     * `wiki/02_products/PROD-ASTAXANTHIN-PLUS.md`
6. one pricing page, for example:

     * `wiki/06_pricing/PRICE-D3-K2-CA-MG-ZN.md`
7. one term page, for example:

     * `wiki/09_term_registry/TERM-NPN.md`
8. Obsidian graph view

This demo shows:

* source evidence
* structured product knowledge
* pricing governance
* term normalization
* linked Markdown pages

---

## Simple explanation for non-technical users

You can explain this project like this:

> This is our company commercial knowledge base. Original files stay in `raw/` as evidence. Important information is extracted into source notes, then organized into product, pricing, translation, marketing, and customer reply pages. The goal is to make company knowledge easier to search, reuse, review, and update without losing source traceability.

---

## Basic Obsidian usage

Recommended built-in Obsidian features:

* File Explorer
* Search
* Backlinks
* Outgoing links
* Graph View
* Properties / frontmatter support

Important note:

Folders alone do not create graph connections.

To make graph view useful, pages need:

* `[[wikilinks]]`
* related pages
* source maps
* shared term links
* consistent tags

---

## Basic Git workflow

Use Git to track changes.

Common commands:

```bash
# Check what changed
git status

# Add all changed files
git add .

# Save a version with a message
git commit -m "feat(wiki): add initial commercial wiki structure"

# Push to GitHub
git push
```

Useful search commands:

```bash
# Search for a product page
rg "PROD-ASTAXANTHIN-PLUS" .

# Search for source notes
rg "SRC-" wiki/

# Search for native review flags
rg "native_review_required" wiki/
```

If you are new to Git, do not force-push or delete files unless you understand the impact.

---

## What a normal operator should do

A normal operator does not need to read every system file every time.

Start here:

```text
logic/USER_WORKFLOWS.md
```

That file explains:

* what workflow to use
* which prompt to use
* what files may be created or updated
* what to check after the update

For setup help, use:

```text
docs/PROJECT_SETUP_README.md
docs/SETUP_OBSIDIAN.md
```

---

## Safety reminders

Do not treat marketing copy as validated fact.

Do not treat undated pricing as current truth.

Do not silently overwrite conflicting knowledge.

Do not remove source traceability.

Do not publish high-risk customer-facing English without review.

Do not upload private company information to a public repository.

---

## Current project status

This project may already contain:

* system prompt
* agents
* rules
* skills
* templates
* source notes
* product pages
* pricing pages
* source registry
* log

The next value comes from:

* adding more source notes
* adding more explicit wikilinks
* creating more term pages
* improving product and pricing pages
* keeping frontmatter and tags consistent
* keeping `source_registry.md` and `log.md` updated

---

## Suggested next steps

1. Open this folder in Obsidian.
2. Read `index.md`.
3. Read the setup documents in `docs/`.
4. Add remaining original files into `raw/`.
5. Create source notes for important source files.
6. Link source notes to product, pricing, marketing, and term pages.
7. Update `wiki/01_sources/source_registry.md`.
8. Update `log.md` after meaningful changes.
9. Review high-risk content before using it externally.

---

## Beginner glossary

### Vault

A folder of Markdown notes opened in Obsidian.

### Markdown

A plain-text file format used for notes and documentation.

Markdown files usually end with `.md`.

### Wikilink

A link between notes using double brackets.

Example:

```md
[[TERM-NPN]]
```

### Source Note

A structured note that extracts important facts from one source file.

### Product Page

A structured page that describes one product using normalized information.

### Pricing Evidence

A pricing record tied to a date and source.

Pricing evidence is not automatically permanent truth.

### Term Registry

A controlled list of preferred English and Chinese terms.

### Frontmatter

Metadata at the top of a Markdown file.

Example:

```yaml
---
id: PROD-ASTAXANTHIN-PLUS
status: current
review_required: false
---
```

### LLM

A Large Language Model, such as ChatGPT or Claude.

In this project, the LLM helps maintain the wiki, but human review remains important.
