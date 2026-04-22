# A1 — Create one source note

## Purpose

Create exactly one new source note from one meaningful uploaded source.

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Use only this uploaded file as the source input.

Create exactly one new Source Note under:
- `wiki/01_sources/`

Also:
- update `wiki/01_sources/source_registry.md`
- append one short entry to `log.md`

Rules:
- do not modify any other files
- preserve source traceability
- do not convert marketing copy into validated fact
- do not treat undated pricing as current truth
- use the exact uploaded file name when referencing the source
```
