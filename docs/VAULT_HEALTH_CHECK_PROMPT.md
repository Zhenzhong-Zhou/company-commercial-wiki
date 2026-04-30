# VAULT_HEALTH_CHECK_PROMPT.md

## Purpose

Use this prompt to check whether the whole vault is still healthy, understandable, and moving in the right direction.

This is a high-level review prompt.

It does **not** fix files.
It does **not** create new pages.
It does **not** rewrite the vault.

It asks an AI assistant to review the vault and tell you whether the overall system still makes sense.

---

## Simple explanation

Think of this prompt like a regular inspection.

It checks questions like:

- Is the vault still organized correctly?
- Are the source files, wiki pages, rules, prompts, and schemas still aligned?
- Can another person understand how to use this vault without your chat history?
- Are product, pricing, translation, and marketing pages still traceable to source files?
- Is the vault still safe to demo or hand off?
- Is anything becoming messy, duplicated, unclear, or hard to maintain?

Use this when you want a second opinion before continuing major work.

---

## When to use this prompt

Use this:

- after a long cleanup session
- before demoing the vault
- before handing the vault to another operator
- before writing or publishing the README
- before merging major changes into the main branch
- when the vault feels messy even if individual files look okay
- when you want to confirm the system is still maintainable

---

## What this prompt checks

This prompt checks the full system, including:

- folder structure
- Raw / Wiki / Logic separation
- source traceability
- product pages
- pricing pages
- term pages
- rules
- lint checks
- schemas
- workflow files
- prompt library
- onboarding documents
- demo readiness

---

## What this prompt does not do

This is not:

- a file-by-file repair prompt
- a schema-fixing prompt
- a create-new-pages prompt
- a pricing-only review prompt
- a graph-only review prompt
- a command to modify files

It is only a review prompt.

The AI should report problems and recommendations, but should not edit anything.

---

## Prompt

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- logic/USER_WORKFLOWS.md
- logic/PROMPT_LIBRARY.md
- logic/schemas/knowledge_object.schema.yaml
- logic/schemas/source_note.schema.yaml
- logic/schemas/product_page.schema.yaml
- logic/schemas/pricing_page.schema.yaml
- logic/schemas/term_entry.schema.yaml
- logic/schemas/common_enums.schema.yaml
- README.md
- docs/SETUP_OBSIDIAN.md
- docs/PROJECT_SETUP_README.md
- index.md
- log.md

Review only.
Do not modify files.

Review this vault at the system level.

Plain-English goal:
Check whether this vault is still organized, understandable, traceable, safe to maintain, and usable by another operator without relying on previous chat context.

Check:

1. Whether the current project structure still follows the intended Raw / Wiki / Logic architecture

2. Whether raw source files, structured wiki pages, and logic/rule files are still clearly separated

3. Whether USER_WORKFLOWS.md and PROMPT_LIBRARY.md are aligned

4. Whether RULES.md, LINT.md, and schemas are aligned with the workflows and prompts

5. Whether page naming, page IDs, file names, and folder locations are consistent

6. Whether source traceability is preserved across source notes, product pages, pricing pages, and term pages

7. Whether product pages separate stable facts from marketing claims

8. Whether pricing governance is safe, meaning pricing is treated as dated evidence rather than timeless truth

9. Whether bilingual content is handled consistently, especially English system metadata and bilingual business content

10. Whether graph/link improvement is moving in the right direction

11. Whether onboarding and setup docs are enough for another operator to understand the vault

12. Whether README.md, docs/SETUP_OBSIDIAN.md, and docs/PROJECT_SETUP_README.md explain the system clearly for a non-technical user

13. Whether the current vault looks demo-ready, maintainable, and scalable

14. Whether anything is drifting, duplicated, under-documented, over-complicated, disconnected, or structurally inconsistent

Output:

1. What is working well

2. What is drifting or inconsistent

3. Top 5 structural risks

4. Top 5 next improvements

5. Beginner-readiness review:
   - Can a non-technical operator understand the purpose?
   - Can they find the correct first files to read?
   - Can they understand what to do next?

6. Demo-readiness review:
   - Is the vault currently demo-ready?
   - If not, what blocks demo readiness?

7. Handoff-readiness review:
   - Can another operator use this vault without previous chat context?
   - What information is missing for handoff?

8. Final status. Choose one:
   - on the right direction
   - mostly on the right direction but needs cleanup
   - drifting and needs structural correction

9. Recommended next action:
   - no action needed
   - small cleanup
   - documentation cleanup
   - structural cleanup
   - stop adding new pages and fix alignment first
```

## How to read the result

If the AI says:

on the right direction

The vault is healthy.
You can keep adding source notes, product pages, pricing pages, and term pages.

mostly on the right direction but needs cleanup

The system is basically good, but some files, links, docs, or schemas need cleanup before more expansion.

drifting and needs structural correction

Stop adding new content for now.
Fix the structure, rules, naming, links, or documentation first.

## Recommended follow-up after running this prompt

After the review:

Fix only the important issues.
Do not rewrite everything.
Update log.md if the cleanup is meaningful.
Run the health check again if the changes were large.
Commit the cleaned version in Git.
## Why this file matters

This file helps keep the vault maintainable.

Without this kind of review, the vault can slowly become:

hard to navigate
full of disconnected notes
inconsistent in naming
unclear for new users
unsafe for pricing or marketing claims
dependent on one person's memory

The goal is to make sure the vault can still be understood and maintained by someone else later.
