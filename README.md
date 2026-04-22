# Company Commercial LLM Wiki

A company commercial knowledge base built in a LLM Wiki pattern.

This project is designed for:
- product information
- material information
- marketing messaging
- translation and terminology
- pricing and quotation rules
- inquiry samples and reply templates

It uses a **Raw / Wiki / Logic** structure so that source evidence, structured knowledge, and system behavior stay separated.

---

# 1. What this project is

This is not just a document folder.

It is a structured commercial knowledge system where:

- `raw/` keeps original files as source evidence
- `wiki/` stores reusable structured knowledge pages
- `logic/` stores rules, prompts, templates, and workflow definitions

The goal is to transform fragmented files such as:
- company decks
- product sheets
- Chinese product cards
- English PDFs
- pricing snippets
- bilingual marketing materials

into a connected, traceable, updateable markdown wiki.

---

# 2. Core design principles

## 1. **Raw sources are immutable**
   - original files are preserved as evidence
   - routine maintenance should not rewrite source files

## 2. **Knowledge is structured**
   - files are normalized into source notes, product pages, pricing pages, term pages, and related notes

## 3. **New information does not automatically erase old information**
   - use explicit states such as:
     - `current`
     - `historical`
     - `conflicting`
     - `pending_confirmation`
     - `deprecated`

## 4. **Important claims must be traceable**
   - major facts should point back to one or more source notes

## 5. **High-risk content requires review**
   - pricing
   - compliance / certification wording
   - strong customer-facing claims
   - high-risk customer-facing English

## 6. **English-first for system logic**
   - file names
   - metadata keys
   - status values
   - schemas
   - architecture labels

## 7. **Bilingual for business knowledge**
   - business pages may contain both English and Chinese
   - terms should keep:
     - canonical English term
     - preferred Chinese translation
     - aliases / discouraged variants

---

# 3. Repository structure

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

### raw/

Stores original source files only.

Examples:

company deck
product sheet
bilingual product card
pricing source material

Recommended subfolders:

raw/brand/
raw/products/
raw/pricing/
raw/translation/
### wiki/

Stores structured knowledge pages.

Main areas:

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
### logic/

Stores system behavior.

Main files:

logic/SYSTEM_PROMPT.md
logic/AGENTS.md
logic/RULES.md
logic/SKILL.md
logic/LINT.md

Templates:

logic/templates/source_note.md
logic/templates/product_page.md
logic/templates/pricing_page.md
logic/templates/term_entry.md
logic/templates/pricing_evidence_row.md
### index.md

Top-level navigation.

### log.md

Operational change log.

## 4. Key files
logic/SYSTEM_PROMPT.md

Defines the overall operating model of the knowledge system.

Includes:

mission
architecture
workflow
bilingual policy
review boundaries
logic/AGENTS.md

Defines the working agents:

SourceLibrarian
WikiMaintainer
InquiryAnalyst
GovernanceAgent
logic/RULES.md

Defines repository rules, traceability rules, pricing rules, translation rules, and review rules.

logic/SKILL.md

Defines the main procedures:

ingest
compare
update
archive
build source note
build product page
build pricing page
normalize terms
lint knowledge
logic/LINT.md

Defines lightweight checks for:

structure
metadata
traceability
pricing freshness
bilingual consistency
customer-facing review flags
## 5. How the wiki works

The project follows this workflow:

### Step 1 — Ingest

A source file is uploaded or added.

Examples:

company deck
product marketing card
product sheet
pricing screenshot or price sheet
### Step 2 — Create a Source Note

Every meaningful source should first become a Source Note in:

wiki/01_sources/

A Source Note captures:

what the file is
source type
source status
stable facts
risky or time-sensitive claims
pricing evidence
translation evidence
open questions
suggested downstream page updates
### Step 3 — Normalize into wiki pages

From the source note, build or update:

product pages
pricing pages
term registry entries
marketing pages
inquiry patterns
reply templates
### Step 4 — Link everything

Use wikilinks to connect:

source notes
product pages
pricing pages
term pages
registry pages
### Step 5 — Log meaningful changes

Append concise operational changes to:

### log.md

Update:

wiki/01_sources/source_registry.md
when new source notes are added.
## 6. Common page types
### Source Note

