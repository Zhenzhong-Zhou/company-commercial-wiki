# D1 — Product retrieval + traceability test

## Purpose

Prove that one product can be answered using source-backed structured knowledge.

## Prompt body

```text
Using only this vault, summarize the current working knowledge for [PRODUCT].

Return:
- product identity
- dosage form
- pack size
- NPN
- recommended use / suggested use
- source notes used
- any conflicting or pending_confirmation items

Do not include unsupported claims.
```