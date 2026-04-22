# R2 — Workflow / prompt system integrity review

## Purpose

Review whether the workflow / prompt system is coherent, aligned, and usable after a refactor.

Targets the current refactored layout:

- `logic/USER_WORKFLOWS.md` — operator guide
- `logic/PROMPT_LIBRARY.md` — prompt index
- `logic/prompts/core/` — default operator path (B1, F1, K1)
- `logic/prompts/specialized/` — A*, B2, C*, E*, G*, H*, I*, J1
- `logic/prompts/demo/` — D1–D5, Q1
- `logic/prompts/refactor/` — R1, R2, R3

## Use when

- `logic/USER_WORKFLOWS.md` was reorganized
- `logic/PROMPT_LIBRARY.md` was restructured as an index
- prompt bodies were split into the `core/ specialized/ demo/ refactor/` folders
- workflow IDs or prompt IDs changed
- you want to verify that the system still works after a large refactor

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- README.md

Review only.
Do not modify files.

Review only these files:
- [exact file list]

Check:
1. whether `USER_WORKFLOWS.md` and `PROMPT_LIBRARY.md` are still aligned
2. whether the default operator path (B1 -> F1 -> K1) is clearly presented in both files
3. whether workflow names and prompt IDs are consistent across both files
4. whether prompt references point to the correct files under
   `logic/prompts/core/`, `logic/prompts/specialized/`, `logic/prompts/demo/`, `logic/prompts/refactor/`
5. whether specialized prompts are grouped consistently
   (source / product / pricing / term / schema-governance / graph-link / recovery)
6. whether demo and proof prompts (D1-D5, Q1) are clearly separated from maintenance prompts
7. whether refactor prompts (R1, R2, R3) are clearly separated from the normal maintenance loop
8. whether any old references or stale wording remain after the refactor
9. whether the refactor introduced duplication, dead references, or operator confusion
10. whether the system is ready for normal operator use

Output:
1. aligned / working files
2. files still needing cleanup
3. exact remaining reference or structure fixes
4. whether the refactor is operator-ready / commit-ready
```