Location:

wiki/01_sources/

Purpose:

preserve traceable extraction from one source file
### Product Page

Location:

wiki/02_products/

Purpose:

normalize product identity, facts, claims, source map, and bilingual structure
### Pricing Page

Location:

wiki/06_pricing/

Purpose:

store pricing as evidence, not timeless truth
### Term Page

Location:

wiki/09_term_registry/

Purpose:

normalize repeated terms for bilingual consistency
## 7. Demo path

A good demo order is:

wiki/00_overview/knowledge_map.md
wiki/01_sources/source_registry.md
one source note, for example:
wiki/01_sources/SRC-PG-ASTAXANTHIN-CN-CARD.md
one product page, for example:
wiki/02_products/PROD-ASTAXANTHIN-PLUS.md
one pricing page, for example:
wiki/06_pricing/PRICE-D3-K2-CA-MG-ZN.md
one term page, for example:
wiki/09_term_registry/TERM-NPN.md
### index.md

Obsidian graph view

This shows:

source evidence
structured product knowledge
pricing governance
term normalization
linked markdown network
## 8. Demo message to explain the system

You can describe the system like this:

This vault is a commercial LLM Wiki.
Raw files stay as evidence.
We first convert each important source into a source note, then normalize product, pricing, translation, and marketing knowledge into linked markdown pages.
High-risk content such as pricing and strong customer-facing claims is reviewed instead of silently promoted as truth.

## 9. Bilingual policy
### English-first

Use English for:

file names
folder names
metadata keys
enum/status values
architecture labels
system logic
technical terms
### Bilingual business knowledge

Use bilingual structure where useful:

Summary (EN)
中文说明
term entries with:
canonical English term
preferred Chinese translation
aliases
discouraged variants
### Customer-facing English

Customer-facing output should default to English.

If content is high-risk, mark:

native_review_required: true

Examples of high-risk content:

claim-heavy marketing copy
pricing-related English
certification superiority wording
strong benefit claims
## 10. Obsidian usage

This project works well as an Obsidian vault.

### Recommended built-in Obsidian features

file explorer
backlinks
outgoing links
search
graph view
properties / frontmatter support
### Important note

Folders alone do not create graph connections.

To make graph view useful, pages should include:

[[wikilinks]]
related pages
source maps
shared term links
consistent tags
## 11. Git recommendation

This project should ideally be versioned with git.

### Recommended v1 setup

local Obsidian vault
local git repo
### Optional later

private GitHub repo for backup or collaboration
## 12. Minimal setup
### Open as a vault

create or clone the project folder
open it as an Obsidian vault
### Initialize git

Example:

```bash
git init
```

### Recommended basic commands

```bash
# check status
git status

# add files
git add .

# commit
git commit -m "feat(wiki): add initial commercial wiki structure"

# search for a product page
rg "PROD-ASTAXANTHIN-PLUS" .

# search for source notes
rg "SRC-" wiki/

# search for native review flags
rg "native_review_required" wiki/
```
## 13. What a normal operator should do

A normal operator does not need to read every system file every time.

Instead, use:

logic/USER_WORKFLOWS.md

That file contains:

workflow guidance
prompt library references
when to use each workflow
what files they create or update
what to check afterward
## 14. Safety reminders
Do not treat marketing copy as validated fact.
Do not treat undated pricing as current truth.
Do not silently overwrite conflicting knowledge.
Do not remove source traceability.
Do not publish high-risk customer-facing English without review.
## 15. Current project status

This project may already contain:

system prompt
agents
rules
skills
templates
source notes
product pages
pricing pages
source registry
log

The next value comes from:

more source notes
more explicit wikilinks
more term pages
more consistent frontmatter and tags
regular source-to-product-to-pricing linking
## 16. Suggested next steps
add new source notes for remaining uploaded files
create or enrich product pages
create pricing evidence pages where needed
create more term pages
improve wikilinks for graph readiness
keep source_registry.md and log.md updated

## Setup documents

- `docs/PROJECT_SETUP_README.md` — full local environment and tooling setup
- `docs/SETUP_OBSIDIAN.md` — Obsidian vault usage and navigation
- 
