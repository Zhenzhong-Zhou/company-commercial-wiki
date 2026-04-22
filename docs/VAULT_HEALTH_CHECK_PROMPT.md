# VAULT_HEALTH_CHECK_PROMPT.md

## Purpose

Use this prompt to check whether the vault is still moving in the right direction overall.

This is broader than a schema-only check or a graph-only check.

Use it when you want to verify:
- the vault architecture still makes sense
- the workflow files, prompt library, rules, lint, and schemas stay aligned
- the current batch is not drifting away from the intended system design
- onboarding and setup documentation are sufficient for another operator
- the project is still demo-ready and maintainable

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
- index.md
- log.md

Review only.
Do not modify files.

Review this vault at the system level.

Check:
1. whether the current project structure still matches the intended Raw / Wiki / Logic architecture
2. whether USER_WORKFLOWS.md and PROMPT_LIBRARY.md are aligned
3. whether RULES.md, LINT.md, and schemas are aligned with the workflows and prompts
4. whether page naming, IDs, and file organization are staying consistent
5. whether source traceability is being preserved across product, pricing, and term pages
6. whether graph/link improvement is moving in the right direction
7. whether pricing governance is still safe
8. whether onboarding/setup docs are sufficient for another operator
9. whether the current vault looks demo-ready, maintainable, and scalable
10. whether anything is drifting, duplicated, under-documented, or structurally inconsistent

Output:
1. what is working well
2. what is drifting or inconsistent
3. the top 5 structural risks
4. the top 5 next improvements
5. whether the vault is currently:
   - on the right direction
   - mostly on the right direction but needs cleanup
   - drifting and needs structural correction
6. whether the current setup is usable by another operator without chat context
```

---

## When to use

Use this:
- after a long cleanup session
- before demoing the vault
- before handing the vault to another operator
- before writing a public README
- when you feel the project may be getting messy even if individual files look okay

---

## What this is not

This is not:
- a file-by-file schema repair prompt
- a create-pages prompt
- a narrow graph-only prompt
- a pricing-only prompt

It is a high-level health and direction review prompt.
