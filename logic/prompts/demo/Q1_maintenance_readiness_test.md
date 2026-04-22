# Q1 — Maintenance-readiness test

## Purpose

Check whether a linked product cluster is operationally maintainable.

## Prompt body

```text
Act as GovernanceAgent for [PRODUCT] and the pages linked to it.

Check:
- missing source_ids
- weak traceability
- unsupported claims
- stale or unclear pricing
- inconsistent term usage
- missing review flags
- missing updated_at
- missing important wikilinks

Return:
- must fix now
- should fix soon
- okay for now
```