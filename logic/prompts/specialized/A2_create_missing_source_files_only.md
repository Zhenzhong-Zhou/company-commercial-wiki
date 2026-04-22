# A2 — Create missing source files only

## Purpose

Create only the missing source-note files without rerunning a broader batch.

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Use only these uploaded files in the current session as source inputs.
Do not assume any repo raw/ path that has not been explicitly created yet.
When referencing sources, use the exact uploaded file names.

Create only these missing files:
- [list only the missing files]

Also:
- update `wiki/01_sources/source_registry.md` if a new source note is created
- append one short entry to `log.md` if meaningful

Do not modify any other files.
```